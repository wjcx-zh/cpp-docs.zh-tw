---
title: 編譯器警告 C4972 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4972
dev_langs:
- C++
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf5337a60781c6fb39281f051657ea7ebd9371fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4972"></a>編譯器警告 C4972
直接修改或將 Unbox 作業的結果視為左值，將無法驗證  
  
 對實值類型的控制代碼取值 (也稱為 Unboxing)，然後指派給它，這個作業無法驗證。  
  
 如需詳細資訊，請參閱[Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4972。  
  
```  
// C4972.cpp  
// compile with: /clr:safe  
using namespace System;  
ref struct R {  
   int ^ p;   // a value type  
};  
  
int main() {  
   R ^ r = gcnew R;  
   *(r->p) = 10;   // C4972  
  
   // OK  
   r->p = 10;  
   Console::WriteLine( r->p );  
   Console::WriteLine( *(r->p) );  
}  
```