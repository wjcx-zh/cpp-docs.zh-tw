---
title: 編譯器錯誤 C3207 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3207
dev_langs:
- C++
helpviewer_keywords:
- C3207
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0973b929e9feafeed3c2cde0b2b6e9e30996855
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251454"
---
# <a name="compiler-error-c3207"></a>編譯器錯誤 C3207
'function': 'arg' 的無效樣板引數，必須是類別樣板  
  
 樣板函式定義為使用樣板類樣板引數。 不過，已傳遞樣板類型引數。  
  
 下列範例會產生 C3207：  
  
```  
// C3207.cpp  
template <template <class T> class TT>  
void f(){}  
  
template <class T>  
struct S  
{  
};  
  
void f1()  
{  
   f<S<int> >();   // C3207  
   // try the following line instead  
   // f<S>();  
}  
```