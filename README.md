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

*Appium is a tool for automating native, mobile web, and hybrid applications on iOS, Android, and Windows platforms. It supports iOS native apps written in Objective-C or Swift and Android native apps written in Java or Kotlin. It also supports mobile web apps accessed using a mobile browser (Appium supports Safari on iOS and Chrome or the built-in 'Browser' app on Android). Perform Appium automation tests on [LambdaTest's online cloud](https://www.lambdatest.com/appium-mobile-testing).*

Learn the basics of [Appium testing on the LambdaTest platform](https://www.lambdatest.com/support/docs/getting-started-with-appium-testing/).

[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

## Table of Contents

* [Pre-requisites](#pre-requisites)
* [Setting Up Your Authentication](#setting-up-your-authentication)
* [Upload Your Application](#upload-your-application)
* [Run Your First Test](#run-your-first-test)
* [Executing The Tests](#executing-the-tests)
* [Troubleshooting](#troubleshooting)
* [About LambdaTest](#about-lambdatest)

---

## Pre-requisites

Before you can start performing Ruby automation testing with Appium, you would need to:

1. Install **Ruby**: Ensure you have Ruby 3.4+ installed.

   - For **Windows**, download from [RubyInstaller](https://rubyinstaller.org/downloads/).
   - For **macOS**, run `brew install ruby`.
   - For **Linux** or **Ubuntu**, you can run a simple apt command like below:
     sudo apt-get install ruby-full

2. **Clone The Sample Project**:

```bash
git clone [https://github.com/Priya2224/LT-appium-ruby.git](https://github.com/Priya2224/LT-appium-ruby.git)
cd LT-appium-ruby

```

## Setting Up Your Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts. To obtain your access credentials, purchase a plan or access the access the [App Automation Dashboard](https://appautomation.lambdatest.com/)

Set LambdaTest Username and Access Key in environment variables.

For Linux/macOS:

```bash
export LT_USERNAME=YOUR_LAMBDATEST_USERNAME
export LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY
```

For Windows:

```bash
set LT_USERNAME=YOUR_LAMBDATEST_USERNAME
set LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY
```

## Upload Your Application

Upload your iOS application (.ipa file) or android application (.apk file) to the LambdaTest servers using our REST API. You need to provide your Username and AccessKey in the format Username:AccessKey in the cURL command for authentication. Make sure to add the path of the appFile in the cURL request. Here is an example cURL request to upload your app using our REST API:

Using App File:

For Linux/macOS:

```bash
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"'
```

For Windows:

```bash
curl -u "USER:KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"C:/path/to/proverbial_android.apk""
```

Using App URL:

For Linux/macOS:

```bash
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'
```

For Windows:

```bash
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{"url":"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk","name":"sample.apk"}"
```

Tip:

1. If you do not have any .apk or .ipa file, you can run your sample tests on LambdaTest by using our sample 🔗 [Android App](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample 🔗 [iOS App](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
2. Response of above cURL will be a JSON object containing the App URL of the format - lt://APP123456789123456789 and will be used in the next step.

## Run Your First Test

Once you are done with the above-mentioned steps, you can initiate your first Ruby test on LambdaTest.

Test Scenario: Check out [Android.rb](https://github.com/LambdaTest/LT-appium-ruby/blob/master/android/android-sample.rb) file to view the sample test script for android and [iOS.rb](https://github.com/LambdaTest/LT-appium-ruby/blob/master/ios/ios-sample.rb) for iOS.

### Configuring Your Test Capabilities (Ruby 3.4/W3C Fix)
Update the caps object in your scripts. For Ruby 3.4, keys must be Symbols.

Android Configuration

```bash
caps = {
  "lt:options" => {
    :deviceName => "Galaxy S24",
    :platformName => "Android",
    :platformVersion => "14",
    :isRealMobile => true,
    :app => "YOUR_APP_URL",
    :w3c => true
  },
  :platformName => "Android"
}
```

iOS Configuration

```bash
caps = {
  "lt:options" => {
    :deviceName => "iPhone 17 Pro",
    :platformName => "iOS",
    :platformVersion => "26",
    :isRealMobile => true,
    :app => "YOUR_APP_URL",
    :w3c => true
  },
  :platformName => "iOS"
}
```

Info Note:

1. You must add the generated APP_URL to the "app" capability in the config file.
2. You can generate capabilities for your test requirements with the help of our inbuilt [Capabilities Generator tool](https://www.lambdatest.com/capabilities-generator/). A more Detailed Capability Guide is available [here](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/).

## Executing The Tests

1. Install dependencies:

```bash
bundle install
```

2. Run the scripts:

Running on Android

Navigate to the corresponding directory based on your app.

```bash
cd android
```

Execute the following command to run your test on LambdaTest platform:

```bash
ruby android-sample.rb
```

Running on iOS

Navigate to the corresponding directory based on your app.

```bash
cd ios
```

Execute the following command to run your test on LambdaTest platform:

```bash
ruby ios-sample.rb
```

Note: Ensure you have updated the YOUR_APP_URL in each respective file before running these commands. Your test results will be displayed on the terminal and can also be viewed in detail on the [App Automation Dashboard](https://appautomation.lambdatest.com/).

## Troubleshooting

1. Ruby 3.4 ArgumentError (String to Symbol)

   If you encounter an ArgumentError stating "String cannot be converted to Symbol," it is because Ruby 3.4 requires explicit symbols for the driver initialization keys. Update your initialization to include the :caps and :appium_lib symbols exactly as shown below:

```bash
@appium_driver = Appium::Driver.new({
  :caps => caps,
  :appium_lib => { :server_url => server_url }
}, true)
```

2. Gem Installation Issues

     If you encounter an error like No such file or directory @ rb_sysopen during gem installation, you can resolve it by using administrator privileges or ensuring the directory exists:
      
      - macOS/Linux: Use sudo gem install appium_lib -v 10.6.0.

      - Windows: Open Command Prompt as Administrator and run gem install appium_lib -v 10.6.0.

3. W3C Protocol Compatibility

    Ensure your capabilities object includes the :w3c => true option and wraps custom LambdaTest options inside the "lt:options" key to stay compatible with modern Appium standards.

## Additional Links

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

## Documentation & Resources 📚

Visit the following links to learn more about LambdaTest's features, setup and tutorials around test automation, mobile app testing, responsive testing, and manual testing.

 - [LambdaTest Documentation](https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby)
 - [LambdaTest Blog](https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby)
 - [LambdaTest Learning Hub](https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby)

## LambdaTest Community :busts_in_silhouette:

The [LambdaTest Community](https://community.lambdatest.com/) allows people to interact with tech enthusiasts. Connect, ask questions, and learn from tech-savvy people. Discuss best practises in web development, testing, and DevOps with professionals from across the globe 🌎

## What's New At LambdaTest ❓

To stay updated with the latest features and product add-ons, visit [Changelog](https://changelog.lambdatest.com/) 
      
## About LambdaTest

[LambdaTest](https://www.lambdatest.com) is a leading test execution and orchestration platform that is fast, reliable, scalable, and secure. It allows users to run both manual and automated testing of web and mobile apps across 3000+ different browsers, operating systems, and real device combinations. Using LambdaTest, businesses can ensure quicker developer feedback and hence achieve faster go to market. Over 500 enterprises and 1 Million + users across 130+ countries rely on LambdaTest for their testing needs.    

### Features

* Run Selenium, Cypress, Puppeteer, Playwright, and Appium automation tests across 3000+ real desktop and mobile environments.
* Real-time cross browser testing on 3000+ environments.
* Test on Real device cloud
* Blazing fast test automation with HyperExecute
* Accelerate testing, shorten job times and get faster feedback on code changes with Test At Scale.
* Smart Visual Regression Testing on cloud
* 120+ third-party integrations with your favorite tool for CI/CD, Project Management, Codeless Automation, and more.
* Automated Screenshot testing across multiple browsers in a single click.
* Local testing of web and mobile apps.
* Online Accessibility Testing across 3000+ desktop and mobile browsers, browser versions, and operating systems.
* Geolocation testing of web and mobile apps across 53+ countries.
* LT Browser - for responsive testing across 50+ pre-installed mobile, tablets, desktop, and laptop viewports
    
[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

      
## We are here to help you :headphones:

* Got a query? we are available 24x7 to help. [Contact Us](support@lambdatest.com)
* For more info, visit - [LambdaTest](https://www.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby)
