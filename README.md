## Sauce Labs Devices
#### `python` Edition

<br>
<img align="right" src="assets/logo_7.png">  



| :rocket: [Sign Up for a _free_ trial at Sauce Labs][3] :bangbang: |
|:----------------------------------------------------------------- |
| :page_facing_up: [Source `python` Repo][7] and [README][8]        |
| :page_facing_up: [Dynamic Device Allocation][13]                  |
| :page_facing_up: [Selenium Python Course][11]                     |
| :page_facing_up: _`saucelabs`_ [Documentation Home][10]           |
| :page_facing_up: _`saucelabs`_ [Knowledge Base][12]               |
| :page_facing_up: _`saucelabs`_ [API Reference][9]                 |




&nbsp;

### _Quick Start_

- _`pipenv`_ Required
- Set Environment Variables
  - _`SAUCE_USERNAME`_
  - _`SAUCE_ACCESS_KEY`_
- Download Repo and Create _virtualenv_  

&nbsp;

```shell
# clone repo
git clone https://github.com/kmissoumi/demo-python.git && cd demo-python

# setup virtualenv
pipenv install

# enter virtualenv
pipenv shell

# optional info
python --version      # Python 3.9.9
pipenv --version      # pipenv, version 2021.11.23             


# notes // the test suite referenced below has (5) tests

# run the entire test suite once, (5) tests
# on the same (1) device, cacheId key with the same UUID as the value for each test
pytest best_practice/mobile_native/android --dc=us

# run the entire test suite, (5) tests, on (N) devices
pytest best_practice/mobile_native/android --dc=us -n20



# run all (5) tests, twice on a single device
pytest best_practice/mobile_native/android --dc=us --count 2 

# run all 


```

   </br>

---

## _Dynamic Device Allocation_

   </br>

> _Note:_ _Only_ update the _rdc_browser_ in [best_practice/conftest.py](best_practice/conftest.py#L163)
>   
> _Suggestion:_ _Only_ update one capability at a time for your first few reps. 


### _[Dynamic Device Allocation](https://docs.saucelabs.com/mobile-apps/supported-devices/#dynamic-device-allocation)_  

- [deviceName](https://docs.saucelabs.com/dev/test-configuration-options/#devicename)
- [platformVersion](https://docs.saucelabs.com/dev/test-configuration-options/#platformversion)
- [platformName](https://docs.saucelabs.com/mobile-apps/automated-testing/appium/real-devices/#specifying-the-platformname)  

### Set the Device _Type_ and/or _Pool_

- [tabletOnly](https://docs.saucelabs.com/dev/test-configuration-options/#tabletonly)
- [phoneOnly](https://docs.saucelabs.com/dev/test-configuration-options/#phoneonly)
- [privateDevicesOnly](https://docs.saucelabs.com/dev/test-configuration-options/#privatedevicesonly)
- [publicDevicesOnly](https://docs.saucelabs.com/dev/test-configuration-options/#publicdevicesonly)



    </br>
 > _Hint:_ Run multiple test suites on the same device with _[cacheId!](https://docs.saucelabs.com/dev/test-configuration-options/#cacheid)_

    </br>


---

## Example Capabilities

   </br>


```python
# specific device via id
caps = {
    'deviceName': 'iPhone_12_POC137',
    'platformName': 'iOS',
    'cacheId': 'yogi'
}
```

> _Hint_: [Find Device Id, Details, and Availability _theEasyWay!_](https://gist.github.com/kmissoumi/b54d5abc87658e8e30314175be2c61a5)


   </br>

```python
# any iPhone from my private device pool
caps = {
    'deviceName': 'iPhone.*',
    'platformName': 'iOS',
    'cacheId': 'booboo',
    'privateDevicesOnly': True
}
```

   </br>

```python
# any iOS 15.x phone from the public device pool
caps = {
    'deviceName': '.*',
    'platformName': 'iOS',
    'platformVersion': 15,
    'phoneOnly': True,
    'cacheId': 'cindy',
    'publicDevicesOnly': True
}
```

   </br>
```python

# any Android 10 phone or tablet 
caps = {
    'deviceName': '*',
    'platformName': 'Android',
    'platformVersion': 10,
    'cacheId': 'ranger'
}
```

   </br>

---

## References

- [Documentation Home](https://docs.saucelabs.com)
- [Demo Repos](https://github.com/saucelabs-training/)
  - [Source demo-python Repo](https://github.com/saucelabs-training/demo-python) and [README](https://github.com/saucelabs-training/demo-python/blob/main/README.md) file
- [Support Central](https://support.saucelabs.com/hc/en-us)
- [Knowledge Base Articles](https://support.saucelabs.com/hc/en-us#knowledge-base)
  - [Tips & Troubleshooting for Device](https://support.saucelabs.com/hc/en-us/sections/115000518514-RDC-Mobile-Application-Testing-Tips-and-Troubleshooting)
  - [Session, Job, and Appium Ids Explained](https://support.saucelabs.com/hc/en-us/articles/360062316954-Session-ID-Job-ID-and-Appium-Session-ID-What-is-the-difference-)
- [Sauce School](https://training.saucelabs.com) Training Resources
  - [Selenium Python Course](https://training.saucelabs.com/seleniumpython/)
- [Videos](https://saucelabs.com/resources/videos) & [Webinars](https://saucelabs.com/resources/webinars)
- [Data Sheets](https://saucelabs.com/resources/data-sheets)
  - [Device Cleanup Procedures](https://saucelabs.com/assets/19LV8PISelZ5na3uwghC1x/5e2846c6c4c4aed55e97db30a301f2b6/DS__Device_Cleanup_Procedure.pdf)
- [Papers & Reports](https://saucelabs.com/resources/white-papers)
- [Case Studies](https://saucelabs.com/resources/case-studies)
- [YouTube Channel](https://www.youtube.com/user/saucelabs/videos)
- [API Reference](https://docs.saucelabs.com/dev/api/#accessing-the-apis)
- [CLi Reference](https://docs.saucelabs.com/dev/cli/)
- [Glossary of Sauce Labs Terminology](https://docs.saucelabs.com/dev/glossary/)
- [Common Error Messages](https://docs.saucelabs.com/dev/error-messages/)
- [System Status](https://status.saucelabs.com) & [Maintenance Windows](https://docs.saucelabs.com/dev/data-center-maint/)
- [Platform Configurator](https://saucelabs.com/platform/platform-configurator#/)

---

### Device Cleanup

#### Per Session _[Device Cleanup](https://docs.saucelabs.com/mobile-apps/supported-devices/#real-device-cleaning)_ Steps

- accounts and data _cleared_
- default browser history and user data _removed_
- non-default browsers _uninstalled_
- network settings _reset_
- device settings _reset_
- app _uninstalled_
- cached data _deleted_
- device _de-allocated_








&nbsp;

[1]: <https://docs.saucelabs.com/testrunner-toolkit/configuration/common-syntax/#mode>
  "Test Runner Toolkit Common Syntax"
[2]: <https://docs.saucelabs.com/testrunner-toolkit/ide-integrations/vscode>
  "Test Runner Toolkit IDE Integration w/ Visual Studio Code"
[3]: <https://saucelabs.com/sign-up>
  "Sauce Labs Free Trial!"
[4]: <https://docs.saucelabs.com/testrunner-toolkit/>
  "_saucectl_ Docs"
[5]: <https://docs.saucelabs.com/testrunner-toolkit/saucectl/)>
  "_saucectl_ CLI Reference"
[6]: <https://docs.saucelabs.com/testrunner-toolkit/configuration/espresso/>
  "_saucectl_ YML Reference"
[7]: <https://github.com/saucelabs-training/demo-python>
  "source _demo_ python repo"
[8]: <https://github.com/saucelabs-training/demo-python/blob/main/README.md>
  "source _demo_ python readme"
[9]: <https://docs.saucelabs.com/dev/api/#accessing-the-apis>
  "reference docs _api"
[10]: <https://docs.saucelabs.com>
  "documentation home"
[11]: <https://training.saucelabs.com/seleniumpython>
  "Selenium Python Course"
[12]: <https://support.saucelabs.com/hc/en-us#knowledge-base>
  "Knowledge Base Articles"
[13]: <https://docs.saucelabs.com/mobile-apps/supported-devices/#dynamic-device-allocation>
  "Dynamic Device Allocation"



  [100]: best_practice/conftest.py