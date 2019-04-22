---
title: __lzcnt16，__lzcnt，__lzcnt64
ms.date: 11/04/2016
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
ms.openlocfilehash: 333d9f2b23fb90388af8395945256956c9222ab9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041334"
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16，__lzcnt，__lzcnt64

**Microsoft 專屬**

計數有前置字元數目的前置零的 16、 32 或 64 位元整數。

## <a name="syntax"></a>語法

```
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

#### <a name="parameters"></a>參數

*value*<br/>
[in]16-、 32 或 64 位元不帶正負號的整數掃描前置零。

## <a name="return-value"></a>傳回值

前置零位元中的數字`value`參數。 如果`value`為零，則傳回值是輸入運算元 （16、 32 或 64） 的大小。 如果最高有效位元`value`為 1，傳回的值為零。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__lzcnt16`|AMD:進階的位元操作 (ABM)<br /><br /> Intel:Haswell|
|`__lzcnt`|AMD:進階的位元操作 (ABM)<br /><br /> Intel:Haswell|
|`__lzcnt64`|AMD:進階位元操作 (ABM) 在 64 位元模式。<br /><br /> Intel:Haswell|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

每個這些內建函式會產生`lzcnt`指令。  值的大小，`lzcnt`指令會傳回其引數的大小相同。  在 32 位元模式中有無 64 位元一般用途的暫存器，因此沒有 64 位元`lzcnt`。

若要判斷硬體支援`lzcnt`指令呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 5 的`CPUInfo[2] (ECX)`。 此位元會經過支援指令，則為 1 和 0。 如果您執行程式碼使用此內建在不支援的硬體上`lzcnt`指令，結果會無法預測。

不支援的 Intel 處理器上`lzcnt`指令的位元組編碼為執行指令， `bsr` （位元掃描相反）。 如果程式碼可攜性有問題，請考慮使用`_BitScanReverse`內建函式改用。 如需詳細資訊，請參閱 < [_bitscanreverse、_bitscanreverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)。

## <a name="example"></a>範例

```
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

本文部分內容是由進階 Micro 裝置，Inc.Copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)
