---
title: "&#39;&lt;規範&gt;&#39; 在成員變數宣告中無效 | Microsoft Docs"
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
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;規範&gt;&#39; 在成員變數宣告中無效
`Dim` 陳述式包含無效的關鍵字。`Dim` 陳述式只能包含 `Friend`、`Private`、`Protected`、`Public`、`ReadOnly`、`Shadows`、`Shared` 或 `Static` 關鍵字。  
  
 如果您在程序之外宣告 `Static` 變數，也會出現這個訊息。`Static` 只能在程序層級使用。  
  
 請注意，如果您在 `Dim` 陳述式中包含有效的關鍵字，則可以選擇性地省略 `Dim` 關鍵字。  
  
 **錯誤 ID︰**BC30235  
  
### 更正這個錯誤  
  
1.  請從 `Dim` 陳述式中移除無效的關鍵字。  
  
2.  如果您在程序之外宣告了 `Static` 變數，請將此宣告移至程序內，或移除 `Static` 關鍵字。  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)