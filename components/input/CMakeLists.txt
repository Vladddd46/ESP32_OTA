idf_component_register(SRCS "get_input_from_uart.c" "execute.c" "user_input.c"
                    INCLUDE_DIRS "."
                    REQUIRES libmx utils http_commands connect_to_wifi)