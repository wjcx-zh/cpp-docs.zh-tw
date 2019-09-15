---
title: _clear87、_clearfp
ms.date: 04/05/2018
api_name:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
ms.openlocfilehash: 4ca49895b881d9e307c1116681bc36f86b167c25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942961"
---
# <a name="_clear87-_clearfp"></a>_clear87、_clearfp

取得及清除浮點狀態字組。

## <a name="syntax"></a>語法

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>傳回值

傳回值中的位表示在呼叫 **_clear87**或 **_clearfp**之前的浮點狀態。 如需 **_clear87**所傳回之位的完整定義，請參閱 Float. h。 許多數學程式庫函式會修改 8087/80287 狀態字組，伴隨著無法預期的結果。 從 **_clear87**和 **_status87**傳回的值會變得更可靠，因為浮點狀態單字的已知狀態之間會執行較少的浮點運算。

## <a name="remarks"></a>備註

**_Clear87**函式會清除浮點狀態字中的例外狀況旗標，將忙碌的位設定為0，並傳回狀態單字。 浮點狀態字組是 8087/80287 狀態字組和 8087/80287 例外狀況處理常式所偵測到其他條件的組合，例如浮點的堆疊溢位和反向溢位。

**_clearfp**是與平臺無關、可移植的 **_clear87**常式版本。 它與 Intel （x86）平臺上的 **_clear87**完全相同，而且 X64 和 ARM 平臺也支援。 若要確保您的浮點程式碼可移植到 x64 和 ARM，請使用 **_clearfp**。 如果您僅以 x86 平臺為目標，您可以使用 **_clear87**或 **_clearfp**。

使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯時，這些函式已被取代，因為 Common language runtime 只支援預設的浮點精確度。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_clear87**|\<float.h>|
|**_clearfp**|\<float.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_clear87.c
// compile with: /Od

// This program creates various floating-point
// problems, then uses _clear87 to report on these problems.
// Compile this program with Optimizations disabled (/Od).
// Otherwise the optimizer will remove the code associated with
// the unused floating-point values.
//

#include <stdio.h>
#include <float.h>

int main( void )
{
   double a = 1e-40, b;
   float x, y;

   printf( "Status: %.4x - clear\n", _clear87()  );

   // Store into y is inexact and underflows:
   y = a;
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );

   // y is denormal:
   b = y;
   printf( "Status: %.4x - denormal\n", _clear87() );
}
```

```Output
Status: 0000 - clear
Status: 0003 - inexact, underflow
Status: 80000 - denormal
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
