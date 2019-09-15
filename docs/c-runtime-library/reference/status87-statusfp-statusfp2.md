---
title: _status87、_statusfp、_statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958097"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87、_statusfp、_statusfp2

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

針對 **_status87**和 **_statusfp**，傳回值中的位表示浮點狀態。 請參閱 FLOAT。H 包含 **_statusfp**所傳回之位定義的檔案。 許多數學程式庫函式都會修改浮點狀態字組，伴隨著無法預期的結果。 優化可以重新排列、結合和消除對 **_status87**、 **_statusfp**和相關函式之呼叫的浮點運算。 使用 [/Od (停用 (偵錯))](../../build/reference/od-disable-debug.md) 編譯器選項或 [fenv_access](../../preprocessor/fenv-access.md) pragma 指示詞，防止最佳化重新排序浮點運算。 如果在浮點狀態單字的已知狀態之間執行較少的浮點運算，則從 **_clearfp**和 **_statusfp**傳回值，以及 **_statusfp2**的傳回參數也會更可靠。

## <a name="remarks"></a>備註

**_Statusfp**函數會取得浮點狀態字組。 狀態字組是浮點處理器狀態與浮點例外狀況處理常式所偵測到之其他條件的組合，例如浮點堆疊溢位和反向溢位。 傳回狀態字組的內容之前，會檢查取消遮罩的例外狀況。 這表示會通知呼叫端有關暫止例外狀況。 在 x86 平臺上， **_statusfp**會傳回 X87 和 SSE2 浮點狀態的組合。 在 x64 平台上，傳回的狀態是根據 SSE 的 MXCSR 狀態。 在 ARM 平臺上， **_statusfp**會從 fpscr 暫存器註冊傳回狀態。

**_statusfp**是與平臺無關、可移植的 **_status87**版本。 它與 Intel （x86）平臺上的 **_status87**完全相同，而且 X64 和 ARM 平臺也支援。 若要確保您的浮點程式碼可移植到所有架構，請使用 **_statusfp**。 如果您僅以 x86 平臺為目標，您可以使用 **_status87**或 **_statusfp**。

我們建議使用具有 x87 和 SSE2 浮點處理器的晶片（例如 Pentium IV）的 **_statusfp2** 。 若為 **_statusfp2**，則會使用 X87 或 SSE2 浮點處理器的浮點狀態字組來填滿位址。 對於支援 x87 和 SSE2 浮點處理器的晶片，如果使用 **_statusfp**或 **_CONTROLFP** ，則 EM_AMBIGUOUS 會設定為1，且動作不明確，因為它可能會參考 x87 或 SSE2 浮點狀態字組。 只有在 x86 平臺上才支援 **_statusfp2**函數。

這些函數不適用於[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md) ，因為 Common language RUNTIME （clr）只支援預設的浮點精確度。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_status87**、 **_statusfp**、 **_statusfp2**|\<float.h>|

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
