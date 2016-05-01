# AhtauTouch
Peek and Pop extensions compatible with all iOS devices.

## Usage

Import AhtauTouch at the top of the file containing the class in which you plan on supporting previewing (Peek) and commit (Pop).

```swift
import AhtauTouch
```

Create a AhtauTouch object, register your view controller for handling the peek and specify the source view. You will also need to declare that your view controller will conform to the AhtauTouchPreviewingDelegate protocol.

```swift
// final prefix for optimization if your View Controller is not being subclassed.
final class ViewController: UIViewController, AhtauTouchPreviewingDelegate {
    
    // AhtauTouch Object
    var ahtauTouch: AhtauTouch?
        
    override func viewDidLoad() {
        
        // Initialize with Reference to Containing View Controller
        ahtauTouch = AhtauTouch(viewController: self)

        // Register View to Target for Observing Gestures (self.view is used to ensure proper rendering).
        ahtauTouch?.registerForPreviewingWithDelegate(self, sourceView: self.view)
    }

}
```

As with Apple's own 3D Touch preview APIs, AhtauTouchPreviewingDelegate requires implementing two methods in the conforming class. 

The first function defines the View Controller initialized as the previewing context: 
```swift
    func previewingContext(previewingContext: PreviewingContext, viewControllerForLocation location: CGPoint) -> UIViewController?
```

The second function then defines how to handle the actual use of that previewing context for the "Pop" action: 
```swift
    func previewingContext(previewingContext: PreviewingContext, commitViewController viewControllerToCommit: UIViewController)
```

##CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Cocoa projects. You can install it with the following command:

```bash
$ gem install cocoapods
```

> CocoaPods 0.39.0+ is required to build AhtauTouch 0.0.1+.

To integrate AhtauTouch into your Xcode project using CocoaPods, specify it in your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'
use_frameworks!

pod 'AhtauTouch', '~> 0.0.1'
```

Then, run the following command:

```bash
$ pod install
```

##Related Projects:

###Example Swift Apps by Mark Hamilton, Dryverless
Collection of example applications written in Swift / Objective-C for iOS 9.x (developed under 9.2.1 SDK - will be migrated to 9.3 when released)
######https://github.com/TheDarkCode/Example-Swift-Apps

##Support:

#####Send any questions or requests to: support@dryverless.com

## Contributing

  - 1) Fork this repository!
  - 2) Create your feature branch: ```git checkout -b Your-New-Feature```
  - 3) Commit your changes: ```git commit -am 'Adding some super awesome update'```
  - 4) Push to the branch: ```git push origin Your-New-Feature```
  - 5) Submit a pull request!

## License
Copyright (c) 2016 Mark Hamilton / dryverless (http://www.dryverless.com)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
