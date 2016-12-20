---
title: "要將 &#39;Date&#39; 轉換成 &#39;Double&#39; 需要呼叫 &#39;Date.ToOADate&#39; 方法 | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 要將 &#39;Date&#39; 轉換成 &#39;Double&#39; 需要呼叫 &#39;Date.ToOADate&#39; 方法
您嘗試將 `Date` 值轉換成 `Double` 值，若不使用 <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> 方法便無法完成。  
  
 **錯誤 ID︰**BC30532  
  
### 更正這個錯誤  
  
-   請使用 <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> 方法來轉換值。  
  
## 請參閱  
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)