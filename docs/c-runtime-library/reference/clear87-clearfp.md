---
title: _clear87、_clearfp
ms.date: 04/05/2018
apiname:
- _clearfp
- _clear87
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 4148f85d82a4210033686455c73046081832e3c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340543"
---
# <a name="clear87-clearfp"></a>_clear87、_clearfp

取得及清除浮點狀態字組。

## <a name="syntax"></a>語法

```C
unsigned int _clear87( void );
unsigned int _clearfp( void );
```

## <a name="return-value"></a>傳回值

傳回的值中的位元表示浮點狀態，再呼叫 **_clear87**或是 **_clearfp**。 如需完整的定義所傳回的位元 **_clear87**，請參閱 Float.h。 許多數學程式庫函式會修改 8087/80287 狀態字組，伴隨著無法預期的結果。 傳回值，從 **_clear87**並 **_status87**變得更加可靠，因為浮點狀態字組之已知狀態之間執行較少浮點運算。

## <a name="remarks"></a>備註

**_Clear87**函式，可清除浮點狀態字組中的例外狀況旗標、 忙碌的位元設定為 0，並在傳回狀態字組。 浮點狀態字組是 8087/80287 狀態字組和 8087/80287 例外狀況處理常式所偵測到其他條件的組合，例如浮點的堆疊溢位和反向溢位。

**_clearfp**平台無關的可攜式版本 **_clear87**常式。 它等同於 **_clear87** Intel (x86) 平台上，也受 x64 和 ARM 平台支援。 若要確保您的浮點程式碼移植到 x64 和 ARM，使用 **_clearfp**。 如果您只的目標 x86 平台，您可以使用 **_clear87**或是 **_clearfp**。

進行編譯時，會取代這些函式[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)因為 common language runtime 只支援預設的浮點精確度。

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
