---
title: "編譯器錯誤 CS0126 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0126"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0126"
ms.assetid: 15fb0f38-ac9d-4c09-a69f-398a4903d790
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0126
需要可轉換為 'type' 類型的物件  
  
 有 return 陳述式存在，但此陳述式未傳回預期類型的值。 如需詳細資訊，請參閱[屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0126：  
  
```  
// CS0126.cs public class a { public int i { set { } get { return;   // CS0126, specify a value to return } } }  
```