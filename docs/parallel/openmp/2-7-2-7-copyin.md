---
title: "2.7.2.7 copyin | Microsoft Docs"
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
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.7 copyin
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Copyin** 子句提供一個機制，來指派相同的值，以 **threadprivate** 每個執行緒在執行平行區域小組中的變數。  每個變數中所指定 **copyin** 子句中，小組的主執行緒中變數的值就會複製，好像是由指派\] 中，執行緒私用複本在平行區域的開頭。  語法 **copyin** 子句是，如下所示：  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 若要限制 **copyin** 子句如下：  
  
-   變數中所指定 **copyin** 子句必須具有可存取的、 模稜兩可的複製設定運算子。  
  
-   變數中所指定 **copyin** 子句必須是 **threadprivate** 變數。