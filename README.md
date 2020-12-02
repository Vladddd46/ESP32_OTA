<h1>Remote update firmware on esp32. (OTA - over the air update)</h1>
<h2>esp-idf version: ESP-IDF v4.3-dev-1521-g0289d1cc8-dirty</h2>
<br>
<p>NOTE: OTA functionality is described in main/check_firmware_updates_task.c. Other code is used to connect esp32 to wifi, which is not the topic of this issue.
https://github.com/Vladddd46/esp32_WIFI/creative describes how to connect esp32 with wifi.</p>


<p>In order to set OTA on esp32 you need to do the following steps:</p>
<li>
	<ul>Integrate code from main/check_firmware_updates_task.c in your code. check_firmware_updates_task should be separate task, which periodically checks. if any firmware update is available.</ul>
</li>