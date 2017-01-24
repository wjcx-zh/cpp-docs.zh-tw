---
title: "編譯器錯誤 CS0139 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0139"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0139"
ms.assetid: 235ba3d4-566c-4ef6-801a-a338f4f2a12d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0139
沒有可中斷或繼續的封閉式迴圈  
  
 在迴圈外部遇到中斷或繼續陳述式。  
  
 如需詳細資訊，請參閱[跳躍陳述式](../Topic/Jump%20Statements%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0139 兩次：  
  
```  
// CS0139.cs namespace x { public class a { public static void Main() { continue;  // CS0139 break;     // CS0139 } } }  
```