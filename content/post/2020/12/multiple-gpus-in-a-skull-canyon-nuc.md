+++
date = "2020-12-19T12:00:00-00:00"
title = "Multiple GPUs in a Skull Canyon NUC"
slug = "2020/12/multiple-gpus-in-a-skull-canyon-nuc"
author = "Alan Pope"
tags = ['hardware', 'thinkpad', 'intel', 'amd', 'nvidia', 'ubuntu']
+++

*This article previously appeared on [listed.to](https://listed.to/@popey/17478/multiple-gpus-in-a-skull-canyon-nuc). I've moved it here to consolidate my blogging*

Every 3 years at Canonical we get a laptop refresh fund. With it we can buy whatever devices we need to work. I used my last one to buy a [ThinkPad T450](https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_T450/ThinkPad_T450_Spec.PDF). The most recent one arrived in November this year. I was considering replacing the ThinkPad with a desktop computer of some kind. I can certainly keep the T450 for portable work, but I mostly sit at the same desk all day, so figure I may as well get a desktop rather than a laptop.

I recently mentioned to my friend and colleague - [Martin Wimpress](https://twitter.com/m_wimpress), that my ThinkPad T450 was becoming a bit long in the tooth. There's a Linux Kernel bug somewhere which causes the GPU to lock up randomly when driving 3 displays (internal + two external monitors) which is annoying when you are trying to work on it. It's also struggling to cope when doing a bit of heavy video work - such as having multi-party video meetings, while other things are happening. I appreciate this is quite the 'first world problem', complaining about running three displays. 

On hearing this Martin told me he had a "spare" desktop I could use, as it's sat gathering dust at his place. Once he explained the specs and what I'd be borrowing, I jumped at it. So now I'm typing this blog post on an [Intel Skull Canyon NUC](https://geni.us/UWWjh). It's a bit nice! I've never used a computer with an illuminated skull on the lid before :D

The interesting thing about this computer is it features a combined Intel CPU/GPU and AMD GPU on one board. The Intel [i7-8809G](https://ark.intel.com/content/www/us/en/ark/products/130409/intel-core-i7-8809g-processor-with-radeon-rx-vega-m-gh-graphics-8m-cache-up-to-4-20-ghz.html) sports a 4-core 8-thread 3.1GHz main CPU and HD Graphics 630 on-board GPU. However, it's bundled with a discrete AMD Radeon RX Vega GPU too! 

What's even more neat is the NUC has a ThunderBolt port which means I can attach an external GPU should I wish. I wish, so I have. The only GPU I had kicking around was an [nVidia GeForce GTX 960](https://geni.us/TT80) (a hand-me-down from another PC which was recently upgraded to an [nVidia 1050Ti](https://geni.us/i0Ylyv)).

So now this computer technically has 3 GPUs, Intel, AMD and nVidia.
```
alan@robot:~$ sudo lshw -C display
⋮
description: VGA compatible controller
product: Polaris 22 XT [Radeon RX Vega M GH]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
⋮
description: Display controller
product: HD Graphics 630
vendor: Intel Corporation
⋮
description: VGA compatible controller
product: GM206 [GeForce GTX 960]
vendor: NVIDIA Corporation
```
Cats and dogs living together!

Bit weird, not gonna lie.

I haven't fully exercised these capabilities yet. I did one quick test to see if I could use [OBS](https://snapcraft.io/obs-studio) to live-stream a window being displayed with the AMD GPU, but with the stream encoding done via nvenc on the nVidia GPU. That seems to work well. What a time to be alive! 

Thanks Martin, you're not getting this back. :D