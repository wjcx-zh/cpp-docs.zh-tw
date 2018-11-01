---
title: _status87、_statusfp、_statusfp2
ms.date: 04/05/2018
apiname:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 271c28dd4e267e5b3b702858cc398689e3e35d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597509"
---
# <a name="status87-statusfp-statusfp2"></a>_status87、_statusfp、_statusfp2

取得浮點狀態字組。

## <a name="syntax"></a>語法

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>參數

*px86*<br/>
這個位址會填入 x87 浮點單位的狀態字組。

*pSSE2*<br/>
這個位址會填入 SSE2 浮點單位的狀態字組。

## <a name="return-value"></a>傳回值

針對 **_status87**並 **_statusfp**，傳回值中的位元表示浮點狀態。 請參閱浮點數。H 包含檔案的定義所傳回的位元 **_statusfp**。 許多數學程式庫函式都會修改浮點狀態字組，伴隨著無法預期的結果。 最佳化可以重新排列、 結合及消除呼叫的浮點運算 **_status87**， **_statusfp**，和相關函式。 使用 [/Od (停用 (偵錯))](../../build/reference/od-disable-debug.md) 編譯器選項或 [fenv_access](../../preprocessor/fenv-access.md) pragma 指示詞，防止最佳化重新排序浮點運算。 從中傳回值 **_clearfp**並 **_statusfp**，和也傳回參數的 **_statusfp2**，如果較少浮點作業將會更加可靠之間的浮點狀態字組的已知狀態。

## <a name="remarks"></a>備註

**_Statusfp**函式會取得浮點狀態字組。 狀態字組是浮點處理器狀態與浮點例外狀況處理常式所偵測到之其他條件的組合，例如浮點堆疊溢位和反向溢位。 傳回狀態字組的內容之前，會檢查取消遮罩的例外狀況。 這表示會通知呼叫端有關暫止例外狀況。 在 x86 平台 **_statusfp**傳回 x87 和 SSE2 浮點狀態的組合。 在 x64 平台上，傳回的狀態是根據 SSE 的 MXCSR 狀態。 在 ARM 平台， **_statusfp**傳回 FPSCR 暫存器中的狀態。

**_statusfp**平台無關的可攜式版本 **_status87**。 它等同於 **_status87** Intel (x86) 平台上，也受 x64 和 ARM 平台支援。 若要確保您的浮點程式碼可移植到所有的架構，請使用 **_statusfp**。 如果您只的目標 x86 平台，您可以使用 **_status87**或是 **_statusfp**。

我們建議 **_statusfp2**如有 x87 和 SSE2 浮點處理器的晶片 （例如 Pentium IV)。 針對 **_statusfp2**，位址會填入 x87 或 SSE2 浮點處理器使用浮點狀態字組。 針對支援 x87 和 SSE2 浮點處理器的晶片，則 EM_AMBIGUOUS 會設為 1; 如果 **_statusfp**或是 **_controlfp**用和動作模稜兩可，因為它無法參照 x87 或 SSE2浮點狀態字組。 **_Statusfp2**函式才支援 x86 平台。

這些函式不適用於[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)因為 common language runtime (CLR) 只支援預設的浮點精確度。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_status87**， **_statusfp**， **_statusfp2**|\<float.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
