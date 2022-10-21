# lrs-pager-systems-bruteforce
Long Range Pager Systems  pagers and coasters URH and YS1 (yardstick one / cc11xx) information and brute force tool
# lrs-pager-systems-bruteforce
Long Range Pager Systems  pagers and coasters URH and YS1 (yardstick one / cc11xx) information and brute force tool
Inspired by [Tony Tiger's prior work using the HackRF One](https://github.com/tony-tiger/lrs)

I used the [LRS Transmitter Tuneup manual](https://fccid.io/2AB6OTX1605/Parts-List-Tune-Up-Info/Tune-Up-Procedures-2357525) to verify the center frequency, deviation, modulation and 

This script requires nothing more than [RfCat](https://github.com/atlas0fd00m/rfcat)
```
Frequency: 467.75 Mhz
Modulation: FSK
Encoding: Manchester
Rate: 626 baud
Samples/Symble: 3200
Sample Rate: 2M
```

This script will brute-force all restauraunt ids, blasting all pagers (pager id 0) with the command to flash for 30 seconds.
```
Alert Commands
1 Flash 30 Seconds
2 Flash 5 Minutes
3 Flash/Beep 5X5
4 Beep 3 Times
5 Beep 5 Minutes
6 Glow 5 Minutes
7 Glow/Vib 15 Times
10 Flash Vib 1 Second
68 beep 3 times
```

```
The protocol generating a pager alert packet is:
preamble header restauraunt_id system_id pager_number 0000 0000 alert_type crc
The crc is given by taking the sum of the hex values and then taking the modulus  of the sum by 255 
For restauraunt 0 and pager 0 (all) with an alert type of 1 the value would be
aaaaaafc2d0000000000000000012b
```
