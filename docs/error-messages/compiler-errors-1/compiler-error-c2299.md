---
title: "編譯器錯誤 C2299 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2299"
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 編譯器錯誤 C2299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 行為變更: 明確特製化不能是複製建構函式或複製指派運算子  
  
 對 Visual C\+\+ 2005 的編譯器完成一致性處理後也可能會發生這項錯誤：舊版 Visual C\+\+ 允許將複製建構函式或複製指派運算子明確特製化。  
  
 若要解決 C2299 的問題，請不要讓複製建構函式或指派運算子成為樣板函式，而要讓非樣板函式採用類別型別。  透過明確指定樣板引數呼叫複製建構函式或指派運算子的任何程式碼都需要移除樣板引數。  
  
 下列範例會產生 C2299：  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```