# Analyzing Cloud and On-Prem network configurations with Batfish

These are the companion files to my articles about using Batfish to analyze cloud (AWS) and network configurations, available here: [Part 1](https://www.linkedin.com/pulse/analyzing-cloud-on-prem-network-configurations-batfish-mikel-maeso-fqtof/?trackingId=E7dS8q6dQfO1QQY4POdcqA%3D%3D) and [Part 2](https://www.linkedin.com/pulse/analyzing-cloud-on-prem-network-configurations-batfish-mikel-maeso-hveef/?trackingId=E7dS8q6dQfO1QQY4POdcqA%3D%3D).

# Topology

![topology](https://github.com/mmaeso/batfish-hybrid-cloud/assets/29441054/391181c7-cb45-4971-8a43-fa8cc3d5e610)

All the configuration files for this topology are contained within their respective folders; the 'hybrid-cloud-modified' folder contains the configurations with issues, while the 'hybrid-cloud-fixed' contains the corrected configuration files.

# How to use

Once you have the Batfish service deployed and pybatfish installed (on the same device/container or a different one) open a python shell and type the following:

```
from pybatfish.client.session import Session
bf = Session(host="localhost") # use the IP or FQDN where the batfish service is hosted
bf.set_network('hybrid-cloud-modified')
bf.init_snapshot('/data/batfish-hybrid-cloud/hybrid-cloud-modified','base',overwrite=True) # Adjust the path to reflect the actual path on your device
```

Once done, you can start querying the batfish service. All the questions can be found under the namespace `bf.q.`
