---
title: _mm_extract_si64，_mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: cfd7029966c29f876f0e4f671830e20e2eacc940
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217410"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64，_mm_extracti_si64

**Microsoft 專屬**

`extrq`產生指令, 以從其第一個引數的低64位解壓縮指定的位。

## <a name="syntax"></a>語法

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>參數

*Source*\
在128位欄位, 其中的輸入資料位於其較低的64位。

*描述項*\
在128位欄位, 描述要解壓縮的位欄位。

*長*\
在整數, 指定要解壓縮的欄位長度。

*指數*\
在整數, 指定要解壓縮之欄位的索引

## <a name="return-value"></a>傳回值

128位欄位, 其中的已解壓縮欄位的最小有效位。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些內建函式會`extrq`產生從*來源*解壓縮 bits 的指示。 有兩個版本: `_mm_extracti_si64`是「立即」版本, `_mm_extract_si64`而不是「即時」 (immediate)。 每個版本都會從*來源*中依其長度所定義的位欄位, 以及其最低有效位的索引來解壓縮。 長度和索引的值會採用 mod 64, 因此-1 和127都會被視為63。 如果 (縮減) 索引和 (縮減) 欄位長度的總和大於 64, 則結果會是未定義的。 欄位長度為零的值會解讀為64。 如果欄位長度和位索引皆為零, 則會解壓縮*來源*的 bits 63:0。 如果欄位長度為零, 但位索引不是零, 則結果會是未定義的。

在對的呼叫`_mm_extract_si64`中,*描述*元包含位13:8 的索引, 以及要在 bits 5:0 中解壓縮之資料的欄位長度。

如果您使用`_mm_extracti_si64`編譯器無法判斷為整數常數的引數呼叫, 編譯器會產生程式碼, 將這些值封裝成 XMM 暫存器 (*描述*元) 並`_mm_extract_si64`呼叫。

若要判斷`extrq`指令的硬體支援, 請使用`__cpuid` `InfoType=0x80000001`呼叫內建函式並檢查的`CPUInfo[2] (ECX)`位6。 如果支援指令, 此位會是 1, 否則為0。 如果您執行的程式碼使用的內部硬體不支援該`extrq`指令, 則結果會是無法預測的。

## <a name="example"></a>範例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**結束 Microsoft 專屬**

由 Advanced 微裝置, Inc. 的部分著作權2007著作權所有，並保留一切權利。 已從 Advanced 微裝置, Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
