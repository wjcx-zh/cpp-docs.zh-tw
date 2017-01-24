---
title: "assert 函式所列印的診斷 | Microsoft Docs"
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
  - "C"
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# assert 函式所列印的診斷
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.2**：**assert** 函式的診斷列印和終止行為。  
  
 **assert** 函式會列印一個診斷訊息，並在運算式為 false \(0\) 時呼叫 **abort** 常式。  診斷資訊的格式如下  
  
 **判斷提示失敗**: *expression***，檔案** *filename***，行號** *linenumber*  
  
 其中 filename 是原始程式檔的名稱，而 linenumber 是原始程式檔中發生失敗的判斷提示行號。  如果運算式為 true \(非零\)，則不會採取任何動作。  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)