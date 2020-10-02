# Use AMD for your Mac to accelerate Deeplearning

[<img src="XXXXXXXX">](
httpsasdfafasfasfdasf)
xxxxxxx - httpsasdfafasfasfdasf

Every machine learning engineer these days will come to the point where he wants to use a GPU to improve his deeplearning calculations.



## Table of Contents


## Pre-requisits

If you want to follow along, you should have
- a Mac OS
- an external AMD GPU
- [Keras](https://keras.io/), as deep learning library


## What I am having



### MacOS Catalina

```sh
System Version: macOS 10.15.6 (19G2021)
Kernel Version: Darwin 19.6.0
Boot Volume: Macintosh HD
Boot Mode: Normal
Secure Virtual Memory: Enabled
System Integrity Protection: Enabled
```

### External GPU

Runnning

```sh
system_profiler SPDisplaysDataType
```

will give you the Graphics/Display output.

It shows my external GPU:

```sh

    Radeon RX 5700 XT:

      Chipset Model: Radeon RX 5700 XT
      Type: External GPU
      Bus: PCIe
      PCIe Lane Width: x4
      VRAM (Total): 8 GB
      Vendor: AMD (0x1002)
      Device ID: 0x731f
      Revision ID: 0x00c1
      ROM Revision: 113-D1990103-O09
      Automatic Graphics Switching: Supported
      gMux Version: 4.0.29 [3.2.8]
      Metal: Supported, feature set macOS GPUFamily2 v1
      GPU is Removable: Yes
```

### Library versions

```sh
keras=2.2.4=pypi_0
keras-applications=1.0.8=py_1
keras-preprocessing=1.1.0=py_0

plaidbench=0.7.0=pypi_0
plaidml=0.7.0=pypi_0
plaidml-keras=0.7.0=pypi_0
```


## Connect external GPU to Mac




## plaidml-setup


![](../assets/amdGpuOnMac_2020-09-30-19-01-21.png)

## plaidbench keras mobilenet


![](../assets/amdGpuOnMac_2020-09-30-19-04-11.png)


## Additional reading

- [Use an external graphics processor with your Mac](https://support.apple.com/en-ug/HT208544)



---

## About

Daniel is an entrepreneur, software developer and lawyer. He has worked at various IT companies, tax advisory, management consulting and at the Austrian court.

His knowledge and interests currently revolve around programming machine learning applications and all its related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.

Don't hesitate to get in touch if you have ideas, projects, or problems.

![You can support me on https://www.buymeacoffee.com/createdd](/2020/assets/template_2020-09-25-22-32-52.png)
You can support me on https://www.buymeacoffee.com/createdd

![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)
- [createdd.com](https://www.createdd.com/)
