---
title: 編譯器錯誤 C2299 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e21213f08e25050932274a64d0ed56db96f2a453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2299"></a>編譯器錯誤 C2299
'function': 行為變更： 明確特製化不能複製建構函式或複製指派運算子  
  
 也可以針對 Visual c + + 2005年所進行的編譯器一致性工作產生這個錯誤： 舊版 Visual c + + 允許複製建構函式或複製指派運算子的明確特製化。  
  
 若要解決 C2299，請勿複製建構函式或指派運算子的樣板函式，而非樣板函式接受類別型別。 透過明確指定樣板引數呼叫複製建構函式或指派運算子的任何程式碼需要移除的樣板引數。  
  
 下列範例會產生 C2299:  
  
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