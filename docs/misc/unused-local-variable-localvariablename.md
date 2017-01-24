---
title: "未使用的區域變數：&#39;&lt;區域變數名稱&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未使用的區域變數：&#39;&lt;區域變數名稱&gt;&#39;
已宣告程序中的本機變數，但從未使用過。  
  
 一個可能的原因是，程序中的區域變數拼字錯誤。 如果這個變數實際上用於另一個陳述式，但拼法不同，對編譯器而言就是兩個不同的變數。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤識別碼：**BC42024  
  
### 更正這個錯誤  
  
1.  檢查程序內的區域變數是否拼字錯誤。 請注意，不區分大小寫。 名稱 `ABC` 和 `abc` 視為參考相同的變數。  
  
2.  如果拼字沒有錯誤，請移除這個變數的宣告，或在程序中的另一個陳述式中使用它。  
  
## 請參閱  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)