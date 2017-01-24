---
title: "無法寫入記錄檔，因為如果寫入，可用磁碟空間會減少到 ReservedSpace 值以下 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ReservedSpaceEncroached"
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法寫入記錄檔，因為如果寫入，可用磁碟空間會減少到 ReservedSpace 值以下
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別無法寫入記錄檔，因為：  
  
-   可用磁碟空間數量 \(以位元組為單位\) 小於 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> 屬性的值  
  
     —且—  
  
-   <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性的值是 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>。  
  
### 更正這個錯誤  
  
1.  封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。  
  
2.  將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> 屬性的值變更為較小的數字，以保留較少的磁碟空間。  
  
3.  將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>，以在可用磁碟空間不足時，捨棄訊息而不發出警告。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log 物件](../Topic/My.Application.Log%20Object.md)   
 [My.Log Object](../Topic/My.Log%20Object.md)