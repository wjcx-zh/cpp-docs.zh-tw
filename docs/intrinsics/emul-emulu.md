---
title: __emul、__emulu
ms.date: 09/02/2019
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 16b2b38f6f44b99c9f5b9370ba586342a860684e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216737"
---
# <a name="__emul-__emulu"></a>__emul、__emulu

**Microsoft 專屬**

執行乘法運算, 以使32位整數可以保留的內容溢位。

## <a name="syntax"></a>語法

```C
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

### <a name="parameters"></a>參數

*為*\
在乘法的第一個整數運算元。

*位元組*\
在乘法的第二個整數運算元。

## <a name="return-value"></a>傳回值

相乘的結果。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__emul`|x86、x64|
|`__emulu`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`__emul`採用 2 32 位帶正負號的值, 並以64位帶正負號的整數值傳回相乘的結果。

`__emulu`採用 2 32 位不帶正負號的整數值, 並以64位不帶正負號整數值的形式傳回相乘的結果。

## <a name="example"></a>範例

```cpp
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Output

```Output
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
