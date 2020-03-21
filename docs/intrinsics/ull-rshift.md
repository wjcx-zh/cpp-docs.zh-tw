---
title: __ull_rshift
ms.date: 09/02/2019
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: bf9fe7775cee1c774c097a1b6bd371721c9fa34f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80074981"
---
# <a name="__ull_rshift"></a>__ull_rshift

**Microsoft 專屬**

在 x64 上，會使用第二個參數所指定的位數，將第一個參數所指定的64位值向右移位。

## <a name="syntax"></a>語法

```C
unsigned __int64 __ull_rshift(
   unsigned __int64 mask,
   int nBit
);
```

### <a name="parameters"></a>參數

*遮罩*\
在要右移的64位整數值。

*nBit*\
在要移位的位數、x86 上的模數32，以及 x64 上的模數64。

## <a name="return-value"></a>傳回值

以 `nBit` 位移位的遮罩。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ull_rshift`|x86、x64|

**標頭檔**\<intrin.h >

## <a name="remarks"></a>備註

如果 x86 上的第二個參數大於31（x64 上為63），該數位會取得模數32（x64 上的64），以判斷要移位的位數。 名稱中的 `ull` 表示 `unsigned long long (unsigned __int64)`。

## <a name="example"></a>範例

```cpp
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

```Output
1
```

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ll_rshift](../intrinsics/ll-rshift.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
