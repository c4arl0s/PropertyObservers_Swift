# PropertyObservers_Swift
PropertyObservers_Swift

- willSet is called just before the value is stored.
- didSet is called immediately after the new value is stored.

# Take a look how newValue and oldValue are created into the willSet and didSet Methods.

``` swift
//
//  StepCounter.swift
//  PropertyObservers_Swift
//
//  Created by Carlos Santiago Cruz on 9/1/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

import Foundation

class StepCounter {
    var totalSteps: Int = 0 {
        willSet {
            print("About to set totalSteps to \(newValue)")
        }
        didSet{
            if totalSteps > oldValue {
                print("Added \(totalSteps - oldValue)")
            }
        }
    }
}
```


``` swift
//
//  ViewController.swift
//  PropertyObservers_Swift
//
//  Created by Carlos Santiago Cruz on 9/1/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        let stepCounter = StepCounter()
        stepCounter.totalSteps = 200
        stepCounter.totalSteps = 350
        stepCounter.totalSteps = 896
    }
}
```

``` console
About to set totalSteps to 200
Added 200
About to set totalSteps to 350
Added 150
About to set totalSteps to 896
Added 546
```

# You can create new temporal variables like this and you get the same result.

``` swift
//
//  StepCounter.swift
//  PropertyObservers_Swift
//
//  Created by Carlos Santiago Cruz on 9/1/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

import Foundation

class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)")
        }
        didSet(oldTotalSteps){
            if totalSteps > oldTotalSteps {
                print("Added \(totalSteps - oldTotalSteps)")
            }
        }
    }
}





