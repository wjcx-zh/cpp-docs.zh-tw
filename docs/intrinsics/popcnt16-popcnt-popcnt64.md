---
title: __popcnt16、__popcnt、__popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221352"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16、__popcnt、__popcnt64

**Microsoft 專屬**

計算16、32 `1`或64位不帶正負號整數中的位數 (人口數)。

## <a name="syntax"></a>語法

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>參數

*value*\
在我們想要其人口計數的16、32或64位不帶正負號的整數。

## <a name="return-value"></a>傳回值

Value 參數中`1`的位數 。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__popcnt16`|先進的位操作|
|`__popcnt`|先進的位操作|
|`__popcnt64`|64位模式中的先進位操作。|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

每個內建函式都會產生`popcnt`指令。 在32位模式中, 沒有64位的一般用途暫存器, 因此不支援64位`popcnt` 。

若要判斷`popcnt`指令的硬體支援, 請`__cpuid`呼叫內建函式`InfoType=0x00000001`並核取的`CPUInfo[2] (ECX)`位23。 如果支援指令, 則此位為 1, 否則為0。 如果您在不支援`popcnt`指令的硬體上執行使用這些內建函式的程式碼, 結果會是無法預測的。

## <a name="example"></a>範例

```cpp
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**結束 Microsoft 專屬**

由 Advanced 微裝置, Inc. 的部分著作權2007著作權所有，並保留一切權利。 已從 Advanced 微裝置, Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
