# VR-setup

We study the neural activity of mice's hippocampus using optogenetics methods.
Specifically, we are training mice to navigate in VR environment for studying in-vivo place-cells activity using voltage-imaging technique.

Here we share our homemade hardware &amp; software experimental setup.

<img src="https://user-images.githubusercontent.com/98536980/152039157-080e52ce-9548-43cd-a01d-442dcaa100bd.gif" width="500" height="400">

## 3d printings
 
 We Used [Arthur Sugden](https://github.com/asugden/bebox/tree/master/3d/wheel) model with slight changes.
 
 The modified model's `.SCAD files` can be found in `3D printing models` directory which contains models for:
 
 - The wheel
 - U shape construct for the wheel axis
 - Screen for VR projection
 
 
## Electronics & more

- [capacitance sensor](https://www.sparkfun.com/products/12041) - for mice licks detections.
- [solenoid valve](https://theleedifference.com/products/#solenoid-valves/3) - for reward control.
- [H bridge](https://m.banggood.com/10-Pcs-Geekcreit-L298N-Dual-H-Bridge-Stepper-Motor-Driver-Board-p-1054211.html?utm_source=googleshopping&utm_source=googleshopping&utm_medium=cpc_organic&utm_medium=cpc_bgs&gmcCountry=IL&utm_content=minha&utm_content=sandra&utm_campaign=minha-il-en-mb&utm_campaign=sandra-ssc-il-all-0507&currency=ILS&cur_warehouse=CN&createTmp=1&ad_id=519822680399&gclid=Cj0KCQiA6NOPBhCPARIsAHAy2zBwOR6kqKPrn7NYVQt2XXXowL66YlR-dfJfsxjh51QuHRhCAJZCJ7saAtPREALw_wcB) - for 12V voltage supply for the valve.
- [Rotary encoder](https://www.ia.omron.com/data_pdf/cat/e6b2-c_ds_e_6_1_csm491.pdf?id=487) - for wheel spinning detection.
- [Arduino Uno](https://docs.arduino.cc/hardware/uno-rev3) - controlling the electrical devices.
- [LED projector](https://www.optoma.com/ap/product/ml750st/#) - for project the VR environment in front of the mice.
- [Bearings](https://www.4project.co.il/product/flanged-ball-bearing-5x14x5)
- [Motor](https://www.4project.co.il/product/micro-metal-gearmotor-lp-54rpm-encoder-shaft)

## Hardware all together

 We based the Wheel on [ThorLabs Board](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=159) with ThorLabs basic rods.
 The mice head was fixed by [Neurotar head fixation system](https://www.neurotar.com/the-mobile-homecage/#stability).
 
<img src="https://user-images.githubusercontent.com/98536980/152039318-e970ad76-c7f7-4bf8-936f-f8c45221edb3.jpeg" width="300" height="350">

 Tube (filled with 10% sucrose water for reward delivery), was connected to [Neurotar lick port](https://www.neurotar.com/the-mobile-homecage/#stability) 
 from one end, and to solenoid valve from the other end. 
 The solenoid valve was connected to an H-bridge for voltage supply.
 An electrical wire was soldered to the edge of a needle which compose on the lick port.
 This wire was connected to a capacitance sensor for mice lick detection.

<img src="https://user-images.githubusercontent.com/98536980/152039358-6db3975e-dfc3-45fc-8f1e-7cf7f580c015.jpeg" width="300" height="350">

 A rotary encoder was fixed on the shaft of the wheel spinning indication.
  
<img src="https://user-images.githubusercontent.com/98536980/152039393-15f94a31-0364-4099-9c3a-60a78214d7ac.jpeg" width="300" height="350">

 The H-bridge, capacitance sensor and the rotary encoder was connected to an arduino uno.
 The arduino was connected to a standard computer, which the ViRMen software was installed on.
 Beside the regular monitor of the computer, a projector was connected to it too.
 The projector was mount on the ThorLabs board and project the VR enviroment on 3d printted screen that was placed in front of the wheel.
 
<img src="https://user-images.githubusercontent.com/98536980/152039487-7858f3c2-c7bf-4502-821c-9ef62dac772b.jpeg" width="400" height="250">
 
## Software

The VR rendering designed and executed by [ViRMEn v.2016-02-12](http://pni.princeton.edu/pni-software-tools/virmen-download).
Configurations files for 3 different VR worlds can be found at [`ViRmEn\Mice_Training.mat`](https://github.com/yoavadamlab/VR-setup/tree/main/ViRmEn).

Beside the VR design we had to control on the following:
- Progress of the VR according to the mice movement on the wheel
- Release specific amount of reward (i.e. sucrose water) at specific location (i.e. reward zone)
- keep track of the mice licking the lick port (for learning rate analysis)
- Save the behavioral data from the training and Imaging sessions for future analysis

Based on our `Mice training protocol.pdf` we desined specific training logic for each training stage. In the begining of each training session, the trainer need to declare the current training stage:

<img src="https://user-images.githubusercontent.com/98536980/152346139-fcaaa5a1-cf53-491e-b12b-43afecabe5d1.jpeg" width="120" height="150">

Then, the mouse meta-data should be given:

<img src="https://user-images.githubusercontent.com/98536980/152346599-a7af7c9b-0426-423c-9dd2-fcf7cce3f366.jpeg" width="120" height="150">

Now the training begin. We can see during the training how does the mice preforms:

<img src="https://user-images.githubusercontent.com/98536980/152347088-6d8f3362-81f3-4c35-bcaa-c08bd8368aa9.jpeg" width="300" height="200">

After the training finished the mouse training data saved as csv.file and automated python script us runnig to preform anlytics of the current training session. The script send summary data to the lab members emails with the cuurnet day data and with plots about the training history of the mouse:

<img src="https://user-images.githubusercontent.com/98536980/152347980-54f78c41-0e4e-4b14-9f4c-53d236ccaf72.png" width="300" height="200">

have a look on the [daily summary plots](https://github.com/yoavadamlab/VR-setup/files/7994692/daily_plots.2.pdf)

## Contact us

for more information and quetsions you are welcome to contact us by opeening an issue.


