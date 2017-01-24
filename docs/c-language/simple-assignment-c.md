---
title: "簡單指派 (C) | Microsoft Docs"
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
  - "指派運算子 [C++], 簡單"
  - "資料類型轉換 [C++], 簡單指派"
  - "等號"
  - "運算子 [C], 簡單指派"
  - "簡單指派運算子"
  - "類型轉換 [C++], 簡單指派"
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 簡單指派 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

簡單指派運算子會將其右運算元指派給其左運算元。  右運算元的值會轉換為指派運算式的類型，並且取代儲存在左運算元指定之物件中的值。  以指派的轉換規則為準 \(請參閱[指派轉換](../c-language/assignment-conversions.md)\)。  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 在此範例中，`y` 的值會轉換成類型 **double** 並指派給 `x`。  
  
## 請參閱  
 [C 指派運算子](../c-language/c-assignment-operators.md)