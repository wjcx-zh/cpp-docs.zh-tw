---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220025"
---
# <a name="__shiftright128"></a>__shiftright128

**Microsoft 專屬**

移位 128 位元數量，表示兩個距離右邊達 `LowPart` 指定之位元數的 64 位元數量 `HighPart` 和 `Shift`，並傳回結果的較低 64 個位元。

## <a name="syntax"></a>語法

```C
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>參數

*LowPart*\
在要轉移之128位數量的低64位。

*HighPart*\
在要轉移之128位數量的高64位。

*結*\
在要移位的位數。

## <a name="return-value"></a>傳回值

結果的較低 64 個位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__shiftright128`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`Shift` 值一律為模數 64，使得 (舉例而言) 如果您呼叫 `__shiftright128(0, 1, 64)`，函式將向右移高部分 `0` 個位元，並傳回 `0` 而非 `1` 的低部分，因為將會預期其他值。

## <a name="example"></a>範例

如需範例, 請參閱[__shiftleft128](../intrinsics/shiftleft128.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__shiftleft128](../intrinsics/shiftleft128.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
