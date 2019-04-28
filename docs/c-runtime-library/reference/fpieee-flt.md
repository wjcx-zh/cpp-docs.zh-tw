---
title: _fpieee_flt
ms.date: 04/05/2018
apiname:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 9a49ec403b1cb95407b0a366accf1d9374d9cb22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333244"
---
# <a name="fpieeeflt"></a>_fpieee_flt

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

*handler*<br/>
使用者之 IEEE 設陷處理常式的指標。

## <a name="return-value"></a>傳回值

傳回值 **_fpieee_flt**是所傳回的值*處理常式*。 因此，IEEE 篩選常式可能會用於結構化例外狀況處理 (SEH) 機制的 except 子句。

## <a name="remarks"></a>備註

**_Fpieee_flt**函式會叫用 IEEE 浮點例外狀況的使用者定義的設陷處理常式，並提供所有的相關資訊。 此常式作為 SEH 機制中的例外狀況篩選，可在必要時叫用您自己的 IEEE 例外狀況處理常式。

**_FPIEEE_RECORD** Fpieee.h 中所定義的結構包含 IEEE 浮點例外狀況的相關資訊。 此結構會傳遞至使用者定義的設陷處理常式 **_fpieee_flt**。

|_FPIEEE_RECORD 欄位|描述|
|----------------------------|-----------------|
|**RoundingMode**<br/>**整數位數**|這些**不帶正負號** **int**欄位包含的相關資訊的浮點環境時，發生例外狀況。|
|**Operation**|這**不帶正負號** **int**欄位表示已導致陷阱的作業類型。 如果類型是比較 (**_FpCodeCompare**)，您可以提供其中一個特殊 **_FPIEEE_COMPARE_RESULT**中的值 （如 Fpieee.h 中所定義） **Result.Value**欄位。 轉換類型 (**_FpCodeConvert**) 表示設陷發生在浮點轉換作業期間。 您可以看看**Operand1**並**結果**類型，以判斷正在嘗試之轉換的類型。|
|**Operand1**<br/>**Operand2**<br/>**結果**|這些 **_FPIEEE_VALUE**結構表示的型別和建議的結果和運算元的值。 每個結構會包含下列欄位：<br /><br /> **OperandValid** -旗標，指出回應的值是否有效。<br />**格式**-之對應值的資料類型。 即使對應的值無效，還是可能會傳回格式類型。<br />**值**-結果或運算元資料值。|
|**原因**<br/>**Enable**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS**包含一個位元欄位，每個類型的浮點例外狀況。 這些欄位與用來遮罩提供給 [_controlfp](control87-controlfp-control87-2.md) 之例外狀況的引數之間具有對應關係。 每個位元的確切意義取決於內容︰<br /><br /> **原因**-每個設定的位元都表示所引發的特定例外狀況。<br />**啟用**-每個設定的位元都表示特定的例外狀況目前取消遮罩。<br />**狀態**-每個設定的位元都表示特定的例外狀況目前暫止。 這包括已因為進行遮罩所未引發的例外狀況 **_controlfp**。|

啟用暫止例外狀況時，會引發停用的暫止例外狀況。 這會導致未定義的行為時使用 **_fpieee_flt**為例外狀況篩選條件。 一律在啟用浮點例外狀況之前呼叫 [_clearfp](clear87-clearfp.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
