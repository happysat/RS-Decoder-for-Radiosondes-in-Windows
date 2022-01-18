<!DOCTYPE html>
<html class="no-js" lang="en">
  <head>
  </head>
  <body>
    <div class="wrapAll clearfix">
      <div class="mainsection"><br>
        <div class="article">
          <h1><font style="font-size: 20pt" size="5"><span style="color:
                rgb(0, 0, 0); font-family: &quot;Times New Roman&quot;;
                font-size: 26.6667px; font-style: normal;
                font-variant-ligatures: normal; font-variant-caps:
                normal; font-weight: 400; letter-spacing: normal;
                orphans: 2; text-align: start; text-indent: 0px;
                text-transform: none; white-space: normal; widows: 2;
                word-spacing: 0px; -webkit-text-stroke-width: 0px;
                text-decoration-style: initial; text-decoration-color:
                initial; display: inline !important; float: none;">RS-Decoder
                for Radiosonde's in Windows</span>.</font> </h1>
          <p class="siteSub">
          <div class="articleRight"> <img src="img/rs1.png" alt="rs41s"
              width="82" height="280"><br>
          </div>
          <br>
          <p style="user-select: auto !important; margin: 0px 0px 20px;
            padding: 0px; border: 0px; outline: 0px; font-size: 15px;
            vertical-align: baseline; background: 0px 0px rgb(255, 255,
            255); color: rgb(68, 68, 68); font-family: &quot;Helvetica
            Neue&quot;, sans-serif; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 300; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">A radiosonde is a
            small weather sensor package that is typically attached to a
            weather balloon. <br>
            As it rises into the atmosphere it measures parameters such
            as temperature, humidity, pressure, GPS location etc, and
            transmits this data back down to a receiver base station
            using a radio signal.<br>
            Zilog's<span> </span><span style="user-select: auto
              !important; margin: 0px; padding: 0px; font-size: 15px;
              vertical-align: baseline; background: 0px 0px; color:
              rgb(46, 110, 176); text-decoration: underline;
              -webkit-tap-highlight-color: rgb(0, 0, 0);"></span><span>RS-Decoders
            </span>is a free open source radiosonde decoder for
            Windows/Linux and it supports a wide range of radiosonde
            protocols. <br>
            Together with an RTL-SDR it is possible to receive
            radiosonde signals, and decode them using RS-Decoders.</p>
          <p style="user-select: auto !important; margin: 0px 0px 20px;
            padding: 0px; border: 0px; outline: 0px; font-size: 15px;
            vertical-align: baseline; background: 0px 0px rgb(255, 255,
            255); color: rgb(68, 68, 68); font-family: &quot;Helvetica
            Neue&quot;, sans-serif; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 300; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">This tutorial
            covers some tricky points like setting up Virtual audio
            piping in Windows, and getting the GPS data to route with
            perl to into virtual COM port to use with GPS programs.<br>
            In this example Windows 10 1909 in VirtualBox is used with
            GPS-Mouse, RTL-SDR V3 / Airspy R2 SDR radio, SDR#,
            SDRConsole and APRS-Map Software.<br>
            Install x32 Software version´s for 32 Bit Windows (XP/7 ect)
            and offcourse x64 for 64 Bit Windows.<br>
          </p>
          <p style="user-select: auto !important; margin: 0px 0px 20px;
            padding: 0px; border: 0px; outline: 0px; font-size: 15px;
            vertical-align: baseline; background: 0px 0px rgb(255, 255,
            255); color: rgb(68, 68, 68); font-family: &quot;Helvetica
            Neue&quot;, sans-serif; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 300; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">A new develop
            branch is active 'experimental' demodulation chains, which
            use David Rowe's FSK Demodulator to enable better tracking
            of drifty sondes. <br>
            It is expected that the new experimental demod chain will
            have a slightly higher CPU usage than the legacy chains, <br>
            though the exact impact is minimal.<br>
            <br>
            These demodulators are intended for use in situations where
            radiosonde frequency drift is encountered, E.g. DFM's. <br>
            <br>
            Refer to these tech-note's for details:<br>
            <br>
            <a
href="https://github.com/projecthorus/radiosonde_auto_rx/blob/master/auto_rx/test/notes/2019-04-26_fsk_demod.md"
              target="_blank">https://github.com/projecthorus/radiosonde_auto_rx/blob/master/auto_rx/test/notes/2019-04-26_fsk_demod.md</a><br>
            <a
href="https://github.com/projecthorus/radiosonde_auto_rx/blob/master/auto_rx/test/notes/2019-04-23_rs41_highpass.md"
              target="_blank">https://github.com/projecthorus/radiosonde_auto_rx/blob/master/auto_rx/test/notes/2019-04-23_rs41_highpass.md</a><br>
            <br>
          </p>
          <div class="contentsPanel">
            <div class="contentsHeader">Contents:</div>
            <ul>
              <li> <span></span>Overview
                <ul>
                  <li><span>1.1&nbsp; <a href="#Compile_Decoders_">Compile
                        Decoders</a></span> </li>
                  <li><span>1.2&nbsp; <a href="#Decoder_Scripts_">Decoder
                        Script's</a></span> </li>
                  <li><span>1.3&nbsp; </span><a href="#Setting_up_Virtual_"><span>Setup
                        Virtual Audio/COM Ports</span></a><span><br>
                    </span></li>
                  <li><span>1.4&nbsp;  </span><a href="#SDR_Radio_programs_">SDR
                      Radio Programs</a><span></li>
                  <li><span>1.5&nbsp; <a href="#GPS_Setup_">GPS Setup</a></span>
                  </li>
                  <li><span>1.6&nbsp; </span><span><a
                        href="#Get_it_all_Running_">Get it all running</a>
                      </a> </span></li>
                  <li><span>1.7&nbsp; </span><a 
				        href="#APRS-Map_">APRS-Map</a></li>
                  <li>1.8&nbsp; <a href="#ADB_Android_USB_GPS">ADB
                      Android USB GPS</a>
                  <li>1.9&nbsp; <a href="#Android_WiFi_GPS">Android
                      WiFi GPS</a><br>
                  </li>
                  <li>2.0&nbsp; <a
                      href="https://github.com/happysat/Windows-Subsystem-for-Linux-WSL-and-SDR-in-Windows-10"
                      target="_blank">WSL and SDR</a><br>
                  </li>
		  <li>2.1&nbsp; <a
                      href="https://github.com/happysat/Windows-Subsystem-for-Android-WSA-and-SDR"
                      target="_blank">WSA and SDR</a><br>
                  </li>
                </ul>
          </div>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </p>
          <h2><a name="Compile_Decoders_"></a>Compile
            Decoders&nbsp;&nbsp; <br>
          </h2>
          <br>
          <a href="/RS.zip?raw=true">Download Decoders and Script</a><br>
          <br>
          <a href="https://github.com/happysat/RS-Binaries/tree/main/Windows" target="_blank">Updated
            compiled RS-Decoders are overhere.</a><br>
          <br>
          <b>Unzip rs.zip and move to C:</b><br>
          <br>
          <b>Note:</b><br>
          <br>
          All scripts are having output to com3 (pos2nmea.pl 2&gt;COM3)
          <b>&lt;&lt;-- change this if you have another port number!</b><br>
          <b>Audio device is named "CABLE Output" in all script's!</b><br>
          <br>
          <b>When compiling also put pos2nmea.pl (NMEA perl script) in
            the decoder folder!</b><br>
          The perl script from GIT in folder RS/tools is only for Linux
          Usage.<br>
          <b>Use the one above linked in rs.zip adapted for Windows
            NMEA!</b><br>
          <br>
          <p> <a href="#Setting_up_Virtual_">And skip this part.</a></p>
          <br>
          Or create manually, RS-Decoders can be compiled with <a
            href="https://cygwin.com/install.html" target="_blank">cygwin</a>.<br>
          <br>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Download the
              decoders source files, </b></p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><span></span><a
              href="https://github.com/rs1729/RS/archive/master.zip"
              target="_blank">https://github.com/rs1729/RS/archive/master.zip</a></p>
          <b>Unzip:</b><br>
          cd build/demod/mod<br>
          gcc -c demod_mod.c -w -O3<br>
          gcc -DCYGWIN -c bch_ecc_mod.c -w -O3<br>
          <br>
          <b>For RS-41</b>:<br>
          gcc -DCYGWIN rs41mod.c demod_mod.o bch_ecc_mod.o -lm -O3 -o
          rs41mod -w<br>
          <br>
          <b>DFM:</b><br>
          gcc -DCYGWIN dfm09mod.c demod_mod.o -lm -O3 -o dfm09mod -w<br>
          <br>
          <b>M10, 20:</b><br>
          <br>
          gcc -DCYGWIN m10mod.c demod_mod.o -lm -O3 -o m10mod -w<br>
          <br>
          gcc -DCYGWIN mXXmod.c demod_mod.o -lm -O3 -o mXXmod -w<br>
          <br>
          <h2><a name="Decoder_Scripts_"></a>Decoder Scripts<br>
          </h2>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> <b>Example&nbsp;
              DFM09 Script:</b><br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Create new file
            dfm09.bat with content:</p>
          @echo off<br>
          SET sox_path="C:\Program Files (x86)\sox-14-4-2\"<br>
          SET tail_path="C:\RS\decoders\"<br>
          SET perl_path="C:\Strawberry\perl\bin\"<br>
          SET dfm_path="C:\RS\decoders\"<br>
          %sox_path%sox.exe -q -t waveaudio "CABLE Output" -t wav -
          2&gt;nul | %dfm_path%dfm09mod.exe --dist --ptu -vv --auto
          &gt;&gt;
          C:\RS\log\dfm09_%date:~-4,4%%date:~-7,2%%date:~-10,2%.txt |
          %tail_path%tail.exe -f
          C:\RS\log\dfm09_%date:~-4,4%%date:~-7,2%%date:~-10,2%.txt |
          %perl_path%perl.exe pos2nmea.pl 2&gt;COM3<br>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Save it</b>.<br>
            <br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>Example RS-41
              Script:</b><br>
          </p>
          <p style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;">Create new file
            rs41.bat with content: </p>
          @echo off<br>
          SET sox_path="C:\Program Files (x86)\sox-14-4-2\"<br>
          SET tail_path="C:\RS\decoders\"<br>
          SET perl_path="C:\Strawberry\perl\bin\"<br>
          SET rs41_path="C:\RS\decoders\"<br>
          %sox_path%sox.exe -q -t waveaudio "CABLE Output" -t wav -
          2&gt;nul | %rs41_path%rs41mod.exe --ecc2 --crc -vx --ptu
          &gt;&gt;
          C:\RS\log\rs41_%date:~-4,4%%date:~-7,2%%date:~-10,2%.txt |
          %tail_path%tail.exe -f
          C:\RS\log\rs41_%date:~-4,4%%date:~-7,2%%date:~-10,2%.txt |
          %perl_path%perl.exe pos2nmea.pl 2&gt;COM3<br>
          <b>Save it</b>.<br>
          <br>
          <span style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"><b>What does it
              all mean.</b><br>
            <br>
            <b>rs41mod -h</b><br>
            rs41mod [options] audio.wav<br>
            options:<br>
            &nbsp;-v, -vx, -vv&nbsp; (info, aux, info/conf)<br>
            &nbsp;-r, --raw<br>
            &nbsp;-i, --invert<br>
            &nbsp;--ths &lt;x&gt;&nbsp;&nbsp;&nbsp; (peak threshold;
            default=0.7)<br>
            &nbsp;--iq0,2,3&nbsp;&nbsp;&nbsp; (IQ data)<br>
            <br>
            <b>dfm09mod -h</b><br>
            dfm09mod [options] audio.wav<br>
            options:<br>
            &nbsp;-v, -vv<br>
            &nbsp;-r, --raw<br>
            &nbsp;-i, --invert<br>
            &nbsp;--ecc&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            (Hamming ECC)<br>
            &nbsp;--ths &lt;x&gt;&nbsp;&nbsp;&nbsp; (peak threshold;
            default=0.6)<br>
            &nbsp;--json&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (JSON
            output)<br>
            &nbsp;--ecc2 now also gives the output after each block how
            many bits the error correction has corrected. <br>
            &nbsp;--ptu temperature Info<br>
            &nbsp;--dist is like ecc, but only blocks that belong to the
            same frame are taken, i. if errors occur, the frame is
            discarded / Inversed used for DFM06/90</span><br>
          <span style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"></span><span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </span>
          <h2><a name="Setting_up_Virtual_"></a>Setting up Virtual
            Audio/COM ports&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br>
          </h2>
          <br>
          <a href="https://sourceforge.net/projects/sox/"
            target="_blank">Download the windows version of sox and
            install.</a><br>
          <br>
          <a
            href="https://www.vb-audio.com/Cable/index.htm#DownloadCable"
            target="_blank">Download Virtual Audio Cable and install.</a><br>
          <br>
          <b>Open VB-Audio Control Panel in options change Internal
            Sampling rate to 48000 Hz and reboot.</b><br>
          <br>
          <a
            href="https://sourceforge.net/projects/com0com/files/com0com/3.0.0.0/"
            target="_blank">Download Com0Com x64 Program.</a><br>
          <br>
          <b>Install:</b><br>
          <br>
          <img src="img/com_install.jpg" alt="" width="489" height="380"><br>
          <br>
          Make sure you have a virtual com port, otherwise change the
          number.<br>
          All scripts are having output to com3 (pos2nmea.pl 2&gt;COM3)
          <b>&lt;&lt;-- change this if you have another port number!</b><br>
          <br>
          <img src="img/com_setup.jpg" alt="" width="449" height="391"><br>
          <br>
          If everything is okay you have <b>2 new virtual COM ports</b>
          in Windows Control Panel.<br>
          <br>
          <img src="img/ports_cp.jpg" alt="" width="388" height="382"><br>
          <br>
          <b>Download Perl x64 and install:</b><br>
          <br>
          <a href="http://strawberryperl.com/releases.html"
            target="_blank">http://strawberryperl.com/releases.html</a><br>
          <br>
          Needed for NMEA Perl Script for GPS Output. <span
            style="color: rgb(0, 0, 0); font-family: &quot;Times New
            Roman&quot;; font-size: medium; font-style: normal;
            font-variant-ligatures: normal; font-variant-caps: normal;
            font-weight: 400; letter-spacing: normal; orphans: 2;
            text-align: start; text-indent: 0px; text-transform: none;
            white-space: normal; widows: 2; word-spacing: 0px;
            -webkit-text-stroke-width: 0px; text-decoration-style:
            initial; text-decoration-color: initial;"> </span>
          <h2><a name="SDR_Radio_programs_"></a>SDR Radio Programs<br>
          </h2>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <br>
          <img src="img/sdr.jpg" alt="" width="608" height="363"><br>
          <br>
          <b>SDR#:</b><br>
          <br>
          <a href="https://airspy.com/download/" target="_blank">https://airspy.com/download/</a><br>
          <br>
          <img src="img/sdrc.jpg" alt="" width="609" height="340"><br>
          <br>
          <b>SDR Console:</b><br>
          <br>
          <a href="https://www.sdr-radio.com/Software" target="_blank">https://www.sdr-radio.com/Software</a><br>
          <br>
          <h2><a name="GPS_Setup_"></a>GPS Setup<br>
          </h2>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          <br>
          <b>Download SAS-Planet GPS or use any favorite program.</b><br>
          <br>
          <a href="http://www.sasgis.org/download/" target="_blank">http://www.sasgis.org/download/</a><br>
          <br>
          SAS-Planet is free software with many Maps.<br>
          Minor is the city names from only Google Maps are displayed in
          Russian text.<br>
          <br>
          We can change that, goto SAS.Planet\Maps\sas.maps\Google
          folder.<br>
          Inside each map folder is a params.txt except for the
          GoogleSat folder.<br>
          <br>
          Find ru in the url link and change it into en example:
          DefURLBase=http://mt.google.com/vt/lyrs=m@169000000&amp;hl=en<br>
          Remove SAS.Planet\cache and the maps are English.<br>
          &nbsp;<br>
          <img src="img/SAS-Planet.jpg" alt="" width="929" height="545"><br>
          <br>
          <p> </p>
          <h2><a name="Get_it_all_Running_"></a>Get it all Running!<br>
          </h2>
          <br>
          Start your favorite SDR Software, <b>make sure The [MME]CABLE
            Input is selected in Audio Options.</b><br>
          <br>
          <img src="img/sound.jpg" alt="" width="226" height="158"><br>
          <br>
          Tune into the Radiosonde signal. <br>
          <br>
          <b>Start the shortcut of the Decoder.bat.</b><br>
          <br>
          <img src="img/dfm.jpg" alt="" width="677" height="380"><br>
          <br>
          <b>Start SAS-Planet</b>, goto GPS Tab and <b>Select the
            correct serial COM port</b>, Rate is always 4800 Baud.<br>
          Change device timeout to 6000 = Max.<br>
          <br>
          <img src="img/gps_com.jpg" alt="" width="678" height="558"><br>
          <br>
          Push the sat-icon and GPS should be connected and gives a
          current position of the radiosonde.<br>
          <br>
          <img src="img/sdr_all.jpg" alt="" width="1144" height="638"><br>
          <p><br>
          </p>
          <h2><a name="APRS-Map_"></a>APRS-Map<br>
          </h2>
          APRS-Map can also show the current Radiosonde and your own
          position (offcourse a GPS-Mouse is required), <a
            href="#ADB_Android_GPS_">or use your Android phone as a GPS.</a><br>
          In Offline Maps, without the need to sent data over the APRS
          Network.<br>
          <br>
          <b>Download APRS-Map for Windows:</b><br>
          <br>
          <a
            href="http://wiki.oevsv.at/index.php?title=DXL_-_APRSmap_Download"
            target="_blank">http://wiki.oevsv.at/index.php?title=DXL_-_APRSmap_Download</a><br>
          <br>
          <b>Setup GPS:</b><br>
          <br>
          Make sure you have the right COM Port number the GPS is
          connected to.<br>
          And replace this by the com1 example.<br>
          <br>
          <b>Make a gps.bat file and insert:</b><br>
          <br>
          gps2aprs.exe -t com1:4800 -I CAR -i /k -D -0 30 -b 2 -v -r
          127.0.0.1:9002<br>
          <b><br>
          </b><b> gps2aprs -h</b><br>
          <br>
          &nbsp;-t
          &lt;tty&gt;:&lt;baud&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          (com1:4800)<br>
          &nbsp;-I
          &lt;mycall&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Mycall with SSID like NOCALL-15<br>
          &nbsp;-D&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          DAO Extension on for 20cm Resolution<br>
          &nbsp;-b
          &lt;s&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Driving Beacon Time in Seconds (15)<br>
          &nbsp;-r
          &lt;x.x.x.x:destport&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use
          AXUDP (to Soundmodem)<br>
          &nbsp;-v&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Verbous-Mode<br>
          &nbsp;-i&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
          Ballon /O, Car /&gt; -i /k<br>
          <br>
          <b>Start gps.bat and NMEA data from your local GPS-Mouse
            should roll in:</b><br>
          <br>
          <img src="img/GPS2APRS.png" alt="" width="466" height="274"><br>
          <br>
          Start SDR, Decoder on the Radiosonde and APRS-Map.<br>
          <br>
          Goto Config / Rf-Ports Tab: <br>
          <br>
          <img src="img/RF-Port.png" alt="" width="703" height="369">&nbsp;&nbsp;
          <br>
          <br>
          Check RF-Port 1 and <b>make sure</b> its
          UDP1(ip:send:listen)|1|127.0.0.1:9001:9002<br>
          <br>
          It is also possible to use the NMEA output of the RS-Decoders
          and feed data into APRSMap via UDP thru the Perl pos2aprs
          script.<br>
          -U UDP Ip and Port.<br>
          -d generates APRS frames with DAO (and thus finer position
          resolution).<br>
          -i&nbsp; Sonde ID E.g. i-Met.<br>
          <br>
          <b>POS2APRS:<br>
            <br>
            Download: </b><a
            href="https://github.com/dl9rdz/RS/blob/master/tools/pos2aprs.pl?raw=true"
            target="_blank">https://github.com/dl9rdz/RS/blob/master/tools/pos2aprs.pl</a><br>
          <br>
          Example scripts RS-41 and DFM:<br>
          <br>
          sox.exe -q -t waveaudio "CABLE Output" -t wav - 2&gt;nul |
          rs41mod.exe --ecc2 --crc -vx --ptu | perl.exe pos2aprs.pl
          WIN10 0 _RS41 -d -U 127.0.0.1:9002<br>
          <br>
          sox.exe -q -t waveaudio "CABLE Output" -t wav - 2&gt;nul |
          dfm09mod.exe --ecc --ptu -v --auto | perl.exe pos2aprs.pl
          WIN10 0 _DFM09 -d -U 127.0.0.1:9002<br>
          <br>
          The Radiosonde position should be Visible and every 30 Seconds
          the CAR Position will be updated.<br>
          <br>
          <img src="img/aprsmap.jpg" alt="" width="703" height="450"><br>
          <br>
          All stuff running SDR#, RS-Decoder, APRS-Map, RadioSonde
          output and Own GPS Position plotted on the Map:<br>
          <br>
          <img src="img/aprsmap_all.jpg" alt="" width="927" height="489"><br>
          <br>
          <b>Note's:</b><br>
          <br>
          Fill in <b>a callsign</b> with optional SSID and <b>QTH
            Location</b> from the <b>Online Menu</b>.<br>
          Zoom to your QTH as far as you can 100% identify your home
          (zoom level &lt;16). <br>
          <br>
          <b>Then open</b> ONLINE - MY POSITION and point to your home.
          <br>
          While push and hold the SHIFT key click on your home. <br>
          The coordinates will be copied into the MY POSITION field,
          Just click OK to save them.<br>
          <br>
          Aprsmap has a setting that should not be used. Config, Map
          Parameter, Trackfilter - <b>please leave out!</b><br>
          <br>
          <b>Change start view:</b><br>
          <br>
          Set the target area on the map.<br>
          Then click Zoom and with the Shift key pressed, left-click on
          this button:<br>
          <br>
          <img src="img/pos.png" alt="" width="193" height="167"><br>
          <br>
          The button is then called as the level (here: 11) and is used
          as a view at program start. <br>
          This view can also be called up with the "1" key. <br>
          <br>
          In the same way, the three buttons on the right work next to
          it.<br>
          With Shift and click on the respective button the current view
          is saved, only the click (or the digit) calls up this view.<br>
          <br>
          In response to these actions, there are brief messages at the
          top left. "View stored!" after saving and "Show One Symbol
          Off" after invoking a saved view. <br>
          <p> </p>
          <p><br>
            <b>Its possible to use other map sources, open and edit
              getosm.ini and change/insert:</b><br>
          </p>
          <p>1|0|http://tile.memomaps.de/tilegen/*.png|tiles_topo2|</p>
          <p><b>For example OSM Map.</b><br>
            <br>
          </p>
          <p><b>This must be changed in aprsmap.cfg also!</b></p>
          <p>Map Names|1|tiles_topo2 0.25 25</p>
          <p>The Map listed above will be the first one to show up.<br>
            <br>
          </p>
          <p><b>Maps can be changed in Tools / Change Maps.</b><br>
          </p>
          <p>All Maps can be saved for Offline usage.<br>
            <br>
          </p>
          <p><b>Howto about the regular functions and options from
              APRS-Map read the Wiki:</b><br>
            <br>
            <a
              href="http://wiki.oevsv.at/index.php?title=DXL_-_APRSmap_englisch"
              target="_blank">http://wiki.oevsv.at/index.php?title=DXL_-_APRSmap_englisch</a><br>
          </p>
          <h2><a name="ADB_Android_USB_GPS"></a>ADB Android USB GPS<br>
          </h2>
          <br>
          <a href="#Setting_up_Virtual_">Com0com needs to be installed.</a><br>
          <br>
          <b>Add another pair of com ports, as the other com port is
            needed for RS-Decoder output.</b><br>
          <br>
          <a
            href="https://developer.android.com/studio/releases/platform-tools"
            target="_blank">Download ADB Android SDK.</a><br>
          <br>
          <b>Ensure the USB drivers for your mobile are installed on the
            PC.</b><b><br>
          </b><b> Ensure that USB debugging is enabled on the mobile
            device.</b><br>
          <br>
          <b>Download ShareGPS</b>:&nbsp; <a
href="https://play.google.com/store/apps/details?id=com.jillybunch.shareGPS&amp;hl=en"
            target="_blank">Playstore</a><a
            href="https://www.apk4fun.com/apk/2792/" target="_blank"> </a>or<a
            href="https://www.apk4fun.com/apk/2792/" target="_blank">
            APK4FUN</a><br>
          <br>
          In Share GPS, create a new connection for NMEA USB. <br>
          <b>With port 7777.</b><br>
          Connect your phone to a computer with the USB data cable.<br>
          <br>
          <a href="/adb.zip?raw=true">Download ADB.bat</a><br>
          Move the batchfile into ADB Android SDK Folder.<br>
          <br>
          Double click adb.bat<br>
          <b>Ensure ADB detects the mobile. </b><br>
          <br>
          <img src="img/ADB.png" alt="" width="617" height="346"><br>
          <br>
          <b>The mobile may need to authorize access. </b><b><br>
          </b><b> Check the phone screen.</b><br>
          You can close the adb screen.<br>
          <br>
          <b>Start the connection in Share GPS. </b><br>
          <br>
          <img src="img/ShareGPS.png" alt="" width="243" height="432"><br>
          <br>
          You should see USB listening in the status.<br>
          <br>
          <a
href="https://arundaleais.github.io/docs/ais/NmeaRouter_setup_1.3.66.exe?raw=true"
            target="_blank">Download NmeaRouter</a><br>
          <br>
          Install and select Configure/Profile/New<br>
          Name Profile Android USB<br>
          Configure/Connection/New<br>
          <br>
          <img src="img/1.png" alt="" width="289" height="254"><br>
          <br>
          Ok.<br>
          <br>
          <img src="img/2.png" alt="" width="257" height="409"><br>
          <br>
          Port: 7777 Like in ShareGPS.<br>
          <br>
          Again Configure/Connection/New<br>
          <br>
          <img src="img/3.png" alt="" width="285" height="268"><br>
          <br>
          Ok.<br>
          <br>
          <img src="img/4.png" alt="" width="245" height="203"><br>
          <br>
          Select <b>First</b> Virtual Com Port (<b>take care with the
            ones used for RS-Decoders!</b>), check Windows - Control
          Panel Devices.<br>
          <br>
          <img src="img/no_route.png" alt="" width="591" height="328"><br>
          <br>
          Now we see this, but there is not Route between our local ip
          and the com port..<br>
          <br>
          Select Configure/Route/New<br>
          <br>
          <img src="img/Route.png" alt="" width="262" height="176"><br>
          <br>
          Enable and Ok.<br>
          <br>
          <img src="img/NMEA_Router.png" alt="" width="592" height="331"><br>
          <br>
          Click Start, You also see on the phone in ShareGPS, USB
          Connected.<br>
          GPS NMEA Data Rolling in :)<br>
          <br>
          <a href="#APRS-Map_">Repeat Steps overhere but make sure to
            select second virtual com port for GPS Out!</a><br>
          <br>
          Whenever done sending NMEA data, long press the connection in
          Share GPS and select Disconnect.<br>
          Kill ADB.exe in taskmanager, Stop Nmea-Router and Exit
          APRS-Map.<br>
          <h2><a name="Android_WiFi_GPS"></a>Android WiFi GPS<br>
          </h2>
          <br>
          Com0com needs to be installed.</a><br>
          <br>
          <b>Add another pair of com ports, as the other com port is
            needed for RS-Decoder output.</b><br>
          <br>
          <b>Download Windows 7 GPS Sharing:</b>&nbsp; <a
href="https://play.google.com/store/apps/details?id=com.michaelchourdakis.windows7gpssharing&amp;hl=en"
            target="_blank">Playstore</a> or <a
href="https://apkpure.com/nl/gps-sharing-for-windows-sensor/com.michaelchourdakis.windows7gpssharing"
            target="_blank">APKPure</a><br>
          <br>
          <img src="img/Win7GPS.png" alt="" width="252" height="449"><br>
          <br>
          In Windows 7 GPS Sharing, Tap on Listing port <b>change to
            port 7777.</b><br>
          <br>
          <a
href="https://arundaleais.github.io/docs/ais/NmeaRouter_setup_1.3.66.exe?raw=true"
            target="_blank">Download NmeaRouter</a><br>
          <br>
          Install and select Configure/Profile/New<br>
          <br>
          <img src="img/1b.png" alt="" width="269" height="124"><br>
          <br>
          Name Profile Android WiFi<br>
          Configure/Connection/New<br>
          <br>
          <img src="img/1.png" alt="" width="289" height="254"><br>
          <br>
          Ok.<br>
          <br>
          <img src="img/3b.png" alt="" width="265" height="409"><br>
          <br>
          Port: 7777 and Ip adres of the Phone.<br>
          <br>
          Again Configure/Connection/New<br>
          <br>
          <img src="img/3.png" alt="" width="285" height="268"><br>
          <br>
          Ok.<br>
          <br>
          <img src="img/4.png" alt="" width="245" height="203"><br>
          <br>
          Select <b>First</b> Virtual Com Port, check Windows - Control
          Panel Devices.<br>
          <br>
          We need a route between the ip and com connection.<br>
          Select Configure/Route/New<br>
          <br>
          <img src="img/Route.png" alt="" width="262" height="176"><br>
          <br>
          Enable and Ok.<br>
          <br>
          <img src="img/5.png" alt="" width="617" height="439"><br>
          <br>
          Click Start, You also see on the phone Client Connected.<br>
          GPS NMEA Data Rolling in :)<br>
          <br>
          <a href="#APRS-Map_">Repeat Steps overhere but make sure to
            select second virtual com port for GPS Out!</a><br>
          <p> </p>
        </div>
        <div class="pagefooter">
          <p>Thanks fly out to Zilog80, Andreas6 and Auto-RX Team.</p>
  </body>
</html>
