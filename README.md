# Task

Install tinc and set up a network using host variables.

 * Install tinc
 * Set configured tinc networks to start at boot.
 * Create network configurations.
 * Generate key pairs or use existing keys
 * Create host configurations.
 * Synchronize host configurations between participants

# Dependencies

**Supported distributions and operating systems:**

 * Linux
   * Debian (Jessie, Stretch)
   * Gentoo
 * *BSD
   * FreeBSD

## Linux hosts

 * Python 2

## BSD hosts

 * Python 2

# Variables

Gentoo specific configurations are in `Gentoo.yml`.

 * `tinc_service`: Name of the tinc service.
   * *Default:* "tinc"
   * *Gentoo:* "tincd"
 * `tinc_switch_net_address_vpn_*interface*`: Address of the tinc network in switched mode.
   * *Default:* "192.168.3.0/24"
 * `tinc_router_net_cidr_vpn_*interface)*`: Netmask of the tinc network in routed mode.
   * *Default*: "32"
 * `tinc_key_bits`: Bits to use when geneating the key.
   * *Default*: "4096"
 * `tinc_conf_dir`: Where to store tinc configuration files.
   * *Default*: "/etc/tinc"
   * *Default*: "/usr/local/etc/tinc"

## Hosts

Each hosts tinc configuration is created using host variables. A configuration
for a host connecting to two tinc networks, one of them using  bridge `br0`
looks like this:

    tinc_interfaces:
      tun0:
        hostname: "laptop"
        ip4: "192.168.3.30"
        netmask4: "255.255.255.0"
        name: "vps1"
        onboot: true
        master: false
        mode: "switch"
        bridge: "br0"
      tun1:
        hostname: "laptop"
        ip4: "192.168.2.30"
        netmask4: "255.255.255.0"
        name: "cg"
        onboot: false
        master: false
        mode: "router"

 * **name:** Name of the tinc network.
 * **mode:** `switch` or `router` network mode. [See the tinc manual](https://www.tinc-vpn.org/documentation/Main-configuration-variables.html#Main-configuration-variables)
 * **master:** If set to `true`, this host used as a connection point for other hosts.
 * **bridge:** If set to the name of a bridge interface, the tinc tunnel interface is added to that bridge.
