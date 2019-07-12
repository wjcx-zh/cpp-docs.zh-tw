---
title: __rdtscp
ms.date: 07/11/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b8a31c6d19cd171cbe909c75a27c2389866bd578
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861119"
---
# <a name="rdtscp"></a>__rdtscp

**Microsoft 專屬**

會產生`rdtscp`的指示，將寫入`TSC_AUX[31:0`] 的記憶體，並傳回 64 位元時間戳記計數器 (`TSC)`結果。

## <a name="syntax"></a>語法

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>參數

*Aux*<br/>
[out]將包含特定電腦的暫存器內容的位置指標`TSC_AUX[31:0]`。

## <a name="return-value"></a>傳回值

64 位元不帶正負號的整數的滴答計數。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__rdtscp`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式會產生`rdtscp`指令。 若要判斷此指令的硬體支援，請呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查一些 27 `CPUInfo[3] (EDX)`。 此位元可說是支援的指示，則為 1 和 0。  如果您執行程式碼使用此內建在不支援的硬體上`rdtscp`指令，結果會無法預測。

這個指令會等到所有前面的指示執行，以及所有先前的負載都是全域可見。 不過，它不是序列化的指示。 Intel 和 AMD 手冊，如需詳細資訊，請參閱。

中值的意義`TSC_AUX[31:0]`取決於作業系統。

## <a name="example"></a>範例

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**結束 Microsoft 專屬**


## <a name="see-also"></a>另請參閱

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)