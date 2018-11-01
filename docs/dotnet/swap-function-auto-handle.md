---
title: swap 函式 (auto_handle)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::swap
- msclr.swap
helpviewer_keywords:
- swap function
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
ms.openlocfilehash: a4e15e2a0481f10b58517135c5dc283549f358af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638298"
---
# <a name="swap-function-autohandle"></a>swap 函式 (auto_handle)

交換物件之間一個`auto_handle`是另一個。

## <a name="syntax"></a>語法

```
template<typename _element_type>
void swap(
   auto_handle<_element_type> % _left,
   auto_handle<_element_type> % _right
);
```

#### <a name="parameters"></a>參數

*_left*<br/>
`auto_handle`。

*右方 （_r)*<br/>
另一個`auto_handle`。

## <a name="example"></a>範例

```
// msl_swap_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   swap( s1, s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_handle.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle::swap](../dotnet/auto-handle-swap.md)