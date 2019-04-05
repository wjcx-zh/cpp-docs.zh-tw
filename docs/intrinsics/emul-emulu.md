---
title: __emul、__emulu
ms.date: 11/04/2016
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 8657c0fb034ac6bbcfbebb946e059ad08d9e7046
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030046"
---
# <a name="emul-emulu"></a>__emul、__emulu

**Microsoft 特定的**

執行乘法運算可以保存的 32 位元整數的溢位。

## <a name="syntax"></a>語法

```
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

#### <a name="parameters"></a>參數

*一個*<br/>
[in]第一個整數運算元的乘法運算。

*b*<br/>
[in]第二個整數運算元的乘法運算。

## <a name="return-value"></a>傳回值

乘法運算的結果。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__emul`|x86、x64|
|`__emulu`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`__emul` 採用兩個 32 位元帶正負號的值，並傳回做為 64 位元帶正負號的整數值相乘的結果。

`__emulu` 採用兩個 32 位元不帶正負號的整數值，並傳回做為 64 位元不帶正負號的整數值相乘的結果。

## <a name="example"></a>範例

```
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

```
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)