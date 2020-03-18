---
title: _ASSERT、_ASSERTE、_ASSERT_EXPR 巨集
ms.date: 11/04/2016
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: 26a1439e4de8824edd11af1afd455d2b2c31c088
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443084"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集

評估運算式，並在結果為**False**時產生一個 debug 報告（僅限 debug 版本）。

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

**_ASSERT_EXPR**、 **_ASSERT**和 **_ASSERTE**宏為應用程式提供了一種全新且簡單的機制，可在偵錯工具期間檢查假設。 這些巨集不需要括在 `#ifdef` 陳述式中，以避免在應用程式的零售組建中被呼叫，所以極具彈性。 此彈性來自使用 [_DEBUG](../../c-runtime-library/debug.md) 巨集。 只有在編譯時期定義 **_DEBUG**時，才可以使用 **_ASSERT_EXPR**、 **_ASSERT**和 **_ASSERTE** 。 未定義 **_DEBUG**時，會在前置處理期間移除對這些宏的呼叫。

**_ASSERT_EXPR**、 **_ASSERT**和 **_ASSERTE**評估其*booleanExpression*引數，而當結果為**false** （0）時，則會列印診斷訊息，並呼叫[_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)來產生「偵錯工具」報告。 **_ASSERT**宏會列印簡單的診斷訊息， **_ASSERTE**在訊息中包含失敗運算式的字串標記法，而 **_ASSERT_EXPR**在診斷訊息中包含*訊息*字串。 當*booleanExpression*評估為非零時，這些宏不會執行任何動作。

**_ASSERT_EXPR**、 **_ASSERT**和 **_ASSERTE**會叫用 **_CrtDbgReportW**，這會導致所有輸出都是寬字元。 **_ASSERTE**在*booleanExpression*中適當列印 unicode 字元，而 **_ASSERT_EXPR**會在*訊息*中列印 unicode 字元。

因為 **_ASSERTE**宏會指定失敗的運算式，而 **_ASSERT_EXPR**可讓您在產生的報告中指定訊息，所以使用者可以識別問題，而不需要參考應用程式的原始程式碼。 不過，缺點在於，每個 **_ASSERT_EXPR**列印的*訊息*，以及由 **_ASSERTE**所評估的每個運算式，都是以字串常數的形式包含在應用程式的輸出（debug 版本）檔案中。 因此，如果對 **_ASSERT_EXPR**或 **_ASSERTE**進行大量呼叫，這些運算式可能會大幅增加輸出檔案的大小。

除非您另外使用 [_CrtSetReportMode](crtsetreportmode.md) 與 [_CrtSetReportFile](crtsetreportfile.md) 函式進行指定，否則出現在相快顯對話方塊方塊中的訊息等同於設定：

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW**會根據目前的報表模式或針對 **_CRT_ASSERT**報表類型所定義的檔案，產生 debug 報表並決定其目的地或目的地。 判斷提示失敗及錯誤預設會導向到偵錯訊息視窗。 [_CrtSetReportMode](crtsetreportmode.md) 及 [_CrtSetReportFile](crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。

當目的地是 [偵錯工具] 訊息視窗，且使用者按一下 [**重試**] 按鈕時， **_CrtDbgReportW**會傳回1，使 **_ASSERT_EXPR**， **_ASSERT**和 **_ASSERTE**宏啟動偵錯工具，前提是已啟用即時（JIT）偵錯工具。

如需報告程序的詳細資訊，請參閱 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 函式。 如需如何解決判斷提示失敗，以及如何使用這些巨集作為偵錯之錯誤處理機制的詳細資訊，請參閱 [使用的巨集來進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。

除了 **_ASSERT**宏之外， [ASSERT](assert-macro-assert-wassert.md)宏還可以用來驗證程式邏輯。 此巨集可在偵錯版與發行版的程式庫中使用。 [_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md) 偵錯巨集也可用於產生偵錯報表，但其無法評估運算式。 **_RPT**宏會產生簡單的報表。 **_RPTF**宏包括原始程式檔，以及在產生的報表中呼叫報表宏的行號。 這些宏的寬字元版本可供使用（ **_RPTW**、 **_RPTFW**）。 寬字元版本與窄字元版本相同，但所有字串參數及輸出皆會使用寬字元字串。

雖然 **_ASSERT_EXPR**、 **_ASSERT**和 **_ASSERTE**都是宏，而且可以藉由包含 \<crtdbg.h 裡來提供，但當定義 **>** 時，應用程式必須與 C 執行時間程式庫的 debug 版本連結，因為這些宏會呼叫其他執行時間函式。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_ASSERT_EXPR**、 **_ASSERT**、 **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>範例

在此程式中，會對 **_ASSERT**進行呼叫，並 **_ASSERTE**宏來測試 `string1 == string2`的條件。 若該條件失敗時，這些巨集便會列印診斷訊息。 此程式中也會執行 **_RPT**和 **_RPTF**宏群組，做為**printf**函式的替代方案。

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
