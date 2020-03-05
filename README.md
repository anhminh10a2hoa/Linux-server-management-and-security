# Linux Server Management and Security

## Configuring Linux in the Enterprise

### Networking in Linux

You need to install CentOS (It's the binary equivalent of Red Hat and runs great for servers in the enterprise)

## Securing Linux in the Enterprise

1. SELinux

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
