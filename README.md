# Linux Server Management and Security

## Configuring Linux in the Enterprise

### Networking in Linux

You need to install CentOS (It's the binary equivalent of Red Hat and runs great for servers in the enterprise)

## Securing Linux in the Enterprise

1.  SELinux

    - Problems with DAC

      - Administrates cannot control every user
      - File permissions and ACLs cant protect against everything
      - Processes can change permissions and other security properties
      - Compromised software may have access to other parts of the system

    - What is SELinux

      - Stands for Security-Enhanced Linux
      - Originally developed by the NSA to show the value of Mandatory Access Control
      - Build into Linux kernel as of kernel 2.6
      - Primarily used in Redhat and related distributions - Fedora, CentOS and Scientific Linux

    - SELinux breakdown

      - Deny by default
      - Log everything
      - Only allow expections one at the time

    - SELinux modes

      - Enforcing - Default mode which will enforce the SELinux security policy on the system
      - Permissive - SELinux is enabled, but does not enforce. Also logs. Good for troubleshooting
      - Disabled - SELinux is disabled. Never use this

    - Types of enforcement

      - Type enforcement - Primary control which uses the "targeted" policy
      - Role-based access control - Enforcement based on a users role
      - Multi-level security-used in the "targeted" policy, but generally hidden and not often used
      - Multi-category security - extension of multi-level

    - Features and benefits

      - Policies are separate from enforcement
      - Greate logging
      - Controls much of the OS such as files, processes, network, process execution

2.  Linux Security

    - Is linux secure?

      - Linux can be configured in a way that is as secure as every other OS out there
      - NO COMPUTER OR OS IS COMPLETED SECURED
      - Linux can be configured nearly and which way you want it to be configured
      - This also provided pitfalls if we provide secure measures incorrectly

    - Benefits of Linux for scurity

      - Most software on Linux is open source - so you have communites of developers helping to secure it
      - The Linux kernel itself is relatively secure
      - Software usually has less privileges
      - Size is smaller, so software, not kernel is sought after

    - How Linux may be compromised

      - Software vulnerabilities
      - Configurations errors
      - Social engineering or users in general
      - Rootkits, Viruses and Trojans

3.  Software firewall in Linux

    - Get the status of UFW

    ```
    ufw status
    ```

    - Enable firewall

    ```
    ufw enable
    ```

    - Look at some of rules

    ```
    ufw status verbose
    ```

    - Look at the rules has already created

    ```
    ufw status raw
    ```

    - If you want to allow certain services

    ```
    ufw allow [service]/[protocol]
    ```

    - For example

      - Allow ssh service

      ```
      ufw allow ssh
      ```

      - Allow dns with udp protocol

      ```
      ufw allow 53/udp
      ```

      - Allow address and prot

      ```
      ufw allow from 192.168.18.131 to any port 22
      ```

    - If you want to allow certain services

    ```
    ufw deny [service]/[protocol]
    ```

    - For example

      - Deny port 80

      ```
      ufw deny 80
      ```

    - Show all your rules

    ```
    ufw show numbered
    ```

    - Show the firewall status in CentOS

    ```
    firewall-cmd --state
    ```

    - List of zones

    ```
    firewall-cmd --get-zones
    ```

    - List of services

    ```
    firewall-cmd --get-services
    ```

    - If I want to add web server

    ```
    firewall-cmd --zone=public --add-server=http
    ```

4.  Linux services

    - Show all services we have in startup

    ```
    chkconfig
    ```

    - See what services is running and loading in the kernel

    ```
    systemctl
    ```

    - Show all of informations of service

    ```
    systemctl status [service]
    ```

    - Disable or Enable service

    ```
    systemctl disable/enable [service]
    ```

    - After disable, service is still processing

    ```
    pkill [service]
    ```

    - Find all services is running on root or group root

    ```
    find / \( -perm -4000 -o -perm -2000 \) -print
    ```

    - If you want to change mod of any service, I use this command

    ```
    chmod -s [location of service]
    ```

    - For example

    ```
    chmod -s /usr/sbin/locate
    ```
