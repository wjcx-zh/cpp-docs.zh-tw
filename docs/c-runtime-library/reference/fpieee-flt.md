---
title: _fpieee_flt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da55d2940f38a90dfa5c69d71d394e865bb3b4c0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*處理常式*<br/>
使用者之 IEEE 設陷處理常式的指標。

## <a name="return-value"></a>傳回值

傳回值 **_fpieee_flt**是所傳回的值*處理常式*。 因此，IEEE 篩選常式可能會用於結構化例外狀況處理 (SEH) 機制的 except 子句。

## <a name="remarks"></a>備註

**_Fpieee_flt**函式會叫用 IEEE 浮點例外狀況的使用者定義的設陷處理常式，並提供所有的相關資訊。 此常式作為 SEH 機制中的例外狀況篩選，可在必要時叫用您自己的 IEEE 例外狀況處理常式。

**_FPIEEE_RECORD** Fpieee.h 中, 定義的結構包含 IEEE 浮點例外狀況的相關資訊。 此結構會傳遞至使用者定義的設陷處理常式 **_fpieee_flt**。

|_FPIEEE_RECORD 欄位|描述|
|----------------------------|-----------------|
|**RoundingMode**<br/>**整數位數**|這些**不帶正負號** **int**欄位包含環境的相關資訊浮點數時，發生例外狀況。|
|**作業**|這**不帶正負號** **int**欄位指出造成陷阱作業的類型。 如果型別比較 (**_FpCodeCompare**)，您可以提供其中一個特殊 **_FPIEEE_COMPARE_RESULT**中的值 （如定義 Fpieee.h） **Result.Value**欄位。 轉換類型 (**_FpCodeConvert**) 表示的浮點數轉換作業期間發生的設陷。 您可以查看**Operand1**和**結果**來判斷正在嘗試的轉換類型的類型。|
|**operand1**<br/>**operand2**<br/>**結果**|這些 **_FPIEEE_VALUE**結構表示的類型和建議的結果和運算元的值。 每個結構包含下列欄位：<br /><br /> **OperandValid** -旗標，指出回應的值是否有效。<br />**格式**-對應值的資料類型。 即使對應的值無效，還是可能會傳回格式類型。<br />**值**-結果或運算元的資料值。|
|**可能的原因**<br/>**啟用**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS**包含一個位元欄位，每個類型的浮動點例外狀況。 這些欄位與用來遮罩提供給 [_controlfp](control87-controlfp-control87-2.md) 之例外狀況的引數之間具有對應關係。 每個位元的確切意義取決於內容︰<br /><br /> **可能的原因**-每一組位元表示引發特定例外狀況。<br />**啟用**-每一組位元表示特定的例外狀況是目前未遮罩。<br />**狀態**-每一組位元表示特定的例外狀況是目前有擱置中。 這包括不因為它們已由遮罩已引發的例外狀況 **_controlfp**。|

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
