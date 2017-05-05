<h2>AWS Basics</h2>

<h4> AWS Infrastructure design best practices </h4>

**High availability**: Refers to systems that are durable and likely to operate continuously without failure for long periods of time. For a CSA this means making sure your application in AWS is always available when a customer/user tries to access.

**Scalability**: The ability for a cloud infrastructure to easily increase in size and capacity in a cost effective way based on usage demand. 

**Elasticity**: The ability for a cloud infrastructure to increase and decrease in size based on usage demand. In Cloud, this refers to the ability of an application to increase and decrease server capacity on demand.

**Fault Tolerance**: Fault tolerance is the property that enables a system to continue operating properly in the event of the failure of (or one or more faults within) some of its components. On AWS this is implemented by replacing faulty instances with new ones automatically.

---

<h4> Common services </h4>

**Amazon S3:** Common usage: Mass storage - Long-term storage

**Amazon RDS:** Common usage: Customer account info - Inventory catalog

**Amazon EC2:** Common usage: Web hosting - Services - Processing

---

<h4> AWS Physical Distribution </h4>

***Edge Locations:*** 
- AWS datacenter which  does not contain/provide AWS services. It is used to deliver content to the internet and other AWS regions.
- An example would be **CloudFront** which is a CDN (Content delivery network).

***AWS Regions:*** 
- AWS is made up of regions, which are groupings of independently separated data centers in a specific geographic regions known as "Availability Zones". 
- This allow for specific world regulations and better latency on specific region services. 
- When viewing a region in the AWS console you will only view resources in one region at a time but they will be across all As within that region.
- Some AWS services work "globally" and not within specific regions. For example, users created in IAM will work across all regions.


***AWS Availability Zones:*** 
- Availability zones work together in a region to make up a collection of your AWS resources.
- Properly designed applications will utilize multiple AZs for fault tolerance and failover.
- AZs have direct low latency connections between each AZ in a region but each AZ is isolated from other AZs to ensure fault tolerance.
