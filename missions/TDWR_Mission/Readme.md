# Monitor Terminal Doppler Weather Radar (TDWR) Channels with Spectra Record

## Prerequisites 

Download my TDWR Channel Profile that should be used for this mission, and hopefully you do not live near any Wi-Fi radios using these channels because then the record function (see instructions) will not work. You can see if you live near any weather radar on this site http://eumetnet.eu/wp-content/themes/aeron-child/observations-programme/current-activities/opera/database/OPERA_Database/index.html (Thank you Rene Kriedemann, https://2ndwave.de/blog/, Twitter - @wifiwise).

Hardware that is used is a Spectran 500X with pre-amp license that will help with the recive sensitivy, if you use a Spectran V6 Eco with lesser RTBW you can just change the center frequency (added in the profile) to monitor live the channel you want to look at.

## About the mission

(picture)

The mission starts with a **Calibration Block** (https://v6-forum.aaronia.de/forum/topic/calibration-block/) where you add any loss, gain for the Rx. In this mission I have not added anything, but I would highly recommened using an Antenna from Aaronia with callibration points for the frequency range you monitor so the data you see ends up being more correct based on the capabilites of the antenna. But, for this lab it is not that important.

Next block is the **Spectran V6 Block** (https://v6-forum.aaronia.de/forum/topic/spectran-v6-block/) where I have turned on ** Temperature Fan Control ! ** so my fan does not go at 100% all the time, this can be changed under Board Config in the block settings. 

Up next is the **IQ Power Spectrum Block** (https://v6-forum.aaronia.de/forum/topic/iq-power-spectrum/), this blocks converts raw I/Q data via real-time FFT to SPECTRA data.
To keep the calculations working on weaker CPUs I have set the FFT Sice to 1024 under Main settings in the block config. This can be changed lover or higher but higher will of course use more CPU because the CPU will do more IQ to FFT calculations and changing it to low will not give you much detail. Change this as needed for your computer.

The Spectra data is feeded into Histogram, Spectrum and Waterfall to help visualise the data. The Spectrum block have a few added traces like Clear Write, Max Hold, Average, Period Buffer and Histogram (turn on, off, change, add or remove as needed). You can read more about the RF Measurement View blocs here: https://v6-forum.aaronia.de/forum/forum/rf-measurement-views/# 

The **Spectum Condition Block** have three Frequency Masks that is added (change as needed) that will stream any data that enters these masks to a new waterfall block to show you any filtered data, and to a File Writer block. 

(picture)

## How to use this mission

_Hopefully you do not have any Wi-Fi radios using these channels (but I often do see cheap SoHo routers on these channels :( ) so the radar is not hidden (if any)_

Turn on and start the Spectran V6 from the menu, change to the IQ Rate you have available. I would recommend using 1/2 span so you do not get any DC spikes at the center of the center of the channel (https://v6-forum.aaronia.de/forum/topic/different-cw-power-displayed-in-full-span-compared-to-1-2-1-4-etc/). Depending on your IQ rate you could end up not seeing all channels, so change the Center Frequency to one of the channels, or use Full Span with a slighly chifted center frequency so you the DC spikse do not interfere the view of the frequency you are monitoring.

Press "Auto Ref Level" if you use any Amp and/or pre-amp. If you have any radar nearby on these channels you will clearly see a pulse at the center frequency at a few Mz, and if this signal rises above the thershold you will see it in the Waterfall Filtered view. 

Start Record (after creating a save spot for the file at the "burger menu) and now ANY frequency that enters the Spectrum Condition Block will be recorded. 

Look at this very short high pulse that I recorded "looping" in 3D File Reader Mission (remove IQ Power Spectrum from file reader when using Spectra Data).

(Picture)



