idf_component_register(SRCS "main.c" "check_firmware_updates_task.c"
                    INCLUDE_DIRS "." 
                    REQUIRES  libmx "esp_adc_cal" nvs_flash utils 
                    http_commands esp-tls connect_to_wifi input wifi_module esp_http_server my_http_server esp_https_ota esp_http_client json
                    EMBED_TXTFILES ../server_certs/ca_cert.pem)