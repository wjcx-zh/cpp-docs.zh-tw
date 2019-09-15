---
title: _RPT、_RPTF、_RPTW、_RPTFW 巨集
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 567fe0a68f5adad6f5d90ef3da9d673a75bb83a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949076"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 巨集

產生偵錯報表，以追蹤應用程式進度 (僅限偵錯版本)。 請注意， *n*會指定*args*中的引數數目，而且可以是0、1、2、3、4或5。

## <a name="syntax"></a>語法

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表類型： **_CRT_WARN**、 **_CRT_ERROR**或 **_CRT_ASSERT**。

*格式*<br/>
用於建立使用者訊息的格式控制字串。

*引數*<br/>
*格式*所使用的替代引數。

## <a name="remarks"></a>備註

所有這些宏都採用*reportType*和*format*參數。 此外，它們也可能最多接受四個其他引數，以附加至巨集名稱的號碼表示。 例如， **_RPT0**和 **_RPTF0**不接受其他引數、 **_RPT1**和 **_RPTF1**接受*arg1*、 **_RPT2**和 **_RPTF2**採用*arg1*和**arg2**等等。

**_RPT**和 **_RPTF**宏與[printf](printf-printf-l-wprintf-wprintf-l.md)函式類似，因為它們可以用來追蹤應用程式在偵錯工具中的進度。 不過，這些宏比**printf**更具彈性，因為它們不需要括在 **#ifdef**語句中，以避免在應用程式的零售組建中呼叫它們。 使用[_debug](../../c-runtime-library/debug.md)宏即可達到此彈性;只有在已定義 **_debug**旗標時，才可以使用 **_RPT**和 **_RPTF**宏。 未定義 **_debug**時，會在前置處理期間移除對這些宏的呼叫。

**_RPTW**和 **_RPTFW**宏是這些宏的寬字元版本。 它們就像是**wprintf** ，並採用寬字元字串做為引數。

**_RPT**宏會呼叫[_CrtDbgReport](crtdbgreport-crtdbgreportw.md)函式，以產生具有使用者訊息的 debug 報表。 **_RPTW**宏會呼叫 **_CrtDbgReportW**函數，以產生具有寬字元的相同報表。 除了使用者訊息以外， **_RPTF**和 **_RPTFW**宏還會使用原始程式檔和用來呼叫報表宏的行號來建立「偵錯工具」報表。 使用者訊息的建立方式是使用[printf](printf-printf-l-wprintf-wprintf-l.md)函數所定義的相同規則，將**arg**[*n*] 引數取代為*格式*字串。

**_CrtDbgReport**或 **_CrtDbgReportW**會產生 debug 報表，並根據目前的報表模式和針對*reportType*定義的檔案來決定其目的地。 [_CrtSetReportMode](crtsetreportmode.md) 及 [_CrtSetReportFile](crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。

如果呼叫 **_RPT**宏，但未呼叫 **_CrtSetReportMode**或 **_CrtSetReportFile** ，則會顯示如下的訊息。

|報表類型|輸出目的地|
|-----------------|------------------------|
|**_CRT_WARN**|不會顯示警告文字。|
|**_CRT_ERROR**|快顯視窗。 與指定 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 時相同。|
|**_CRT_ASSERT**|與 **_CRT_ERROR**相同。|

當目的地是一個 [偵錯工具] 訊息視窗，且使用者選擇 [**重試**] 按鈕時， **_CrtDbgReport**或 **_CrtDbgReportW**會傳回1，導致這些宏啟動偵錯工具，前提是已啟用即時（JIT）偵錯工具。 如需如何使用這些巨集作為偵錯錯誤處理機制的詳細資訊，請參閱[使用巨集進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。

有兩個其他巨集可產生偵錯報表。 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集會產生報表，但僅限其運算式引數評估為 FALSE 時。 [_ASSERTE](assert-asserte-assert-expr-macros.md)與 **_ASSERT**完全一樣，但會在產生的報告中包含失敗的運算式。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_RPT**宏|\<crtdbg.h>|
|**_RPTF**宏|\<crtdbg.h>|
|**_RPTW**宏|\<crtdbg.h>|
|**_RPTFW**宏|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

雖然這些都是巨集，並且可透過加入 Crtdbg.h 來取得，但因為這些巨集會呼叫其他執行階段函式，所以應用程式必須連結其中一個偵錯程式庫。

## <a name="example"></a>範例

請參閱 [_ASSERT](assert-asserte-assert-expr-macros.md) 主題中的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
