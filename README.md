# VPC Lambda give Internet Accesss. (Public Access)

 ## Initial Steps
 

> **Note:**
> Its recommended to assign name "Public" to one of the Subnets. 

### Step 1

 1. Go to route tables.
 2. Name exiting table (Private) 
 3. Create new route table. (Make sure to name it Public)
	 1. Select Public table.
	 2. Select Routes tab and click **Edit Routes**.
	 3. Destination: **0.0.0.0/0** and points to: **igw-xxxx** (Internet Gateway)
	 4. Now go to **Subnets Associations** tab and click **Edit Subnets associations**.
	 5. Here add Public subnet.

### Step 2

 1. We create NAT Gateway by going to NAT Gateways tab on the left pan.
 2. Click on Create NAT Gateway.
 3. In subnet add **Public Subnet**
 4. Click on **Create new EIP**.
 5. Save.

### Step 3

 1. Go back to Routes Tables.
 2. Select Private Route Table.
 3. Select Routes tab and click **Edit Routes**.
 4. Destination: **0.0.0.0/0** and points to: **nat-xxxxx** the one you created in Step 2.
 5. Now go to **Subnets Associations** tab and click **Edit Subnets associations**.
 6. Here add all Private subnets.

### Step 4

 1. In security group linked with your lambda, in advance -> network, make sure outbound rules are to set to All and destination to 0.0.0.0/0
 2. Make sure your lambda is connected to subnets you configured.

	

