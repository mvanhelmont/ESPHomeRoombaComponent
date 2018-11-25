# Roomba Component for ESPHomeLib

A barebones wrapper to enable control of a Roomba via ESPHomeLib.
Tested with ESPHomeLib 1.9.1, and a Roomba 650 w/a Wemos D1 Mini installed.

## Setup/Use

Take a look at the example directory for a fully working example (very close to my setup).

In short:

* Add `#include "ESPHomeLibRoombaComponent.h"` under the esphomelib include.

* Add the following before `App.setup()`

  ```c++
  auto *custom_roomba = new RoombaComponent(
      "Distance",
      "Voltage",
      "Current",
      "Charge",
      "Capacity",
      "Charging",
      "Docked",
      "Cleaning",
      "On",
      "Off",
      "Dock",
      "Locate",
      "Spot Clean",
      "Roomba/command", /* command_topic */
      4,                /* BRC Pin */
      5000              /* Update Interval */
    );

  App.register_component(custom_roomba);
  App.register_sensor(custom_roomba->distance_sensor);
  App.register_sensor(custom_roomba->voltage_sensor);
  App.register_sensor(custom_roomba->current_sensor);
  App.register_sensor(custom_roomba->charge_sensor);
  App.register_sensor(custom_roomba->capacity_sensor);
  App.register_binary_sensor(custom_roomba->chargingState_sensor);
  App.register_binary_sensor(custom_roomba->dockedState_sensor);
  App.register_binary_sensor(custom_roomba->cleaningState_sensor);
  App.register_switch(custom_roomba->on_switch);
  App.register_switch(custom_roomba->off_switch);
  App.register_switch(custom_roomba->dock_switch);
  App.register_switch(custom_roomba->locate_switch);
  App.register_switch(custom_roomba->spot_switch);
  ```