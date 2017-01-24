---
title: "編譯器錯誤 C2970 | Microsoft Docs"
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
  - "C2970"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2970"
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2970
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 樣板參數 'param' : 'arg' : 運算式中包含具有內部連結的物件，不能當做非型別引數  
  
 您不能將靜態變數的名稱或位址當做樣板引數使用。  該樣板類別必須是一個可以在編譯期間被評估的常數值。  
  
 下列範例會產生 C2970：  
  
```  
// C2970.cpp  
// compile with: /c  
static int si;  
// could declare nonstatic to resolve all errors  
// int si;  
  
template <int i>   
class X {};  
  
template <int *pi>   
class Y {};  
  
X<si> anX;   // C2970 cannot use static variable in templates  
  
// this would also work  
const int i = 10;  
X<i> anX2;  
```