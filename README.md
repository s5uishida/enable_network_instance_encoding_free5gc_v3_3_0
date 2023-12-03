# A Note for Enabling NetworkInstance IE Encoding for free5GC v3.3.0

---

### [Sample Configurations and Miscellaneous for Mobile Network](https://github.com/s5uishida/sample_config_misc_for_mobile_network)

---

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

The encoding of the APN shall follow the Name Syntax defined in RFC 2181 [18], RFC 1035 [19] and RFC 1123 [20].
The APN consists of one or more labels. Each label is coded as a one octet length field followed by that number of
octets coded as 8 bit ASCII characters. Following RFC 1035 [19] the labels shall consist only of the alphabetic
characters (A-Z and a-z), digits (0-9) and the hyphen (-). Following RFC 1123 [20], the label shall begin and end with
either an alphabetic character or a digit. The case of alphabetic characters is not significant. The APN is not terminated
by a length byte of zero.
```
