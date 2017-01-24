---
title: "編譯器錯誤 C3360 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3360"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3360"
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3360
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'string': 無法建立名稱  
  
 傳遞給 [uuid](../../windows/uuid-cpp-attributes.md) 屬性的值無效。  
  
 下列範例會產生 C3360：  
  
```  
// C3360.cpp [ uuid("1") ] // try this line instead // [ uuid("12341234-1234-1234-1234-123412341234") ] struct A   // C3360 { }; int main() { }  
```