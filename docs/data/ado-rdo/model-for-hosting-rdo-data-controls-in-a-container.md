---
title: "將 RDO 資料控制項裝載於容器內的模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RDO RemoteData 控制項, 裝載模型"
  - "RemoteData 控制項, 裝載模型"
ms.assetid: ca598bac-9fef-40e6-b6cd-03d817e16b2e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 RDO 資料控制項裝載於容器內的模型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

容器 \(Container\) 會依照下述方式裝載 \(Host\) RDO 資料控制項：  
  
-   容器自資料控制項取得一個 IVBDSC 介面。  如果無法找到 IVBDSC，它就不是資料控制項。  
  
-   容器自資料控制項取得 **ICursor** 介面。  這些介面提供用戶端可以操作的 Cursor 物件。  
  
-   容器攔截 \(Hook\) 資料控制項的 **INotifyDBEvents** 介面。  這個介面允許容器接收來自資料控制項的告知。  容器應該支援 **INotifyDBEventsSink** 介面，才能進行此工作。  
  
 容器會依照下列方式裝載 RDO 資料繫結控制項：  
  
-   控制項可支援 **IBoundObject** 介面，而容器可支援 **IBoundObjectSite** 介面。  控制項取得了容器的 **IBoundObjectSite** 介面，而容器會取得來自控制項的 **IBoundObject** 介面。  
  
-   控制項可支援 **IPropNotifySink** 介面，並由容器攔截。  這可讓容器接收來自控制項的告知。  
  
-   如果控制項支援 **INotifyDBEventsSink**，就可在連接至資料控制項的 **INotifyDBEvents** 介面後，從 RDO 資料控制項接收告知。  
  
-   接著，控制項可自資料控制項接收指標物件 \(直接或透過容器\)。  接著，便可操作和捲動指標。  此時，已成功地繫結 RDO 資料繫結控制項。  
  
## 請參閱  
 [RDO 資料繫結](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 RDO 資料繫結](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)