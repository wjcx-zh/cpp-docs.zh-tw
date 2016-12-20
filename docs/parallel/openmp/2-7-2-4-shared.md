---
title: "2.7.2.4 shared | Microsoft Docs"
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
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.4 shared
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個子句會共用變數，會出現在*變數清單*在小組中的所有執行緒之間。  團隊內的所有執行緒都存取相同的儲存區的**共用**變數。  
  
 語法**共用**子句是，如下所示：  
  
```  
shared(variable-list)  
```