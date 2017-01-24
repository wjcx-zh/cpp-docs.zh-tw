---
title: "編譯器錯誤 C2803 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2803"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2803"
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2803
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operator' 至少必須擁有一個類別型別的型式參數  
  
 多載運算子欠缺一個類別型別的參數。  
  
 您必須由參考 \(不使用指標，而使用參考\) 或值來傳遞至少一個參數，才能寫入 "a \< b" \(a 和 b 屬於型別類別 A\)。  
  
 如果兩個參數都是指標，它將是指標位址的純比較，而不會使用使用者定義的轉換。  
  
 下列範例會產生 C2803：  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```