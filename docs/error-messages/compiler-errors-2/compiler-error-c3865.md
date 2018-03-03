---
title: "編譯器錯誤 C3865 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cec5eabe6f4fa62648e9d3787d8ef2d2133f7736
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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