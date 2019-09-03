---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221317"
---
# <a name="__rdtscp"></a>__rdtscp

**Microsoft 專屬**

會產生`TSC_AUX[31:0`指令、寫入至記憶體, 並傳回64位時間戳記計數器 (`TSC)` result。 `rdtscp`

## <a name="syntax"></a>語法

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>參數

*AUX*\
脫銷將包含電腦特定`TSC_AUX[31:0]`暫存器內容之位置的指標。

## <a name="return-value"></a>傳回值

64位不帶正負號的整數滴答計數。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__rdtscp`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建函式會`rdtscp`產生指令。 `__rdtscp` 若要判斷此指示的硬體支援, 請`__cpuid`使用`InfoType=0x80000001`呼叫內建函式, 並檢查`CPUInfo[3] (EDX)`的位27。 如果支援指令, 則此位為 1, 否則為0。  如果您在不支援`rdtscp`指令的硬體上執行使用內建的程式碼, 結果會是無法預測的。

此指令會等到所有先前的指示都已執行, 而且所有先前的載入都是全域可見的。 不過, 它不是序列化指令。 如需詳細資訊, 請參閱 Intel 和 AMD 手冊。

中`TSC_AUX[31:0]`的值意義取決於作業系統。

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

[__rdtsc](../intrinsics/rdtsc.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
