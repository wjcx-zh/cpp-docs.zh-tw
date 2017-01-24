---
title: "NMAKE 嚴重錯誤 U1070 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1070"
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

於巨集定義 'macroname' 中產生循環  
  
 給定的巨集定義中包含巨集，此巨集的定義中又包含給定的巨集。  循環的巨集定義是無效的。  
  
## 範例  
 下列巨集定義  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 會造成下列錯誤：  
  
```  
cycle in macro definition 'TWO'  
```