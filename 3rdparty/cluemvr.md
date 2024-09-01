---
id: cluemvr
title: ClueMVR
---

ClueMVR is a third party used for getting driver related information like violation counts, primary driver details ,etc.Likewise other APIs, it is also being called via our pre-hook using hookSchema file with ``ClueMvrCall`` added in the actions array.Basically the Clue report is generated for all the drivers while the MVR runs only for the primary driver.