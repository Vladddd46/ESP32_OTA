<h1>Remote update firmware on esp32. (OTA - over the air update)</h1>
<h2>esp-idf version: ESP-IDF v4.3-dev-1521-g0289d1cc8-dirty</h2>
<br>
<p>NOTE: OTA functionality is described in main/check_firmware_updates_task.c. Other code is used to connect esp32 to wifi, which is not the topic of this issue.
https://github.com/Vladddd46/esp32_WIFI/creative describes how to connect esp32 with wifi.</p>


<p>In order to set OTA on esp32 you need to do the following steps:</p>
<ul>
	<li> Integrate code from main/check_firmware_updates_task.c in your code. check_firmware_updates_task should be separate task, which periodically checks. if any firmware update is available.
	</li>
	<li>CMakeLists.txt: add <b>json</b> component in REQUIRES and add <b>EMBED_TXTFILES ../server_certs/ca_cert.pem</b> in idf_component_register command</li>
	<li>Create two partrition tables for ota1 and ota2. It can be done in menuconfig(idf.py menuconfig) -> Partrition tables</li>
	<li>Create server_certs folder and paste server certificate in it. ca_cert.pem - file with certificate must have this name.</li>
	<li>Create main/component.mk file with line 'COMPONENT_EMBED_TXTFILES :=  ../server_certs/ca_cert.pem'</li>
</ul>


<p>In main/check_firmware_updates_task.c there is define UPDATE_JSON_URL. It is link to json file with the following format: 
<b>{
    "version": 0.2,
    "file": "https://www.some_domain.com/firmwares/2.0.bin"
}</b>
check_firmware_updates_task periodically downloads this json file, parse it, check version with version of firmware on esp32. If versions differ, downloads new firmware by link, contained in "file" key.
</p>


