---
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: 8838282db851c6811a3f24c75a03b31c5870e6d3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948367"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

啟用或停用 CRT 數學常式中的 Streaming SIMD Extensions 2 （SSE2）指令。 (因為預設會啟用 SSE2，所以此函式不適用於 x64 結構)。

## <a name="syntax"></a>語法

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>參數

*flag*<br/>
1 啟用 SSE2 實作；0 停用 SSE2 實作。 根據預設，會在支援它的處理器上啟用 SSE2 實作。

## <a name="return-value"></a>傳回值

如果啟用 SSE2 實作，則為非零；如果停用 SSE2 實作，則為零。

## <a name="remarks"></a>備註

下列函式具有可使用 **_set_SSE2_enable**來啟用的 SSE2 實作為：

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

因為 SSE2 中間值是 64 位元浮點數量，但預設實作中間值是 80 位元浮點數量，所以這些函式的 SSE2 實作所提供的答案可能會與預設實作略有不同。

> [!NOTE]
> 如果您使用[/Oi （產生內建函式）](../../build/reference/oi-generate-intrinsic-functions.md)編譯器選項來編譯專案，則 **_set_SSE2_enable**不會有任何作用。 **/Oi**編譯器選項可讓編譯器使用內建函式來取代 CRT 呼叫;此行為會覆寫 **_set_SSE2_enable**的效果。 如果您想要保證 **/Oi**不會覆寫 **_set_SSE2_enable**，請使用 **/Oi-** 來編譯您的專案。 當您使用其他表示 **/Oi**的編譯器參數時，這也可能是很好的作法。

只有在遮罩所有例外狀況時，才會使用 SSE2 實作。 使用 [_control87、_controlfp](control87-controlfp-control87-2.md) 來遮罩例外狀況。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)<br/>
