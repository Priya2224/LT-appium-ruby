# Ruby With Appium ![pw](https://img.shields.io/badge/Ruby-CC342D?style=for-the-badge&logo=ruby&logoColor=white)

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171857146-90e52e22-0070-4798-b2a5-6cc525a4da66.png">
</p>

<p align="center">
  <a href="https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/c/LambdaTest" target="_bank">YouTube</a>
</p>

*Appium is a tool for automating native, mobile web, and hybrid applications on iOS, Android, and Windows platforms. Perform Appium automation tests on [LambdaTest's online cloud](https://www.lambdatest.com/appium-mobile-testing).*

[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

## Table of Contents

* [Pre-requisites](#pre-requisites)
* [Run Your First Test](#run-your-first-test)
* [Executing The Tests](#executing-the-tests)
* [Troubleshooting](#troubleshooting)

---

## Pre-requisites

To perform Ruby automation testing with Appium on LambdaTest, you must complete the following setup:

### 1. Install Ruby
Install **Ruby 3.4.0** or higher on your local system.
- **Windows**: Download and install from [RubyInstaller for Windows](https://rubyinstaller.org/downloads/).
- **macOS**: Use Homebrew: `brew install ruby`.
- **Linux**: Use apt: `sudo apt-get install ruby-full`.

### 2. Install Bundler
Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed.
```bash
gem install bundler

3. Clone The Project
Clone this repository to your local machine:
git clone [https://github.com/Priya2224/LT-appium-ruby.git](https://github.com/Priya2224/LT-appium-ruby.git)
cd LT-appium-ruby

4. Setup Authentication
Retrieve your LambdaTest Username and Access Key from the LambdaTest Automation Dashboard. Set them as environment variables:

For Windows (CMD):
set LT_USERNAME=YOUR_USERNAME
set LT_ACCESS_KEY=YOUR_ACCESS_KEY

For macOS/Linux:
export LT_USERNAME=YOUR_USERNAME
export LT_ACCESS_KEY=YOUR_ACCESS_KEY

Run Your First Test
1. Upload Your App
Upload your .apk (Android) or .ipa (iOS) file to LambdaTest to receive your App URL (lt://APP12345).

2. Configure Capabilities (Ruby 3.4 Fix)
Update the caps object in your script. Note that for Ruby 3.4, you must use Symbols for driver initialization keys.

caps = {
    "lt:options" => {
        :deviceName => "Pixel 6",
        :platformName => "Android",
        :platformVersion => "13",
        :app => "lt://YOUR_APP_ID",
        :w3c => true,
        :isRealMobile => true
    },
    :platformName => "Android"
}

Executing The Tests
Install the required dependencies and run the sample script:
# Install dependencies
bundle install

# Run the Android test
bundle exec ruby android-sample.rb

# Run the iOS test
bundle exec ruby ios-sample.rb

Troubleshooting
ArgumentError (String to Symbol)
If you see an error regarding String/Symbol conversion, ensure your driver is created with explicit symbols:

@appium_driver = Appium::Driver.new({ :caps => caps, :appium_lib => { :server_url => server_url } }, true)

Missing Gemfile.lock
If you have dependency conflicts, run:
del Gemfile.lock
bundle update

<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">