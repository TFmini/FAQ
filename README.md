# FAQ
Frequently asked questions and answers of TFmini and TFmini-Plus.

# TFmini-FAQ
1. Q：Can the TFmini be tested on the surface of the water？  
A：It is not recommended to detect on the water surface. Due to the principle of lidar ranging, 
it will penetrate the water surface, resulting in inaccurate ranging. Opaque liquids are viable, but there is a risk of failure.
2. Q: When will the peak current of TFmini occur? What will happen if the power supply is insufficient?  
A: There will be A peak current when the LED lights, about 1.6ms after starting. If the power supply is insufficient, an error will be reported, and the current is insufficient, which will bring down the  voltage.
4. Q: What is the power supply level and data level of TFmini-IIC?  
A:Supply voltage is 5V, and data level is 3.3v; If your supply voltage is only 3.3v，an optional 3.3v adapter is available.
5. Q: What is the meaning of 1.25-4p terminal (Molex 510210400) terminal connectors? Where to buy it?  
A: This is the connector. You can find it from Molex, amazon and alibaba.
6. Q: Is there any pull-up resistor in the TFmini-IIC version? What is the resistance value? Can it be removed?  
A: Yes, 2.2k, can't be removed.
7. Q: The chip of the radar generates a lot of heat during the working process. Is it necessary to add heat sinks?  
A: The radar has been verified by internal test that the temperature rise in the working process of the radar will not affect the stability of the radar. Through internal fatigue detection, it can be used normally without heat sink, but if it is willing to add heat sink, it will be beneficial to the stability of radar measurement.
8. Q: How to get the data and how to connect the ports?  
A: The radar uses the serial port transmission UART by default. The communication level LVTTL is 3.3V, the baud rate is 115200, and the power supply voltage is +5V. The terminal type of the cable: one is GH1.25-4P for connection with TFmini and the other end is for ordinary 1.25-4p terminal for connecting devices.
	1. You can use the "radar-TTL /USB - computer" sequence from the computer to obtain data, but also can use a computer or serial port assistant for parameter configuration.
You need to use "USB-TTL " switchboard (you can purchase the switchboard through the 
company's TAOBAO official website, or purchase the switchboard online by yourself), the line sequence is TX<>RX; RX<>TX, it can be self-disassembled and welded, as shown in the figure below.
	2. You can directly connect with your development board, TFmini can connect with any development board that provides serial communication, as long as the development board has a serial port, it can read radar data, and according to the changes of data you can process it.

9. Q: How to reduce the power consumption of TFmini?  
A: You can try the following methods to control radar power consumption:
	1. Set the external trigger mode for measurement and reduce the frame rate, thereby reducing power consumption. This method is suitable for the scene with low frame rate requirement. (recommended)
	2. Control the power supply of 5V on and off. This method is suitable for scene where you only need to work at a certain time.
	3. Set a low range of working mode to ensure stable power consumption. The method is suitable for only specific proximity measurements.

10. Q: Does TFmini have a driver in Linux, can the radar be communicated on Linux? Does TFmini have an SDK based on Linux?  
A: At present, there is no driver under Linux, but the radar is a serial port data output, which can be directly connected to PC through TTL-USB module, and then analyzed through serial port protocol， so there is no need to drive. It has no SDK and reads data directly through a serial port.

11. Q: How to modify the baud rate? Can the host computer make changes?  
A: Baud rate can be modified. The host computer does not support modification at present. You can modify it by sending commands through serial port assistant.

12. Q: Can we add the serial cable of TFmini? Does the lengthening affect data communication? What is its maximum communication length?  
A: TFmini uses serial TTL communication interface and IIC communication interface. These two kinds of communication do not support long-distance transmission; the longest cable length recommended by TTL communication should not exceed 2m; the recommended cable length of IIC communication should not exceed 1m; After the cable is extended, it may cause errors in frames, with the risk of reducing it；In order to improve the transmission the baud rate can be reduced appropriately；At present, at the baud rate of 115200, the cable length can be extended to 1.5m, which has no impact on data communication.
13. Q: How long is the power on the radar? How long does it take to power up to work? What is the communication time of each frame?  
A: The power on time of the radar is 30ms, and the power on time of executing the program will be 500ms. The communication time of each frame is: （1/115200）*8*9=0.625ms。

14. Q: Can the TFmini be used in battery-powered systems?  
A: Radar can be used for battery-powered equipment, but the battery output voltage should meet 5V± 0.1V.

15. Q: Is it possible to reset the device by sending a serial command instead of turning off the power?  
A: You can send this command without re-powering: 42 57 02 00 00 00 00 01.

16. Q: There is data output within 30cm, can it be used?  
A: The value measured in the blind zone is not credible. In the blind zone of TFmini, the data within 0-1m will appear according to the reflectivity of the target. Therefore, the data in the blind zone should be used cautiously. If the usage scene is single, the distance value can be distinguished according to the signal strength.

17. Q: What is the life of the TFmini when the radar works for 8 hours a day within the range of 0-40℃?  
A: The short life of TFmini is LED, which can reach 30000h-50000h in general. Therefore, the product life can reach more than 30000h at room temperature of 25℃, equivalent to more than 3 years.

18. Q: Is there any correlation between radar accuracy and baud rate?  
A: the accuracy of radar ranging is independent of the baud rate.

19. Q: The host computer was used to connect the radar, but the coms port did not appear. How to deal with this situation?  
A: 1.  First ensure that the power supply is normal, the connection cable is stable and reliable; at this time, observe the inside of the TFmini emission lens, you can see the weak red light;
	2) Check if the serial port driver is installed. If not, please install the driver according to the model of the serial port chip;

20. Q: Why does the radar start to output data at an interval of 724ms after the reset command of TFmini-IIC version is issued? Why send instructions to“exit configuration”mode?  
A: The reset command is special. After resetting, it is recommended to wait for 1s and then send other configuration commands to the radar. Moreover, the reset command is designed to avoid the failure to recover after the customer configuration error. It is not recommended that you send the command too frequently; The "exit configuration mode" command may not be sent, It just gets the product going; Often the product will work after you restart.

21. Q: How does the radar achieve 485 communication?  
A: At present, the radar does not have a 485 interface and requires a TTL to 485 conversion module. This conversion module is sold online.

22. Q: Why does the command to modify the frame rate "42 57 02 00 EE FF 00 07" mean 100 Hz?  
A: "EE FF is not A number, it's just a sign for it. 100 Hz is 10 ms, 10 is 0A, and the code is 42, 57, 02, 0A, 0007; 20 Hertz is 50 milliseconds. 50 is 32, so the setting code is 42, 57, 02, 32, 00, 00, 07."

23. Q: Can the radar be supplied with 3.3v voltage?  
A: No, but the 3.3v power supply can be achieved in the form of lifting platen.

24. Q: Why the data will continue to be output when the serial port assistant is configured as an external trigger and then exits the configuration mode? Did the configuration fail?  
A: There is no need to exit the configuration command after the configuration is triggered externally.
Meanwhile, the measurement mode is triggered for power failure without saving. Once configured, if power is cut off or reset commands are sent, the radar will revert to 100Hz spontaneous measurement.

25. Q: Does TFmini come with its own level conversion chip?  
A: Not at the moment. You can connect it directly to the serial port end. If you want to connect to a computer, you need to switch.

26. Q: Does the IIC address of TFmini need to be modified many times, or just once?  
A: After the TFmini modifies the IIC address, it will be saved, but it needs to be repowered or reset to take effect.

27. Q: How many addresses can IIC assign at most? How many TFmini can connect on a bus?  
A: According to the manual, the address range of IIC is 0x10~0x78, so the maximum number of independent addresses can be supported theoretically. About the available quantity, 10 have been tested, and dozens should be no problem in theory.
Note: when there is too much load on the IIC bus, high frequency communication may be affected because the capacitance between the buses cannot be filled.

28. Q: Can TFmini communicate on non-windows systems?  
A: TTL-USB does not distinguish between systems. Whether it is A Windows system or not, normal communication can be achieved as long as corresponding drivers are installed on different systems.

29. Q: After using, when the radar cable is forcibly pulled out, the radar terminal falls.  
A: When you unplug the radar connector, you should not unplug it by force. You should gently press it and then unplug it. Specific operation can refer to the following radar using small video.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190927142703294.png)

29. Q: Can we dismantle the Fmini radar when it fails?  
A: You can't take it apart. First of all, we will have calibration test for each radar. If the normal radar is disassembled and reassembled, it will lead to abnormal accuracy. Secondly, the dismantling may also cause damage to some areas of radar hardware. Thirdly, the dismantler will destroy the first site where the radar goes wrong, so the after-sales cannot analyze the real cause of the problem. If you suspect radar failure, you can contact Benewake after - sales.

30. Q: After sending configuration commands to the radar, if other operations are carried out within a very short time (below 30ms), will it have any impact on the radar?  
A: After sending configuration commands, the waiting time is too short (below 30ms) and other operations are carried out, which may lead to damage of radar program. It is recommended to wait at least 500ms from power on to configuration TFmini.
31. Q：Normally, the frame header should be 0x59 0x59. Why does 0x53 0x53 occur (as shown below)?  

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190927142753797.png)

  A：The reason for this is that the converter used may be USB to RS232, not USB-TTL serial port converter. USB-TTL is recommended to avoid this situation. Reference：
https://www.amazon.com/DSD-TECH-Converter-Compatible-Windows/dp/B072K3Z3TL/ref=sr_1_10?keywords=TTL-USB&qid=1567404735&s=gateway&sr=8-10

# TFmini-Plis-FAQ 
1. Q: how many meters can the serial port cable be extended? How to achieve long-distance communication?  
A: It is not recommended that the maximum distance of the connection cables supported by TTL interface communication should be more than 2m. Switch board can be selected to realize long-distance communication through other interfaces.

2. Q: Will configuration parameters be automatically written and automatically saved after power failure? Does it need to send "save settings" commands?  
A: It doesn't save automatically. You need to send a save command. When you send only modified commands without saving, the radar will resume its output after restarting according to its previous configuration. Saving is equivalent to writing the modified settings

3. Q: How to set the radar for single test?  
A: Single trigger measurement can be implemented in the following ways:
	1. send a command to modify the frame rate, and modify the frame rate to 0, that is, turn on the single trigger measurement switch: 5A 06 03 00 00 63
	2. Send the trigger command: 5A 04 04 63. Each time the command is sent, the TFmini Plus measures once and outputs the result.
	3. Save command: 5A 04 11 6F

4. Q: How to solve the problem of crosstalk with multiple TFmini-Plus?  
A: TFmini Plus does not generate crosstalk when it is not facing; If the TFmini Plus needs to be installed under special conditions, the radar can be set to a single trigger test, staggering the measurement time to avoid mutual interference.

5. Q: What is the current value when 3.3 VDC is output from I/O port?  
A: According to the test, the maximum current I/O can output is 8mA.

6. Q: Can infrared camera see the spot of TFmini Plus?  
A: Sure. Infrared cameras can refer to https://item.taobao.com/item.htm?spm=a1z10.5-c.w4002-15093766596.41.50fa7b53pyNoi1&id=544961710314
If you want to buy other infrared cameras, choose products with a visible central wavelength of 850nm.

7. Q: What is the life of the TFmini?  
A: The short life of TFmini is LED, which can reach 30000h-50000h in general. Therefore, the product life can reach more than 30000h at room temperature of 25℃, equivalent to more than 3 years.

8. Q: What are the functions of temperature and signal strength in data in practical application?  
A: The temperature in the data refers to the chip temperature, which has no special reference significance. Signal strength can help determine the accuracy of distance data.

9. Q: What performance degradation will be caused by setting the high frame rate?  
A: The frame rate is related to the data fluctuation. The higher the frame rate is, the larger the data fluctuation range is. For details, please refer to the introduction of repetition accuracy in the manual.

10. Q: Can you remove the shell of the product?  
A: No. Lens needs to be installed in the shell, which requires very high precision. The absence of a shell has a significant impact on product performance.

11. Q: How is the power consumption of TFmini Plus calculated?  
A: The power consumption of TFmini Plus is: 5V voltage supply. The measured current fluctuates between 110-120mA. Take 110mA to get 550mW.

12. Q: What is the maximum voltage that the radar can withstand? Can it be battery powered?  
A: Radar is very sensitive to power supply. Power supply higher than 5.5v may damage it, and lower than 4.5v cannot guarantee accuracy. It can use battery power supply. If the power supply does not match, it is recommended to use a transformer that supports both a wide range of high input voltage and stable output voltage.

13. Q: Can the PC software provide development code?  
A: The host computer source code is not available, but we can provide the parsing code that can get the radar distance program.

14. Q: To ensure stability, how long before the radar is powered for testing?  
A:The startup time is about 500ms. After startup, it can output normally.

15. Q: Is there any way to reduce the power consumption?  
A: The power consumption can be reduced by the single trigger of the measurement command;

16. Q: What is the radar interface? Does the data need to be specially decrypted?  
A: There are TTL, IIC and IO interfaces of radar, and the data format can be analyzed in the manual.

17. Q: What is the difference between accuracy and distance resolution mentioned in the manual?  
A: Accuracy is the difference between the measurement result and the actual distance, and distance resolution is the minimum distance that can be recognized by radar.

18. Q: Can the radar work outdoors on sunny days? (<70klux or sun can illuminate about 100klux).  
A: We can guarantee the radar to work properly within 70klux, but it does not mean that the radar will fail after exceeding 70klux.

19. Q: What is the standard frame rate of radar?  
A: The standard frame rate of 1000,500,250,200,125,100,50,40,25,20,10,5,4,2,1

20. Q: What will be the effect on the radar transmitter if it is shielded? How much does dust affect it?  
A: No shielding at the radar transmitter; Dust weather will have close range false alarm. Roadside dust, in theory, has no effect.

21. Q: Can the radar work less than 1Hz?  
A: Currently, it is not supported, only 1-1000 integers are supported. For lower frequency measurement, it is suggested to adopt single trigger measurement mode.

22. Q: What's the difference between system reset and factory reset?  
A: System reset means program restart; Restore factory settings are the parameters of the flash configuration to clear and restore to the default state.

23. Q: Is it necessary to add protective cover for outdoor application? Is the light source laser?  
A: the radar has added filters, which can meet basic outdoor applications. It can increase the protective cover, but it needs to pay attention to the effect of crosstalk, the glass should be close to the front surface, not too thick, it is best to be measured. LEDs for light sources have no problem with ordinary glass transmittance.

24. Q: Is the radar usable in rainy weather?  
A: The radar can work normally in the rain, but it will be affected to some extent during heavy rain.

25. Q: What's the difference between the radar measurements at night and during the day?  
A: Radar works better at night than during the day. During the day, depending on the intensity of sunlight, if the intensity is high, the accuracy will decrease, but not too much, the maximum is not more than ±10cm.

26. Q：Is it possible to detect liquids?  
A：It is not recommended to detect on the surface of the water. Due to the principle of optical radar ranging, it will pass through the water surface, resulting in inaccurate ranging. Opaque liquids are feasible, but there is a risk of failure.

27. Q: if the wiring sequence is wrong during use, will it directly burn out the radar?  
A: if only the two cables of communication are reversed, it won't burn out the radar. However, if the power cable is connected incorrectly, as long as the power is turned on, the radar will be burned out, so the line sequence must be accurate.


