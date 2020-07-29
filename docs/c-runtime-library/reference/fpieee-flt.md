---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: c6a77dcba06b58191781900d4e24202c6335cfb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213563"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

針對 IEEE 浮點例外狀況叫用使用者定義的設陷處理常式。

## <a name="syntax"></a>語法

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>參數

*excCode*<br/>
例外狀況代碼。

*excInfo*<br/>
Windows NT 例外狀況資訊結構的指標。

*處理器*<br/>
使用者之 IEEE 設陷處理常式的指標。

## <a name="return-value"></a>傳回值

**_Fpieee_flt**的傳回值是*處理常式*所傳回的值。 因此，IEEE 篩選常式可能會用於結構化例外狀況處理 (SEH) 機制的 except 子句。

## <a name="remarks"></a>備註

**_Fpieee_flt**函式會針對 IEEE 浮點例外狀況叫用使用者定義的設陷處理常式，並提供所有相關資訊。 此常式作為 SEH 機制中的例外狀況篩選，可在必要時叫用您自己的 IEEE 例外狀況處理常式。

定義于 Fpieee.h 所中的 **_FPIEEE_RECORD**結構包含與 IEEE 浮點例外狀況相關的資訊。 這個結構會藉由 **_fpieee_flt**傳遞至使用者定義的設陷處理常式。

|_FPIEEE_RECORD 欄位|說明|
|----------------------------|-----------------|
|**RoundingMode**<br/>**有效位數**|這些 **`unsigned int`** 欄位包含發生例外狀況時的浮點環境相關資訊。|
|**運算**|此 **`unsigned int`** 欄位表示造成陷阱的作業類型。 如果類型是比較（**_FpCodeCompare**），您可以在 [**結果] 值**欄位中提供其中一個特殊的 **_FPIEEE_COMPARE_RESULT**值（如 fpieee.h 所中所定義）。 轉換類型（**_FpCodeConvert**）表示在浮點轉換作業期間發生 trap。 您可以查看**Operand1**和**結果**類型，以判斷所嘗試的轉換類型。|
|**Operand1**<br/>**Operand2**<br/>**結果**|這些 **_FPIEEE_VALUE**結構會指出所提議之結果和運算元的類型和值。 每個結構都包含下欄欄位：<br /><br /> **OperandValid** -表示回應值是否有效的旗標。<br />**格式**：對應值的資料類型。 即使對應的值無效，還是可能會傳回格式類型。<br />**值**-結果或運算元資料值。|
|**原因**<br/>**啟用**<br/>**狀態**|**_FPIEEE_EXCEPTION_FLAGS**包含每個浮點例外狀況類型的一個位欄位。 這些欄位與用來遮罩提供給 [_controlfp](control87-controlfp-control87-2.md) 之例外狀況的引數之間具有對應關係。 每個位元的確切意義取決於內容︰<br /><br /> **原因**-每個設定的位都表示所引發的特定例外狀況。<br />**Enable** -每個設定的位都表示特定的例外狀況目前不會取消遮罩。<br />**狀態**-每個設定的位都表示特定的例外狀況目前處於暫止狀態。 這包括未引發的例外狀況，因為它們已 **_controlfp**的遮罩。|

啟用暫止例外狀況時，會引發停用的暫止例外狀況。 當使用 **_fpieee_flt**做為例外狀況篩選準則時，這可能會導致未定義的行為。 一律在啟用浮點例外狀況之前呼叫 [_clearfp](clear87-clearfp.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp、 \_ _control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
