---
title: "無法從這些引數推斷類型參數的資料類型，因為可能會有一個以上的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從這些引數推斷類型參數的資料類型，因為可能會有一個以上的類型
無法從這些引數推斷類型參數的資料類型，因為可能會有一個以上的類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 多載解析失敗時，會發生這個錯誤。 它會顯示為附屬訊息，表示為什麼排除特定多載候選項目。 這個錯誤說明，如果套用類型推斷以判斷所呼叫泛型程序之類型參數的資料類型，則編譯器會找到其中至少一個類型參數的多個可能資料類型。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 如需詳細資訊與範例，請參閱[無法從這些引數推斷方法 '\<方法名稱\>' 中類型參數的資料類型，因為可能會有一個以上的類型](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-more-than-one-type-is-possible.md)。  
  
 **錯誤 ID︰**BC36653 和 BC36650  
  
## 請參閱  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)