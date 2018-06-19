---
title: 編譯器錯誤 C3738 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3738
dev_langs:
- C++
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf54ba4114c0184871f1c79ca8f1757ae7e78b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265670"
---
# <a name="compiler-error-c3738"></a>編譯器錯誤 C3738
'calling_convention': 明確具現化的呼叫慣例，必須符合要具現化的範本  
  
 建議您不要明確具現化指定呼叫慣例。 如果您必須，不過，必須符合呼叫慣例。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3738。  
  
```  
// C3738.cpp  
// compile with: /clr  
// processor: x86  
#include <stdio.h>  
template< class T >  
void f ( T arg ) {   // by default calling convention is __cdecl  
   printf ( "f: %s\n", __FUNCSIG__ );  
}  
  
template   
void __stdcall f< int > ( int arg );   // C3738  
// try the following line instead  
// void f< int > ( int arg );  
  
int main () {  
   f(1);  
   f< int > ( 1 );  
}  
```