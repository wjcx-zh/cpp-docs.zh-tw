---
title: "編譯器警告 (層級 2) CS0472 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs0472"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cs0472"
ms.assetid: dc80e0a3-dbd3-4a81-b8bb-a59b510cd3e1
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0472
運算式的結果一律會是 'value1'，因為類型 'value2' 的值絕對不會等於類型 'value3' 的 'null'  
  
 編譯器應該會警告您是否搭配使用運算子與常數 Null 值。  
  
## 範例  
 下列範例會產生 CS0472。  
  
```  
public class Test { public static int Main() { int i = 5; int counter = 0; // Comparison: if (i == null)  // CS0472 // To resolve, use a valid value for i. counter++; return counter; } }  
```