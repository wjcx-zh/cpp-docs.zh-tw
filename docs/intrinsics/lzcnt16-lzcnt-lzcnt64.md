---
title: __lzcnt16，__lzcnt，__lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: fcd801717974a230fbd19cc7802d8f6a011774f7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221798"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16，__lzcnt，__lzcnt64

**Microsoft 專屬**

計算16、32或64位整數中前置零的數目。

## <a name="syntax"></a>語法

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>參數

*value*\
在要掃描前置零的16、32或64位不帶正負號的整數。

## <a name="return-value"></a>傳回值

`value`參數中前置字元為零位的數目。 如果`value`為零, 則傳回值為輸入運算元的大小 (16、32或 64)。 如果的最高有效位`value`為 1, 則傳回值為零。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__lzcnt16`|AMDAdvanced Bit 操作 (ABM)<br /><br /> 迅馳Haswell|
|`__lzcnt`|AMDAdvanced Bit 操作 (ABM)<br /><br /> 迅馳Haswell|
|`__lzcnt64`|AMD64位模式中的先進位操作 (ABM)。<br /><br /> 迅馳Haswell|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

每個內建函式都會產生`lzcnt`指令。  `lzcnt`指令傳回值的大小與其引數的大小相同。  在32位模式中, 沒有64位的一般用途暫存器, 因此不支援64位`lzcnt` 。

若要判斷`lzcnt`指令的硬體支援, 請以`__cpuid`呼叫內部`InfoType=0x80000001`函數並檢查的`CPUInfo[2] (ECX)`位5。 如果支援指令, 此位會是 1, 否則為0。 如果您在不支援`lzcnt`指令的硬體上執行使用內建的程式碼, 結果會是無法預測的。

在不支援`lzcnt`指令的 Intel 處理器上, 指示位元組編碼會當做 (位`bsr`掃描反向) 來執行。 如果程式碼可攜性是個`_BitScanReverse`問題, 請考慮改為使用內建函式。 如需詳細資訊, 請參閱[_BitScanReverse、_BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)。

## <a name="example"></a>範例

```cpp
// Compile this test with: /EHsc
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
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**結束 Microsoft 專屬**

本內容的部分是由 Advanced 微裝置, Inc. 所組成的著作權2007。著作權所有，並保留一切權利。 已從 Advanced 微裝置, Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
