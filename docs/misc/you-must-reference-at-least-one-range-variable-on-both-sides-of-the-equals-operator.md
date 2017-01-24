---
title: "您必須在 &#39;Equals&#39; 運算子兩邊至少各參考一個範圍變數 | Microsoft Docs"
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
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 您必須在 &#39;Equals&#39; 運算子兩邊至少各參考一個範圍變數
您必須在 'Equals' 運算子兩邊至少各參考一個範圍變數。 範圍變數 \<變數\> 必須出現在 'Equals' 運算子的一邊，而範圍變數 \<變數\> 則必須出現在另一邊。  
  
 要加入 LINQ 查詢中的集合所識別的區域變數必須出現在 `Equals` 運算子的兩邊，至於出現在哪一邊則取決於識別變數的集合。 換句話說，所要加入之其中一個集合所識別的範圍變數，必須與所要加入之另一個集合所識別的範圍變數出現在 `Equals` 運算子的不同邊。 來自不同集合的範圍變數不能混合放在 `Equals` 運算子的同一邊。  
  
 `Equals` 運算子的兩邊必須至少參考一個來自所加入之個別集合的變數。  
  
 **錯誤 ID︰**BC36622  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)   
 [Join Clause](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [From Clause](../Topic/From%20Clause%20\(Visual%20Basic\).md)   
 [Select Clause](../Topic/Select%20Clause%20\(Visual%20Basic\).md)