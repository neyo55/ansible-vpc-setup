### **1. First Play: Create Infrastructure (VPC, Internet Gateway, Subnet, Route Table, Security Group, EC2 Instance)**

#### Tasks:

1. **Create VPC:**
   - Creates a new VPC with the name "neyo-vpc," CIDR block "10.0.0.0/16," in the "eu-west-1" region.
   - Registers the result in the variable `vpc_good`.

2. **Debug VPC Information:**
   - Prints debug information about the created VPC.

3. **Create Internet Gateway:**
   - Creates an Internet Gateway and associates it with the VPC created in the previous step.
   - Registers the result in the variable `igw_good`.

4. **Create Subnet:**
   - Creates a subnet within the VPC with CIDR block "10.0.1.0/24."
   - Registers the result in the variable `subnet_good`.

5. **Set Up Public Subnet Route Table:**
   - Creates a route table for the VPC and associates it with the public subnet.
   - Adds a default route pointing to the Internet Gateway.
   - Registers the result in the variable `route_table_good`.

6. **Create Security Group:**
   - Creates a security group named "my-security-group" with rules allowing SSH, HTTP, and ICMP traffic.
   - Registers the result in the variable `security_group_good`.

7. **Check if Private Key File Exists:**
   - Checks if the private key file "./aws.neyo-test-key.pem" exists.

8. **Create EC2 Keypair:**
   - Creates an EC2 key pair named "neyo-test-key" in the "eu-west-1" region.
   - Registers the result in the variable `ec2_key_result`.

9. **Save Private Key:**
   - Copies the private key from the key pair result to the file "./aws.neyo-test-key.pem" if it doesn't exist.

10. **Start EC2 Instance:**
    - Launches an EC2 instance named "public-compute-instance" in the public subnet.
    - Associates the key pair, security group, and assigns a public IP address.
    - Registers the result in the variable `ec2_instance`.

11. **Display Public IP:**
    - Prints the public IP address of the launched EC2 instance.

12. **Create Inventory File:**
    - Checks if the inventory file "./inventory.ini" exists.

13. **Remove Existing Block in Inventory:**
    - Removes existing entries for the host "my_ec2_instance" in the inventory file using the `sed` command.

14. **Add Host to Inventory:**
    - Adds the EC2 instance as a host in the inventory file.

15. **Update Inventory File:**
    - Updates the inventory file with the public IP address of the EC2 instance.

16. **Wait for SSH to Become Available:**
    - Waits for the SSH port (22) on the EC2 instance to become available.

### **2. Second Play: Configure EC2 Instance (Install Nginx)**

#### Tasks:

1. **Update Package Cache:**
   - Updates the package cache on the EC2 instance.

2. **Install Nginx:**
   - Installs the Nginx web server on the EC2 instance.

3. **Start Nginx Service:**
   - Starts the Nginx service on the EC2 instance.

### **Notes:**
- The playbooks are designed to create a VPC with a public subnet, launch an EC2 instance in that subnet, and then configure the instance by installing Nginx.
- The second play targets the EC2 instance created in the first play using the `my_ec2_instance` host.
- The private key file is checked, and if it doesn't exist, a new EC2 key pair is created and saved.
- The inventory file is also created when the first playbook is ran and it is also updated with the EC2 instance's public IP address with the instance default user (ubuntu), because the instance is running ubuntu OS.

Overall, this playbook automates the creation of infrastructure and the configuration of an EC2 instance. If you have specific questions about any part of the playbook or need further clarification, feel free to message me kbneyo55@gmail.com