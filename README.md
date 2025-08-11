Role Name
=========

Configures a pf firewall by allowing the user to specify macro definitions, ingress and egress rules.

Requirements
------------

None

Role Variables
--------------


#sThis will be the groupname expressed for the NIC ina /etc/rc.conf.  This must have a group name
# for the firewall configuration to work. (See man ifconfig and look for group
firewall_pf_int_groupname:


# must have a value, controls access from basic ingress rules
# should be for instance for a 10.0.0.0/24 network be set to 10.0.0.0/24
firewall_pf_mynetwork:

# used to control base ingress traffic
firewall_pf_myhostip:

# For the firewall_pf_tcp/udp_svcs_in/out variables see example below in how to express them.
# Must lead with a comma because there will be existing services preceeding the contents of
# these variables
#
# Ex. firewall_pf_tcp_svc_in: ",httpd,httpd"

# services in for TCP
firewall_pf_tcp_svcs_in:

firewall_pf_udp_svcs_in:

# services out for TCP:
firewall_pf_tcp_svcs_out:

# services out for UDP
firewall_pf_udp_svcs_out:


# here's an example of how to express a macro
#
#Ex.
#
#firewall_pf_macros:
#  - macro: "office_printer=10.0.0.100"
#  - macro: 'office_prtr_tcp="{ jetdirect, printer }"'


# macro definitions go here
firewall_pf_macros:
  - macro: 


# if true this will controll opening firewall to printers
# firewall_pf_printer_ingress_rules and firewall_pf_egress_rules must be setup
firewall_pf_enable_printers: false

# macro definition for the printers IPv4 addresses  
firewall_pf_printers_ipv4_macro:


# Here's how to express an ingress rule for a printer continueing from
# the example above in the macro example
#
# Ex.
#
#firewall_pf_ingress_rules:
#  - rule: "pass in log proto tcp from $office_prtr port $office_prtr_tcp keep state"

# ingress rules here
firewall_pf_ingress_rules:
  - rule: additional ingress rule

# egress rules here
firewall_pf_egress_rules:
  - rule: additional egress rule


# list printer ingress firewall rule
firewall_pf_printer_ingress_rules:
  - rule:

# list printer egress firewall rule
firewall_pf_printer_egress_rules:
  - rule:

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - name: freebsd-pf-firewall

License
-------

BSD

Author Information
------------------



