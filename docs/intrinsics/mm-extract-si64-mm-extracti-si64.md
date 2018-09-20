---
title: _mm_extract_si64、_mm_extracti_si64 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs:
- C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fab2bb7f1e4992d2f1e9e979d4eb6ea8cf426dc3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376508"
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64，_mm_extracti_si64

**Microsoft 專屬**

會產生`extrq`指示來擷取指定的 bits，從第一個引數的 64 低位元。

## <a name="syntax"></a>語法

```
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

#### <a name="parameters"></a>參數

*Source*<br/>
[in]128 位元欄位，以在其較低的 64 位元的輸入資料。

*描述元*<br/>
[in]128 位元欄位，描述元欄位，來擷取。

*長度*<br/>
[in]整數，指定要擷取之欄位的長度。

*Tuple*<br/>
[in]整數，指定要擷取之欄位的索引

## <a name="return-value"></a>傳回值

使用擷取的欄位，以其最小顯著性的位元的 128 位元欄位。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式會產生`extrq`擷取的位元指令`Source`。有內建的這兩個版本：`_mm_extracti_si64`是即時版本，和`_mm_extract_si64`是非直接。  每個版本會從擷取`Source`由它的長度和其最小顯著性的位元的索引所定義的位元欄位。 長度和索引的值取自 mod 64，因此解譯為 63 的-1 到 127 之間。 （降低） 的索引與 （降低） 的欄位長度的總和是否大於 64，則結果為未定義。 欄位長度為零的值會解譯為 64。 如果欄位長度和位元索引的這兩個零個、 位元 63:0`Source`解壓縮。 如果欄位長度為零，但位元索引為非零，則結果為未定義。

_Mm_extract_si64，呼叫`Descriptor`包含 13:8 位元和欄位的長度會擷取位元 5:0 中的資料中的索引...

如果您呼叫`_mm_extracti_si64`具有編譯器無法判斷要當做整數常數的引數，編譯器會產生程式碼封裝到 XMM 暫存器的這些值 (`Descriptor`) 並呼叫`_mm_extract_si64`。

若要判斷硬體支援`extrq`指示，請呼叫`__cpuid`與內建`InfoType=0x80000001`，並檢查位元 6 的`CPUInfo[2] (ECX)`。 此位元會經過支援指令，則為 1 和 0。 如果您執行程式碼使用不支援此內建硬體`extrq`指令，結果會無法預測。

## <a name="example"></a>範例

```
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

進階 Micro 裝置，inc.copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製

## <a name="see-also"></a>另請參閱

[_mm_insert_si64、_mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)