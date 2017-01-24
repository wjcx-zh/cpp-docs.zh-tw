---
title: "編譯器錯誤 CS0221 | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0221
無法將常數值 'value' 轉換為 'type' 類型 \(可使用 'unchecked' 語法修正\)  
  
 [checked](../Topic/checked%20\(C%23%20Reference\).md) \(預設為開啟\) 偵測到會導致資料遺失的指派作業。 請更正指派，或使用 [unchecked](../Topic/unchecked%20\(C%23%20Reference\).md) 來解決這個錯誤。 如需詳細資訊，請參閱[Checked 與 Unchecked](../Topic/Checked%20and%20Unchecked%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0221：  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```