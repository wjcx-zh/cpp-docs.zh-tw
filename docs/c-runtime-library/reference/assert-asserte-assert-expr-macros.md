---
title: "_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: a0d8c456f20fc048bab91ec5bc9e1639b93adb6d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集
評估運算式，並在結果為 `False` 時產生偵錯報告 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
_ASSERT_EXPR(  
   booleanExpression,  
   message  
);  
_ASSERT(   
   booleanExpression   
);  
_ASSERTE(   
   booleanExpression   
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `booleanExpression`  
 純量運算式 (包括指標運算式) 會評估為非零值 (true) 或 0 (false)。  
  
 `message`  
 顯示在報表中的寬字串。  
  
## <a name="remarks"></a>備註  
 `_ASSERT_EXPR`, 、 `_ASSERT` 及 `_ASSERTE` 巨集可以讓您在偵錯程序期間，利用清楚簡單的機制來檢查假設。 這些巨集不需要括在 `#ifdef` 陳述式中，以避免在應用程式的零售組建中被呼叫，所以極具彈性。 此彈性來自使用 [_DEBUG](../../c-runtime-library/debug.md) 巨集。 僅當`_ASSERT_EXPR`, `_ASSERT` 、 `_ASSERTE` 及 `_DEBUG` 。 若未定義 `_DEBUG` ，將會在前置處理期間移除對這些巨集的呼叫。  
  
 `_ASSERT_EXPR`, `_ASSERT` 及 `_ASSERTE` 會在結果 `booleanExpression` (0) 時，評估其 `false` 引數，其會列印診斷訊息並呼叫 [_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) ，以產生偵錯報表。 `_ASSERT` 巨集會列印簡單的診斷訊息；  `_ASSERTE` 會在訊息中加入失敗運算式的字串表示法； `_ASSERT_EXPR` 會在診斷訊息中加入 `message` 字串。 當 `booleanExpression` 評估為非零值時，這些巨集不會執行任何動作。  
  
 `_ASSERT_EXPR`, `_ASSERT` 及 `_ASSERTE` 會叫用 `_CrtDbgReportW`，讓所有的輸出都呈現寬字元。 `_ASSERTE` 會正確地列印 `booleanExpression` 中的 Unicode 字元，而 `_ASSERT_EXPR` 則會列印 `message`中的 Unicode 字元。  
  
 因為 `_ASSERTE` 巨集會指定失敗的運算式，而 `_ASSERT_EXPR` 則可讓您指定所產生之報表中的訊息，所以使用者無須參考應用程式的原始程式碼，就能找出問題。 但其缺點在於，每一個由 `message` 所列印的 `_ASSERT_EXPR` 及每一個由 `_ASSERTE` 評估的運算式都會以字串常數形式包含在您應用程式的輸出 (偵錯版本) 檔案中。 因此，當對 `_ASSERT_EXPR` 或 `_ASSERTE`的呼叫十分大量時，這些運算式可能會讓您的輸出檔案大小大幅增大。  
  
 除非您另外使用 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 與 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函式進行指定，否則出現在相快顯對話方塊方塊中的訊息等同於設定：  
  
`_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);`  
  
 `_CrtDbgReportW` 依據目前的報表模式及為 `_CRT_ASSERT` 報告類型所定義的檔案產生偵錯報表，並判斷其目的地。 判斷提示失敗及錯誤預設會導向到偵錯訊息視窗。 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 及 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。  
  
 當目的地為偵錯訊息視窗，而使用者按一下 [重試]  按鈕時，若已有啟用 Just-in-Time (JIT) 偵錯， `_CrtDbgReportW` 會傳回 1，讓 `_ASSERT_EXPR`、 `_ASSERT` 及 `_ASSERTE` 巨集啟動偵錯程式。  
  
 如需報告程序的詳細資訊，請參閱 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 函式。 如需如何解決判斷提示失敗，以及如何使用這些巨集作為偵錯之錯誤處理機制的詳細資訊，請參閱 [使用的巨集來進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。  
  
 除了 `_ASSERT` 巨集之外， [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md) 巨集還可用於驗證程式邏輯。 此巨集可在偵錯版與發行版的程式庫中使用。 [_RPT、_RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 偵錯巨集也可用於產生偵錯報表，但其無法評估運算式。 `_RPT` 巨集會產生簡單的報表。 `_RPTF` 巨集會在所產生的報表中，加入來源檔案及報表巨集呼叫所在的行號。 此外也提供這些巨集的寬字元版本 (`_RPTWn`、 `_RPTFWn`)。 寬字元版本與窄字元版本相同，但所有字串參數及輸出皆會使用寬字元字串。  
  
 雖然 `_ASSERT_EXPR`、`_ASSERT` 及 `_ASSERTE` 均為巨集，並可透過加入 \<crtdbg.h> 的方式使用，但在定義了 `_DEBUG` 的情況下，因為這些巨集會呼叫其他執行階段函式，所以應用程式仍須連結偵錯版的 C 執行階段程式庫。  
  
## <a name="requirements"></a>需求  
  
|巨集|必要的標頭|  
|-----------|---------------------|  
|`_ASSERT_EXPR`,                  `_ASSERT`, `_ASSERTE`|\<crtdbg.h>|  
  
## <a name="example"></a>範例  
 此程式會呼叫 `_ASSERT` 及 `_ASSERTE` 巨集來測試條件 `string1 == string2`。 若該條件失敗時，這些巨集便會列印診斷訊息。 此程式中也會執行 `_RPTn` 與 `_RPTFn` 巨集群組，作為 `printf` 函式的替代函式。  
  
```C  
// crt_ASSERT_macro.c  
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug  
//  
// This program uses the _ASSERT and _ASSERTE debugging macros.  
//  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main()  
{  
   char *p1, *p2;  
  
   // The Reporting Mode and File must be specified  
   // before generating a debug report via an assert  
   // or report macro.  
   // This program sends all report types to STDOUT.  
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);  
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);  
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);  
  
   // Allocate and assign the pointer variables.  
   p1 = (char *)malloc(10);  
   strcpy_s(p1, 10, "I am p1");  
   p2 = (char *)malloc(10);  
   strcpy_s(p2, 10, "I am p2");  
  
   // Use the report macros as a debugging  
   // warning mechanism, similar to printf.  
   // Use the assert macros to check if the   
   // p1 and p2 variables are equivalent.  
   // If the expression fails, _ASSERTE will  
   // include a string representation of the  
   // failed expression in the report.  
   // _ASSERT does not include the  
   // expression in the generated report.  
   _RPT0(_CRT_WARN,  
       "Use the assert macros to evaluate the expression p1 == p2.\n");  
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);  
   _ASSERT(p1 == p2);  
  
   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",  
          p1, p2);  
   _ASSERTE(p1 == p2);  
  
   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);  
  
   free(p2);  
   free(p1);  
  
   return 0;  
}  
```  
  
```Output  
Use the assert macros to evaluate the expression p1 == p2.  
crt_ASSERT_macro.c(54) :   
 Will _ASSERT find 'I am p1' == 'I am p2' ?  
crt_ASSERT_macro.c(55) : Assertion failed!  
crt_ASSERT_macro.c(58) :   
  
 Will _ASSERTE find 'I am p1' == 'I am p2' ?  
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2  
'I am p1' != 'I am p2'  
```  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [assert 巨集、_assert、_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_RPT、_RPTF、_RPTW、_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)
