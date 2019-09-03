---
title: _mm_insert_si64、_mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221781"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64、_mm_inserti_si64

**Microsoft 專屬**

`insertq`產生指示, 將其第二個運算元的位插入其第一個運算元。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*Source1.rc*\
在128位欄位, 其具有較低64位的輸入資料, 將在其中插入欄位。

*Source2*\
在128位欄位, 含有要插入其低位的資料。  針對`_mm_insert_si64`, 也會包含其高位的欄位描述項。

*長*\
在整數常數, 指定要插入之欄位的長度。

*指數*\
在整數常數, 指定要在其中插入資料之欄位的最小有效位索引。

## <a name="return-value"></a>傳回值

128位欄位, 其較低的64位包含*source1.rc*的原始低64位, 且指定的位欄位已由低位的*Source2*取代。 傳回值的64位上限未定義。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些內建函式會`insertq`產生指示, 以將*Source2*中的位插入*source1.rc*。 有兩個版本: `_mm_inserti_si64`、是立即版本, 而且`_mm_insert_si64`是非立即的。 每個版本都會從 Source2 中提取指定長度的位欄位, 並將其插入 Source1.rc。  解壓縮的位是最不重要的 Source2 位。  將插入這些位的欄位 Source1.rc 是由長度和最小有效位的索引所定義。  長度和索引的值會採用 mod 64, 因此-1 和127都會被視為63。 如果 (減少) 位索引和 (縮減) 欄位長度的總和大於 64, 則結果會是未定義的。 欄位長度為零的值會解讀為64。 如果欄位長度和位索引皆為零, 則會將*Source2*的 bits 63:0 插入*source1.rc*中。 如果欄位長度為零, 但位索引不是零, 則結果會是未定義的。

在呼叫 _mm_insert_si64 時, 欄位長度包含在 Source2 的位77:72 和位69:64 的索引中。

如果您使用`_mm_inserti_si64`編譯器無法判斷為整數常數的引數呼叫, 編譯器會產生程式碼, 將這些值封裝成 XMM 暫存器並呼叫`_mm_insert_si64`。

若要判斷`insertq`指令的硬體支援, 請使用`__cpuid` `InfoType=0x80000001`呼叫內建函式並檢查的`CPUInfo[2] (ECX)`位6。 如果支援指令, 則此位為 1, 否則為0。 如果您在不支援`insertq`指令的硬體上執行使用內建的程式碼, 結果會是無法預測的。

## <a name="example"></a>範例

```cpp
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

由 Advanced 微裝置, Inc. 的部分著作權2007著作權所有，並保留一切權利。 已從 Advanced 微裝置, Inc. 的許可權重現

## <a name="see-also"></a>另請參閱

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
