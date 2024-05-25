### NTT
---

This document demonstrates my knowledge of making small buisness networks.

---

Stage 0

![Stage 0](https://github.com/tetsunoheishi/NTT/assets/170445180/cb2b4445-2f55-4a58-bcb0-bb46317ce7e8)

This is the starting topology. It represents the network before implementing firewalls and switches.

---

Stage 1

This shows the implimentation of a firewall, LAN switch, DMZ switch and a Windows Desktop in the network.

![Stage 1 Starting](https://github.com/tetsunoheishi/NTT/assets/170445180/aeb9d3b1-40e9-45cc-84a5-df6873d3b2b1)

Here I implimented commands to configure the firewall to the LAN switch through the gateway 10.128.0.1/24.

![gns3-ntt-lab-stage1-instructions-config-lan-network-fw2](https://github.com/tetsunoheishi/NTT/assets/170445180/706bac8d-2cf6-4eb9-948c-2fee208d329a)

I then verified the configuration.

![gns3-ntt-lab-stage1-instructions-config-lan-network-fw3](https://github.com/tetsunoheishi/NTT/assets/170445180/f99516b5-4799-4dd5-baef-2cafd3d29ef8)

I then configured the DHCP server for the LAN interface using these command prompts.

![gns3-ntt-lab-stage1-instructions-config-lan-network-fw4](https://github.com/tetsunoheishi/NTT/assets/170445180/341ea206-0ace-4849-a7d9-af27cadf9a61)

I verified the configuration here.

![gns3-ntt-lab-stage1-instructions-config-lan-network-fw5](https://github.com/tetsunoheishi/NTT/assets/170445180/9bd72b67-6720-4482-8033-47b1d3e2b20f)

I then set up the network for the Wndows 10 Desktop using the DHCP addresses from the LAN network

![gns3-ntt-lab-stage1-instructions-add-win10-1](https://github.com/tetsunoheishi/NTT/assets/170445180/2dc3a9fe-0cc8-4503-aaad-7a6e48b0aaac)

I then pinged the LAN, WAN, and DNS connections to verify.

![gns3-ntt-lab-stage1-instructions-add-win10-2](https://github.com/tetsunoheishi/NTT/assets/170445180/dcd8bbfc-ab1b-4dfa-8976-14857e83aa92)

After verifying connections I went into the windows desktop and accesses the firewall GUI from http://10.128.0.1/

![gns3-ntt-lab-stage1-instructions-fw-gui2](https://github.com/tetsunoheishi/NTT/assets/170445180/8f78d88c-cb89-4e86-ba03-4a8f214f5dd5)

I then made system changes to enable LAN and DMZ devices to sync time with the firewall using the following promtps in the system settings

hostname = firewall
  timezone = GMT -6:00 Central Time (US & Canada)
  setup device as local NTP server = enabled
      list on interfaces = port2, port4
  idle timeout = 60
  auto file system check = enabled

  I then backed all configurations in case something went wrong and I need to revert back to a previous stage and rebooted.

  After the reboot I configured network interfaces according to the clients requests : 
    10.128.0.0/24 as the LAN network,
    10.128.99.0/24 as the GUEST network, and
    10.128.10.0/24 as the DMZ network

I then created 4 seperate ports.

![image](https://github.com/tetsunoheishi/NTT/assets/170445180/f78a204a-c4a6-4bfb-b506-4efdfc12b458)
