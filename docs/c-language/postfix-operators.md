---
title: "後置運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "運算子 [C], 後置"
  - "後置運算子"
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 後置運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

後置運算子在運算式評估時具有最高優先順序 \(具有更緊密的繫結\)。  
  
## 語法  
 *postfix\-expression*：  
 *primary\-expression*  
  
 *postfix\-expression*  **\[**  *expression*  **\]**  
  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *postfix\-expression*  **.**  *identifier*  
  
 *postfix\-expression*  **–\>**  *identifier*  
  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 此優先順序層級的運算子為陣列註標、函式呼叫、結構和等位成員，以及後置遞增和遞減運算子。  
  
## 請參閱  
 [C 運算子](../c-language/c-operators.md)