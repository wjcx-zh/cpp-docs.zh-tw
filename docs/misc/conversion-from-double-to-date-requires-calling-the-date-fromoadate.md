---
title: "從 &#39;Double&#39; 轉換成 &#39;Date&#39; 需要呼叫 &#39;Date.FromOADate&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 從 &#39;Double&#39; 轉換成 &#39;Date&#39; 需要呼叫 &#39;Date.FromOADate&#39;
您嘗試將 `Date` 值轉換成 `Double` 值，若不使用 <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> 方法便無法完成。  
  
 **錯誤 ID：**BC30533  
  
### 更正這個錯誤  
  
-   請使用 <xref:System.DateTime.FromOADate%2A> 方法來轉換值。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)