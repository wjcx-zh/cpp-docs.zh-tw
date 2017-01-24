---
title: "編譯器錯誤 CS0031 | Microsoft Docs"
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
  - "CS0031"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0031"
ms.assetid: 91f11ae9-9143-41f4-8002-5c38c8ee0651
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0031
無法將常數值 'value' 轉換為 'type' \(請使用 'unchecked' 語法覆寫\)。  
  
 嘗試將值指派給其類型無法儲存值的變數。 如需詳細資訊，請參閱[類型](../Topic/Types%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會在已核對及未核對的內容中產生 CS0031：  
  
```  
// CS0031.cs namespace CS0031 { public class a { public static void Main() { int num = (int)2147483648M; //CS0031 // Try using a larger numeric type instead: // long num = (long)2147483648M; //CS0031 const decimal d = -10M; // Decimal literal unchecked { const byte b = (byte)d; // CS0031 // For small values try using a signed byte instead: // const sbyte b = (sbyte)d; } } } }  
```  
  
## 請參閱  
 [unchecked](../Topic/unchecked%20\(C%23%20Reference\).md)