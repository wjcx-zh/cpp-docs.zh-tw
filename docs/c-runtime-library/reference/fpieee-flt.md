---
title: _fpieee_flt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c2e9f909f3e7e778845d8fefebe5d8b1604af489
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="fpieeeflt"></a>_fpieee_flt
針對 IEEE 浮點例外狀況叫用使用者定義的設陷處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### <a name="parameters"></a>參數  
 `excCode`  
 例外狀況代碼。  
  
 `excInfo`  
 Windows NT 例外狀況資訊結構的指標。  
  
 `handler`  
 使用者之 IEEE 設陷處理常式的指標。  
  
## <a name="return-value"></a>傳回值  
 `_fpieee_flt` 的傳回值是 `handler` 所傳回的值。 因此，IEEE 篩選常式可能會用於結構化例外狀況處理 (SEH) 機制的 except 子句。  
  
## <a name="remarks"></a>備註  
 `_fpieee_flt` 函式會針對 IEEE 浮點例外狀況叫用使用者定義的設陷處理常式，並將所有相關資訊提供給它。 此常式作為 SEH 機制中的例外狀況篩選，可在必要時叫用您自己的 IEEE 例外狀況處理常式。  
  
 Fpieee.h 中所定義的 `_FPIEEE_RECORD` 結構包含 IEEE 浮點例外狀況的相關資訊。 此結構會透過 `_fpieee_flt` 傳遞至使用者定義的設陷處理常式。  
  
|_FPIEEE_RECORD 欄位|描述|  
|----------------------------|-----------------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|這些欄位包含發生例外狀況時的浮點環境相關資訊。|  
|`unsigned int Operation`|表示已導致陷阱的作業類型。 如果類型是比較 (`_FpCodeCompare`)，則可以在 `Result.Value` 欄位中提供 Fpieee.h 中所定義的其中一個特殊 `_FPIEEE_COMPARE_RESULT` 值。 轉換類型 (`_FpCodeConvert`) 表示設陷發生在浮點轉換作業期間。 您可以查看 `Operand1` 和 `Result` 類型，以判斷正在嘗試之轉換的類型。|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|這些結構表示所建議結果和運算元的類型和值︰<br /><br /> `OperandValid` 旗標，指出回應的值是否有效。<br /><br /> `Format` 對應值的資料類型。 即使對應的值無效，還是可能會傳回格式類型。<br /><br /> `Value` 結果或運算元資料值。|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|_FPIEEE_EXCEPTION_FLAGS 會為每個浮點例外狀況類型包含一個位元欄位。<br /><br /> 這些欄位與用來遮罩提供給 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 之例外狀況的引數之間具有對應關係。<br /><br /> 每個位元的確切意義取決於內容︰<br /><br /> `Cause` 每個設定的位元都表示已引發的特定例外狀況。<br /><br /> `Enable` 每個設定的位元都表示目前取消遮罩特定例外狀況。<br /><br /> `Status` 每個設定的位元都表示特定例外狀況目前暫止。 這包括因透過 `_controlfp` 進行遮罩而尚未引發的例外狀況。|  
  
 啟用暫止例外狀況時，會引發停用的暫止例外狀況。 這可能會在使用 `_fpieee_flt` 作為例外狀況篩選時導致未定義的行為。 一律在啟用浮點例外狀況之前呼叫 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_fpieee_flt`|\<fpieee.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)
