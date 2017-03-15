---
title: "編譯器錯誤 C2111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2111"
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2111
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\+': 指標的加法必須要使用整數運算元  
  
 嘗試使用加號 \(`+`\) 運算子將非整數值加入指標。  
  
 下列範例會產生 C2111：  
  
```  
// C2111.cpp int main() { int *a = 0, *pa = 0, b = 0; double d = 0.00; a = pa + d;   // C2111 a = pa + b;   // OK }  
```