target_sources_ifdef(CONFIG_ZMK_ANALOG_STICK app PRIVATE analog_stick.c)
target_sources_ifdef(CONFIG_ZMK_ANALOG_STICK app PRIVATE input_listener.c)
target_sources_ifdef(CONFIG_ZMK_ANALOG_STICK app PRIVATE scan_coordinator.c)

if(CONFIG_ZMK_ANALOG_STICK AND (NOT CONFIG_ZMK_SPLIT OR CONFIG_ZMK_SPLIT_ROLE_CENTRAL))
  target_sources(app PRIVATE hid_accumulator.c)
endif()

if(CONFIG_ZMK_SPLIT)
  target_sources_ifdef(CONFIG_ZMK_ANALOG_STICK app PRIVATE input_split.c)
endif()
