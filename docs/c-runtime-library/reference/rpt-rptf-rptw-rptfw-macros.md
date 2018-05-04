---
title: _RPT、_RPTF、_RPTW、_RPTFW 巨集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a53a069138b4e54988be008917e5ca2b24fa0a6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 巨集

產生偵錯報表，以追蹤應用程式進度 (僅限偵錯版本)。 請注意， *n*指定之引數中*args*而且可以是 0、 1、 2、 3、 4 或 5。

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

*reportType*報告類型： **_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**。

*格式*用來建立使用者訊息的格式控制字串。

*引數*替換引數使用*格式*。

## <a name="remarks"></a>備註

所有這些巨集接受*reportType*和*格式*參數。 此外，它們也可能最多接受四個其他引數，以附加至巨集名稱的號碼表示。 例如， **_RPT0**和 **_RPTF0**採取任何額外的引數， **_RPT1**和 **_RPTF1**採取*arg1*， **_RPT2**和 **_RPTF2**採取*arg1*和**arg2**，依此類推。

**_RPT**和 **_RPTF**巨集是類似於[printf](printf-printf-l-wprintf-wprintf-l.md)函式，因為它們可以用來追蹤在偵錯的程序期間的應用程式的進度。 不過，這些巨集是比更有彈性**printf**因為它們不需要括住 **#ifdef**在零售組建的應用程式中的陳述式，以防止被呼叫。 這種彈性達成方式是使用[_DEBUG](../../c-runtime-library/debug.md)巨集; **_RPT**和 **_RPTF**巨集時，就只能使用 **_DEBUG**旗標定義。 當 **_DEBUG**是未定義時，這些巨集的呼叫會移除在前置處理期間。

**_RPTW**和 **_RPTFW**巨集是寬字元版本，這些巨集。 它們就像是**wprintf**並採取寬字元字串做為引數。

**_RPT**巨集呼叫[_CrtDbgReport](crtdbgreport-crtdbgreportw.md)函數，以產生偵錯報表的使用者訊息。 **_RPTW**巨集呼叫 **_CrtDbgReportW**函式來產生相同的報表與寬字元。 **_RPTF**和 **_RPTFW**巨集建立偵錯報表，報表巨集呼叫，除了使用者訊息的來源檔案和行號。 使用者訊息由取代**arg**[*n*] 引數到*格式*字串所定義的相同規則[printf](printf-printf-l-wprintf-wprintf-l.md)函式。

**_CrtDbgReport**或 **_CrtDbgReportW**會產生偵錯報表，並判斷其目的地根據目前的報表模式和針對檔案群組定義*reportType*。 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。

如果 **_RPT**呼叫巨集並沒有 **_CrtSetReportMode**也 **_CrtSetReportFile**已呼叫，會顯示訊息，如下所示。

|報表類型|輸出目的地|
|-----------------|------------------------|
|**_CRT_WARN**|不會顯示警告文字。|
|**_CRT_ERROR**|快顯視窗。 與指定 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 時相同。|
|**_CRT_ASSERT**|與相同 **_CRT_ERROR**。|

當目的地是偵錯訊息視窗，使用者選擇**重試** 按鈕， **_CrtDbgReport**或 **_CrtDbgReportW**傳回 1，導致啟動這些巨集偵錯工具，假設在 just-in-time (JIT) 偵錯已啟用。 如需如何使用這些巨集作為偵錯錯誤處理機制的詳細資訊，請參閱[使用巨集進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。

有兩個其他巨集可產生偵錯報表。 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集會產生報表，但僅限其運算式引數評估為 FALSE 時。 [_ASSERTE](assert-asserte-assert-expr-macros.md)是一樣 **_ASSERT**，但產生的報告中包含失敗的運算式。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_RPT**巨集|\<crtdbg.h>|
|**_RPTF**巨集|\<crtdbg.h>|
|**_RPTW**巨集|\<crtdbg.h>|
|**_RPTFW**巨集|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

雖然這些都是巨集，並且可透過加入 Crtdbg.h 來取得，但因為這些巨集會呼叫其他執行階段函式，所以應用程式必須連結其中一個偵錯程式庫。

## <a name="example"></a>範例

請參閱 [_ASSERT](assert-asserte-assert-expr-macros.md) 主題中的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
