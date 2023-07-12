# A Note for Enabling NetworkInstance IE Encoding for free5GC v3.3.0

For free5GC v3.3.0, `Network Instance IE` of `PFCP Session Establishment Request` sent from SMF to UPF is not encoded by default.
In this case, `PFCP Session Establishment` may fail between free5GC SMF and other UPF.
Therefore, by adding the following line in the free5GC SMF configuration file `smfcfg.yaml`, the Network Instance IE of `PFCP Session Establishment Request` can be encoded and sent to the UPF.

- `smfcfg.yaml`
```yaml
configuration:
  ...
  nwInstFqdnEncoding: true <--
  ...
```
For this, please refer to the followings of 3GPP specifications.
```
3GPP TS 29.244 Interface between the Control Plane and the User Plane nodes
- 8 Information Elements
  - 8.2 Information Elements
    - 8.2.4 Network Instance

3GPP TS 23.003 Numbering, addressing and identification
- 9A Definition of Data Network Name
  - 9.1 Structure of APN
```
