---
title: "函式呼叫 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式呼叫"
  - "函式呼叫, C 函式"
  - "函式 [C], 呼叫"
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 函式呼叫 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「函式呼叫」是運算式，其中包含所呼叫函式的名稱，或函式指標的值，以及傳遞至函式的選擇性引數。  
  
## 語法  
 *postfix\-expression*：  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *argument\-expression\-list*：  
 *assignment\-expression*  
  
 *argument\-expression\-list*  **,**  *assignment\-expression*  
  
 *postfix\-expression* 必須求出函式位址的值 \(例如，函式識別項或函式指標的值\)，而 *argument\-expression\-list* 是運算式的清單 \(以逗號分隔\)，其值 \(「引數」\) 會傳遞至函式。  *argument\-expression\-list* 引數可以是空的。  
  
 函式呼叫運算式具有函式傳回值的值和類型。  函式不能傳回陣列類型的物件。  如果函式的傳回類型是 `void` \(也就是說，函式宣告為永不傳回值\)，則函式呼叫運算式也會具有 `void` 類型 \(如需詳細資訊，請參閱[函式呼叫](../c-language/function-calls.md)\)。  
  
## 請參閱  
 [函式呼叫運算子：\(\)](../cpp/function-call-operator-parens.md)