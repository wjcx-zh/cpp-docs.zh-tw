---
title: 編譯器錯誤 C3195 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce3c51da68b971c34d651826a9c84974957ac46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256882"
---
# <a name="compiler-error-c3195"></a>編譯器錯誤 C3195
'operator': 已被保留，不能做為 ref 類別或實值型別的成員。 必須使用 'operator' 關鍵字定義 CLR 或 WinRT 運算子  
  
編譯器偵測到使用 Managed Extensions for C++ 語法的運算子定義。 您必須使用 c + + 語法的運算子。  
  
下列範例會產生 C3195，並示範如何修正此問題：  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```