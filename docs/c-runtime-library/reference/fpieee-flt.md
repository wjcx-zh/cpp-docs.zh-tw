---
title: "_fpieee_flt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fpieee_flt"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fpieee_flt"
  - "_fpieee_flt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fpieee_flt 函式"
  - "例外狀況處理, 浮點"
  - "浮點例外狀況處理"
  - "fpieee_flt 函式"
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _fpieee_flt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

叫用 IEEE 浮點例外狀況中使用者定義的錯誤處理常式。  
  
## 語法  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### 參數  
 `excCode`  
 例外狀況代碼。  
  
 `excInfo`  
 對 Windows NT 例外狀況資訊結構的指標。  
  
 `handler`  
 對使用者的 IEEE 攔截處理常式的指標。  
  
## 傳回值  
 `_fpieee_flt` 的傳回值是 `handler`所傳回的值。  因此，IEEE 篩選常式可能被使用，除了一個結構化例外狀況處理 \(SEH\) 機制的子句。  
  
## 備註  
 `_fpieee_flt` 函式會叫用 IEEE 浮點例外狀況中的使用者定義的攔截處理常式並提供所有相關資訊。  這個常式做為 SEH 機制的例外狀況篩選條件，需要時則叫用您的 IEEE 例外處理常式。  
  
 `_FPIEEE_RECORD` 結構，定義在 Fpieee.h，包含 IEEE 浮點例外狀況的相關資訊。  這個結構會藉由 `_fpieee_flt`傳遞至使用者定義的攔截處理常式。  
  
|\_FPIEEE\_RECORD 欄位|描述|  
|-------------------------|--------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|在例外狀況發生時，這些欄位會包含浮點數環境的相關資訊。|  
|`unsigned int Operation`|表示導致這個攔截的作業類型。  如果型別是比較 \(`_FpCodeCompare`\)，您可以提供一個特殊的 `_FPIEEE_COMPARE_RESULT` 值 \(如 Fpieee.h 定義\) 中的 `Result.Value` 欄位。  轉換型別 \(`_FpCodeConvert`\) 表示這個攔截在浮點轉換作業時發生。  您可以仔細留意 `Operand1` 和 `Result` 型別來判斷嘗試轉換的型別。|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|這些結構表示提出結果和運算元的型別和值:<br /><br /> `OperandValid` 旗標表示回應的值是否有效。<br /><br /> `Format` 對應於的值的資料型別。  格式類型可能會回傳，即使對應的值無效。<br /><br /> `Value` 結果或運算元資料值。|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|\_FPIEEE\_EXCEPTION\_FLAGS 包含每種浮點例外狀況型別的位元欄位。<br /><br /> 在這些欄位和用於引數之間提供給 [\_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)的遮罩例外狀況的對應。<br /><br /> 每個位元的確切意義取決於內容:<br /><br /> `Cause` 每個設定位元表示引發的特定例外狀況。<br /><br /> `Enable` 每個設定位元表示特定例外狀況目前被揭露。<br /><br /> `Status` 每個設定位元表示特定例外狀況目前是未定的。  這包括未引發的例外狀況，因為被 `_controlfp`遮罩。|  
  
 當您啟用時，停用的未定的例外狀況會被引發。  在使用 `_fpieee_flt` 做為例外狀況篩選條件時，這可能會產生未定義的行為。  永遠在啟用浮點例外狀況之前呼叫 [\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md) 。  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`_fpieee_flt`|\<fpieee.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
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
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)