# PropertyObservers_Swift
PropertyObservers_Swift

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



