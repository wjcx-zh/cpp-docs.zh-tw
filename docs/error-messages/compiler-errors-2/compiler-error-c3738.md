---
title: 編譯器錯誤 C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: e313c7d66bc030183e330dd961fad2fb35f02ac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539317"
---
# <a name="compiler-error-c3738"></a>編譯器錯誤 C3738

'calling_convention': 明確具現化的呼叫慣例，必須符合要具現化的範本

建議您不要在明確具現化指定的呼叫慣例。 如果您必須，不過，必須符合的呼叫慣例。

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