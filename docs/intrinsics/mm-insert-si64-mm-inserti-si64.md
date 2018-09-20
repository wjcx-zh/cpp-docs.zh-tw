---
title: _mm_insert_si64、_mm_inserti_si64 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f859b461a2072afabbe48126eba94e0a3ed470a3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403860"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64、_mm_inserti_si64

**Microsoft 專屬**

會產生`insertq`指令，以便從其第二個運算元中插入第一個運算元的位元。

## <a name="syntax"></a>語法

```
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

#### <a name="parameters"></a>參數

*Source1*<br/>
[in]128 位元欄位，以在其較低的 64 位元，以將插入的欄位中的輸入資料。

*Source2*<br/>
[in]要插入其低的位元的資料與 128 位元欄位。  針對`_mm_insert_si64`，也會包含在其高的位元欄位描述元。

*長度*<br/>
[in]整數常數，指定要插入之欄位的長度。

*Tuple*<br/>
[in]整數常數，指定將插入資料之欄位的最小顯著性位元的索引。

## <a name="return-value"></a>傳回值

128 位元欄位，其較低的 64 位元包含原始低 64 個位元`Source1`與指定的位元欄位取代的低位元`Source2`。 傳回值的較高的 64 位元會定義。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式會產生`insertq`插入的位元指令`Source2`到`Source1`。 有內建的這兩個版本： `_mm_inserti_si64`，是即時版本，和`_mm_insert_si64`是非直接。  每個版本從 Source2 擷取為給定長度的位元欄位，並將它插入 Source1。  擷取的位元是 Source2 的最小顯著性位元。  將插入這些位元欄位 Source1 定義長度以及其最小顯著性的位元的索引。  長度和索引的值取自 mod 64，因此解譯為 63 的-1 到 127 之間。 如果 （降低） 的位元索引和 （降低） 的欄位長度的總和大於 64，結果會是未定義。 欄位長度為零的值會解譯為 64。  如果欄位長度和位元索引的這兩個零個、 位元 63:0`Source2`插入至`Source1`。  如果欄位長度為零，但位元索引為非零，則結果為未定義。

_Mm_insert_si64 呼叫，則欄位長度都包含在位元 77:72 Source2 和位元 69:64 中的索引。

如果您呼叫`_mm_inserti_si64`引數時，編譯器無法判斷要當做整數常數，則編譯器會產生程式碼封裝到 XMM 暫存器的這些值，並呼叫`_mm_insert_si64`。

若要判斷硬體支援`insertq`指令呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 6 的`CPUInfo[2] (ECX)`。 此位元會經過支援指令，則為 1 和 0。 如果您執行程式碼使用此內建在不支援的硬體上`insertq`指令，結果會無法預測。

## <a name="example"></a>範例

```
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**結束 Microsoft 專屬**

進階 Micro 裝置，inc.copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製

## <a name="see-also"></a>另請參閱

[_mm_extract_si64、_mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)