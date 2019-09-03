---
title: _bittestandset, _bittestandset64
ms.date: 09/02/2019
f1_keywords:
- _bittestandset_cpp
- _bittestandset64_cpp
- _bittestandset64
- _bittestandset
helpviewer_keywords:
- bts instruction
- _bittestandset intrinsic
- _bittestandset64 intrinsic
ms.assetid: 6d6c8670-fea0-4c1c-9aad-2bb842715203
ms.openlocfilehash: d54be5688acfb1e3cfc9d79514c39f665efdd9fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216880"
---
# <a name="_bittestandset-_bittestandset64"></a>_bittestandset, _bittestandset64

**Microsoft 專屬**

產生指示來檢查位址`b` `a`的位、傳回其目前值, 並將位設為1。

## <a name="syntax"></a>語法

```C
unsigned char _bittestandset(
   long *a,
   long b
);
unsigned char _bittestandset64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>參數

*為*\
[in、out]要檢查之記憶體的指標。

*位元組*\
在要測試的位位置。

## <a name="return-value"></a>傳回值

位於指定位置的位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_bittestandset`|x86、ARM、x64、ARM64|
|`_bittestandset64`|x64、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// bittestandset.cpp
// processor: x86, ARM, x64
// This example uses several of the _bittest family of intrinsics
// to implement a Flags class that allows bit level access to an
// integer field.
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_bittestandset, _bittestandreset,\
                  _bittestandcomplement, _bittest)

class Flags
{
private:
    long flags;
    long* oldValues;

public:
    Flags() : flags(0)
    {
        oldValues = new long[32];
    }

    ~Flags()
    {
        delete oldValues;
    }

    void SetFlagBit(long nBit)
    {
        // We omit range checks on the argument
        oldValues[nBit] = _bittestandset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    void ClearFlagBit(long nBit)
    {
        oldValues[nBit] = _bittestandreset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    unsigned char GetFlagBit(long nBit)
    {
        unsigned char result = _bittest(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
        return result;
    }
    void RestoreFlagBit(long nBit)
    {
        if (oldValues[nBit])
            oldValues[nBit] = _bittestandset(&flags, nBit);
        else
            oldValues[nBit] = _bittestandreset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    unsigned char ToggleBit(long nBit)
    {
        unsigned char result = _bittestandcomplement(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
        return result;
    }
};

int main()
{
    Flags f;
    f.SetFlagBit(1);
    f.SetFlagBit(2);
    f.SetFlagBit(3);
    f.ClearFlagBit(3);
    f.ToggleBit(1);
    f.RestoreFlagBit(2);
}
```

```Output
Flags: 0x2
Flags: 0x6
Flags: 0xe
Flags: 0x6
Flags: 0x4
Flags: 0x0
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
