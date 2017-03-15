---
title: "no_dual_interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_dual_interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_dual_interfaces 屬性"
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# no_dual_interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 變更編譯器產生雙重介面方法之包裝函式的方式。  
  
## 語法  
  
```  
no_dual_interfaces  
```  
  
## 備註  
 一般而言，包裝函式將會透過介面的虛擬函式表呼叫方法。  若使用 `no_dual_interfaces`，包裝函式就會改為呼叫 **IDispatch::Invoke** 來叫用方法。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)