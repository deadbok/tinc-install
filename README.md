# Task

Install tinc and set up a network using host variables.

 * Install tinc
 * Set configured tinc networks to start at boot.
 * Create network configurations.
 * Generate key pairs or use existing keys
 * Create host configurations.
 * Synchronize host configurations between participants

# Dependencies

None.

# Variables

Gentoo specific configurations are in `Gentoo.yml`.

 * **tinc_service:** Name of the tinc service.
   * *Default:* "tincd"
   * *Gentoo:* "tincd"
 * **tinc_switch_net_address:** Address of the tinc network in switched mode.
   * *Default:* "192.168.3.0/24"
 * **tinc_router_net_cidr:** Netmask of the tinc network in routed mode.
   * *Default*: "32"
