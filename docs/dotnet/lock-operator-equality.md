---
title: lock::operator==
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
helpviewer_keywords:
- lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
ms.openlocfilehash: 2e7e78f5d03074058dadd969f150855f305cf85e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647859"
---
# <a name="lockoperator"></a>lock::operator==

等號比較運算子。

## <a name="syntax"></a>語法

```
template<class T> bool operator==(
   T t
);
```

#### <a name="parameters"></a>參數

*t*<br/>
要比較相等的物件。

## <a name="return-value"></a>傳回值

傳回 **，則為 true**如果`t`鎖定的物件，與相同**false**否則。

## <a name="example"></a>範例

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\lock.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[lock 成員](../dotnet/lock-members.md)<br/>
[lock::operator!=](../dotnet/lock-operator-inequality.md)