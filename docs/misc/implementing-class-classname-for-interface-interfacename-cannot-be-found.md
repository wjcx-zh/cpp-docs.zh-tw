---
title: "找不到介面 &lt;介面名稱&gt; 的實作類別 &#39;&lt;類別名稱&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31094"
  - "bc31094"
helpviewer_keywords: 
  - "BC31094"
ms.assetid: 262cb67e-2930-4a4a-a63e-bb2e201b3b93
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 找不到介面 &lt;介面名稱&gt; 的實作類別 &#39;&lt;類別名稱&gt;&#39;
無法使用 Interop 組件中的實作類別。  
  
 **錯誤 ID︰**BC31094  
  
### 更正這個錯誤  
  
1.  確認 COM 物件的類型程式庫有效。  
  
2.  使用類型程式庫匯入工具 \(Tlbimp.exe\) 手動建立 Interop 組件，然後從專案中加入該 Interop 組件的參考。  
  
## 請參閱  
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)