# iOS Dependencies
This document details the dependency management and setup for the iOS version of the App.

## 1. Prerequisites
- Install **Xcode** ([Download](https://developer.apple.com/xcode/)).
- Install **Homebrew** ([Homebrew](https://brew.sh/)).
- Install **CocoaPods** and **Swift Package Manager (SPM)**.

## 2. Dependency Management
- Use **CocoaPods** or **Swift Package Manager (SPM)**.
- Example `Podfile`:

```ruby
target 'App' do
  use_frameworks!

  pod 'Alamofire', '~> 5.4'
  pod 'SwiftyJSON', '~> 5.0'
end
```