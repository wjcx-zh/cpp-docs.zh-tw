---
title: 編譯器錯誤 C3865 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99a872d4cf7ed285a0798461c77adf904cfa3e71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275495"
---
# <a name="compiler-error-c3865"></a>編譯器錯誤 C3865
'calling_convention': 只用於原生成員函式  
  
 呼叫慣例的受管理的成員函式或其中一個是全域函式的函式上使用。 只能在原生 （未受管理） 的成員函式的呼叫慣例。  
  
 如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。  
  
 下列範例會產生 C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```