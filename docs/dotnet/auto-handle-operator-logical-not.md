---
title: auto_handle::operator!
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr.auto_handle.operator!
- msclr::auto_handle::operator!
- auto_handle.operator!
- auto_handle::operator!
helpviewer_keywords:
- operator!
ms.assetid: 3f6c7729-3260-4842-87f9-c491c140b299
ms.openlocfilehash: 37c5a35d2cecd3e2e6bc58994fc54704f9169200
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558167"
---
# <a name="autohandleoperator"></a>auto_handle::operator!

使用運算子`auto_handle`條件運算式中。

## <a name="syntax"></a>語法

```
bool operator!();
```

## <a name="return-value"></a>傳回值

**true**包裝的物件是否無效;**false**否則。

## <a name="example"></a>範例

```cpp
// msl_auto_handle_operator_not.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "something";
   if ( s1) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_handle.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_handle 成員](../dotnet/auto-handle-members.md)<br/>
[auto_handle::operator bool](../dotnet/auto-handle-operator-bool.md)