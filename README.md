# Azure Private DNS Zone Rebuild
Personal Checkup on how Azure Private Zones Work and interact mostly with private DNS

# Docker Setup with Core DNS Image
Three Containers used to demonstrate OnPrem Setup or general other DNS Server which is not present in Azure or uses other Public Resolvers then Azure DNS 168.63.129.16

The Azure DNS Resolver is only accesibel over a VM or Instance in Azure VNet others cant access the DNS even over VPN.

So the Required Setup to Resolve Private DNS Zones which are used for Services / Instances in Azure like Storage Accoutns to make them internal Resolvabel over DNS (cause standard is public) you need to query the Azure DNS main Server as meantioned. To do that your DNS is required and one more endpoint in Azure (something like a Standard DNS or the Service Azure Private DNS Endpoint) and surely the Azure DNS Server.

The Issue comes in a Azure Private DNS Zones are the same url / Domain as Public Ones. So there is a kniff with are were you specifically need to add the private DNS Zones not the mother Domain to your DNS. Normaly you may add afs.azure.net and make it forwarded but with that private DNS Zones will not Resolve you specifically need to set the subdomain.afs.azure.net for hostnames to be corretly revoled to the internal A Record you set.
