---
title: _RPT、_RPTF、_RPTW、_RPTFW 巨集
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
ms.openlocfilehash: 61748cca2cdfcc2d72b6943bfeedd9597009e20b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357488"
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 巨集

產生偵錯報表，以追蹤應用程式進度 (僅限偵錯版本)。 請注意， *n*指定的引數數目*args*而且可以是 0、 1、 2、 3、 4 或 5。

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
報表類型： **_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**。

*格式*<br/>
用於建立使用者訊息的格式控制字串。

*args*<br/>
所使用的替換引數*格式*。

## <a name="remarks"></a>備註

所有這些巨集都會*reportType*並*格式*參數。 此外，它們也可能最多接受四個其他引數，以附加至巨集名稱的號碼表示。 比方說， **_RPT0**並 **_RPTF0**採取任何額外的引數 **_RPT1**並 **_RPTF1**採取*arg1*， **_RPT2**並 **_RPTF2**採取*arg1*並**arg2**，依此類推。

**_RPT**並 **_RPTF**巨集是類似[printf](printf-printf-l-wprintf-wprintf-l.md)函式，因為它們可以用來追蹤在偵錯程序期間的應用程式的進度。 不過，這些巨集是比更有彈性**printf**因為它們不需要括住 **#ifdef**陳述式，以防止被呼叫的應用程式的零售組建中。 利用這種彈性來達成[_DEBUG](../../c-runtime-library/debug.md)巨集; **_RPT**並 **_RPTF**巨集時，就只能使用 **_DEBUG**旗標定義。 當 **_DEBUG**是未定義，這些巨集的呼叫會移除在前置處理期間。

**_RPTW**並 **_RPTFW**巨集是這些巨集的寬字元版本。 它們就像是**wprintf**並接受寬字元字串做為引數。

**_RPT**巨集會呼叫[_CrtDbgReport](crtdbgreport-crtdbgreportw.md)函式來產生含使用者訊息的偵錯報表。 **_RPTW**巨集會呼叫 **_CrtDbgReportW**函式來產生具有寬字元相同的報表。 **_RPTF**並 **_RPTFW**巨集建立偵錯報表，報表巨集呼叫，除了使用者訊息的來源檔案和行號。 使用者會建立訊息以替代**arg**[*n*] 引數*格式*字串，使用相同的規則所定義[printf](printf-printf-l-wprintf-wprintf-l.md)函式。

**_CrtDbgReport**或是 **_CrtDbgReportW**會產生偵錯報表，並判斷其目的地根據目前的報表模式和針對檔案群組定義*reportType*。 [_CrtSetReportMode](crtsetreportmode.md) 及 [_CrtSetReportFile](crtsetreportfile.md) 函式可用於定義每個報表類型的目的地。

如果 **_RPT**呼叫巨集及兩者皆無 **_CrtSetReportMode**也 **_CrtSetReportFile**已呼叫，會顯示訊息，如下所示。

|報表類型|輸出目的地|
|-----------------|------------------------|
|**_CRT_WARN**|不會顯示警告文字。|
|**_CRT_ERROR**|快顯視窗。 與指定 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 時相同。|
|**_CRT_ASSERT**|與相同 **_CRT_ERROR**。|

當目的地是偵錯訊息視窗，且使用者選擇**重試** 按鈕， **_CrtDbgReport**或是 **_CrtDbgReportW**傳回 1，讓這些巨集啟動偵錯工具，假設在 just-in-time (JIT) 偵錯已啟用。 如需如何使用這些巨集作為偵錯錯誤處理機制的詳細資訊，請參閱[使用巨集進行驗證和報告](/visualstudio/debugger/macros-for-reporting)。

有兩個其他巨集可產生偵錯報表。 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集會產生報表，但僅限其運算式引數評估為 FALSE 時。 [_ASSERTE](assert-asserte-assert-expr-macros.md)完全相同 **_ASSERT**，但產生的報告中會包含失敗的運算式。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-----------|---------------------|
|**_RPT** macros|\<crtdbg.h>|
|**_RPTF** macros|\<crtdbg.h>|
|**_RPTW** macros|\<crtdbg.h>|
|**_RPTFW** macros|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

雖然這些都是巨集，並且可透過加入 Crtdbg.h 來取得，但因為這些巨集會呼叫其他執行階段函式，所以應用程式必須連結其中一個偵錯程式庫。

## <a name="example"></a>範例

請參閱 [_ASSERT](assert-asserte-assert-expr-macros.md) 主題中的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
