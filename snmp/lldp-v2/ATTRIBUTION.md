<!-- markdownlint-disable-file MD013 MD034 MD043 -->

# LLDP-V2 PAN-OS test data attribution

Source: https://github.com/librenms/librenms
License: GPL-3.0-or-later
Reference commit: `9698538cbd16b5e9689805161c3c220091788efc`

The fixture `librenms-panos-vsys.snmprec` is a reduced subset derived from:

- `tests/snmpsim/panos_vsys.snmprec`, lines 2612-2622 at the reference commit

Subset criteria:

- LLDP-V2 remote-system table OIDs (`1.3.111.2.802.1.1.13.1.4.1.1.*`)

The stored fixture preserves the upstream OIDs, SNMP type codes, and instance indexes needed to prove the PAN-OS
LLDP-V2 table shape. Device identifiers, descriptions, and addresses were replaced with documentation-safe values.

The fixture is used by build-tagged SNMP profile-resolution, collection, and topology-consumption tests. It is not
installed or packaged in Netdata release artifacts.
