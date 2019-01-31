
## [1.6] - 2019-01-31

### Changed

- ESPA 4.4.4 driver 
    -   Master mode
    -   Adding parameter "inactivityTimeout" for the gateway. If no communication during this interval, the gateway will restart (master/slave mode).

### Fixed

- Logic module 
    - AddressListener emit undefined value: https://github.com/ptorrent/webleIoTGateway/issues/5
- Remote Gateway 
    - No changing local value if remote value is undefined : https://github.com/ptorrent/webleIoTGateway/issues/2 
- Modbus driver
    - Solve some flushing issue

## [1.5] - 2019-25-01

### First commit !
