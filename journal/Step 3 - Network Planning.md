#Step 3 - Network Planning

As I was preparing VMs and making templates I realized I should do the network/address planning first in order to build templates which are pre-configured to point to the domain controller.
So, I saved where I was at on my template and decided to plan the network before continuing. For the context of this homelab I want to simulate a medium-sized enterprise
which incorporates network segmentation (subnetting).

The single most important aspect I keep in mind is that my network should be scalable without a single issue in the future if the organisation was to expand. Despite this being a homelab,
I want to future-proof my addressing scheme in a way that it's still simple for a medium-sized company to read and manage, but also plan for possible major expansion.

