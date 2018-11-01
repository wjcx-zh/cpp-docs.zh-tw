---
title: _ASSERT、_ASSERTE、_ASSERT_EXPR 巨集
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: d2d83c3afa8e22c1f75480fe2afefa8bf68be858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598454"
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集

評估運算式，並產生偵錯報表，當結果為**False** （僅限偵錯版本）。

## <a name="syntax"></a>語法

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
純量運算式 (包括指標運算式) 會評估為非零值 (true) 或 0 (false)。

*message*<br/>
顯示在報表中的寬字串。

## <a name="remarks"></a>備註

**_ASSERT_EXPR**， **_ASSERT**並 **_ASSERTE**巨集提供清楚且簡單的機制，來偵錯程序期間檢查假設的應用程式。 這些巨集不需要括在 `#ifdef` 陳述式中，以避免在應用程式的零售組建中被呼叫，所以極具彈性。 此彈性來自使用 [_DEBUG](../../c-runtime-library/debug.md) 巨集。 **_ASSERT_EXPR**， **_ASSERT**並 **_ASSERTE**時，就只能使用 **_DEBUG**在編譯階段所定義。 當 **_DEBUG**是未定義，這些巨集的呼叫會移除在前置處理期間。

**_ASSERT_EXPR**， **_ASSERT**並 **_ASSERTE**評估其*booleanExpression*引數，而且結果會是當**false**(0)，其會列印診斷訊息並呼叫[_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)產生偵錯報表。 **_ASSERT**巨集會列印簡單的診斷訊息 **_ASSERTE**包含失敗的運算式的字串表示，在訊息中，並 **_ASSERT_EXPR**包含*訊息*診斷訊息中的字串。 這些巨集不執行任何動作時*booleanExpression*評估為非零值。

**_ASSERT_EXPR**， **_ASSERT**並 **_ASSERTE**叫用 **_CrtDbgReportW**，讓所有輸出都呈現寬字元。 **_ASSERTE**正確地列印中的 Unicode 字元*booleanExpression*並 **_ASSERT_EXPR**列印中的 Unicode 字元*訊息*。

因為 **_ASSERTE**巨集指定失敗的運算式，並 **_ASSERT_EXPR**可讓您指定產生的報表中的訊息，它們可讓使用者能夠找出問題，而不會參考應用程式來源程式碼。 不過，缺點在於，每一個*訊息*列印 **_ASSERT_EXPR**並評估每個運算式 **_ASSERTE**包含在輸出 （偵錯版本）您的應用程式，為字串常數的檔案。 因此，如果一大堆會呼叫 **_ASSERT_EXPR**或是 **_ASSERTE**，這些運算式會大幅增加您的輸出檔的大小。

除非您另外使用 [_CrtSetReportMode](crtsetreportmode.md) 與 [_CrtSetReportFile](crtsetreportfile.md) 函式進行指定，否則出現在相快顯對話方塊方塊中的訊息等同於設定：

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW**產生偵錯報表，並判斷其目的地，根據目前報表模式及定義的檔案 **_CRT_ASSERT**報表類型。 判斷提示失敗及錯誤預設會導向到偵錯訊息視窗。 [_CrtSetReportMode](crtsetreportmode.md) 及 [_CrtSetReportFile](crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。

如果目的地是偵錯訊息視窗，且使用者按下**重試** 按鈕， **_CrtDbgReportW**會傳回 1，造成 **_ASSERT_EXPR**， **_判斷提示**並 **_ASSERTE**巨集啟動偵錯工具，提供已啟用的 just-in-time (JIT) 偵錯。

如需報告程序的詳細資訊，請參閱 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 函式。 如需如何解決判斷提示失敗，以及如何使用這些巨集作為偵錯之錯誤處理機制的詳細資訊，請參閱 [使用的巨集來進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。

除了 **_ASSERT**巨集[assert](assert-macro-assert-wassert.md)巨集可以用來驗證程式邏輯。 此巨集可在偵錯版與發行版的程式庫中使用。 [_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md) 偵錯巨集也可用於產生偵錯報表，但其無法評估運算式。 **_RPT**巨集會產生簡單的報表。 **_RPTF**巨集產生的報表中包括報表巨集呼叫所在的來源檔案和行號。 這些巨集的寬字元版本可供使用 (**_RPTW**， **_RPTFW**)。 寬字元版本與窄字元版本相同，但所有字串參數及輸出皆會使用寬字元字串。

雖然 **_ASSERT_EXPR**， **_ASSERT**並 **_ASSERTE**均為巨集，而且可包含\<crtdbg.h >，應用程式必須連結偵錯C 執行階段程式庫版本時 **_DEBUG**定義，因為這些巨集會呼叫其他執行階段函式。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_ASSERT_EXPR**， **_ASSERT**， **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>範例

在此程式中，會呼叫 **_ASSERT**並 **_ASSERTE**巨集來測試條件`string1 == string2`。 若該條件失敗時，這些巨集便會列印診斷訊息。 **_RPT**並 **_RPTF**巨集的群組也運用在此程式中，做為替代**printf**函式。

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

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[assert 巨集、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
[_RPT、_RPTF、_RPTW、_RPTFW 巨集](rpt-rptf-rptw-rptfw-macros.md)<br/>
