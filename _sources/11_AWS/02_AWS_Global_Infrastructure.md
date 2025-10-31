# AWS Global Infrastructure

- As we know, AWS provides services all around the world. It provides services all over the world through AWS Regions.

- **AWS Regions** : AWS has regions all over the world. The names of the regions could be us-east-1, eu-west-3, .. etc. A region is the group of data centers. Most AWS services are region-scoped. But we need to keep some things in mind while selecting a region.

  **1) Compliance with data governance and legal requirements** : Generally some countries make some rules that their data must remain their country itself and they doesn't want to share thier to other countries. In this cases, we need to select the region within our country itself.

  **2) Proximity to customers** : If we have more customers in one country then we need to select a region in that country itself which reduces latency issues to our application.

  **3) Available Services within the Region** : Generally all services are not available in all regions. So we need to choose a region, so that it has all services required for our application.

  **4) Pricing** : Generally pricing of the services varies from region to region. So we consider the prices of services required for our application in a region while selecting the region.

- **AWS Availabilty Zones** : Each region has many availabilty zones (such as 3 i,e min 3 or max 6). Some of the avaliabilty zones are ap-south-east-2a, ap-south-east-2b, ap-south-east-2c etc. Each availabity zones has one or more discrete data centers with redundant power, networking, and connectivity. They are seperate from each other which are isolated from disasters. But they are connected with high bandwidth and ultra low latency networking.

- **AWS Points of Presence** : AWS has Points of Presence (PoP) which is called Edge Locations that is strategically placed data center or network facility that caches and delivers content closer to end users by optimizing performance and reducing latency for AWS services. Generally these AWS uses these Edge locations to cache frequently accessed content for its content delivery network (CDNs). When an user requests content like an image or video, that request is gets routed to the nearest edge location. If the content is already cached there, then it is served directly to user with at much lower latency than fetching it from regional data center. Beyond caching, edge locations also hosts small number of services that require ultra-low latency including AWS Route 53, AWS Global Accelerator etc.

- AWS has 400+ Points of Presence (400+ Edge locations and 10 Regional Caches) in 90+ cites accross 40+ countries.

- Most of the services in the AWS are region specific but some services are global which means if you select a service i.e is global then your region looks as global in AWS Console, other wise you would see the region that you have choosen.