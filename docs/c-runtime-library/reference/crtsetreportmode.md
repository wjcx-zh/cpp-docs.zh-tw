---
title: _CrtSetReportMode
ms.date: 11/04/2016
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 2096d39a8ba316fc76c97517a16e34231940e7f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335291"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

指定目的地或所產生的特定報表類型目的地 **_CrtDbgReport**和 呼叫的任何巨集[_CrtDbgReport、 _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)，例如[_ASSERT、 _ASSERTE、_ASSERT_EXPR 巨集](assert-asserte-assert-expr-macros.md)， [_ASSERT、 _ASSERTE、 _ASSERT_EXPR 巨集](assert-asserte-assert-expr-macros.md)， [_RPT、 _RPTF、 _RPTW、 _RPTFW 巨集](rpt-rptf-rptw-rptfw-macros.md)，和[_RPT、 _RPTF、 _RPTW、 _RPTFW 巨集](rpt-rptf-rptw-rptfw-macros.md)（僅限偵錯版本）。

## <a name="syntax"></a>語法

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表類型： **_CRT_WARN**， **_CRT_ERROR**，並 **_CRT_ASSERT**。

*reportMode*<br/>
新報表模式或模式*reportType*。

## <a name="return-value"></a>傳回值

成功完成時， **_CrtSetReportMode**中所指定的報表類型，傳回的先前報表模式*reportType*。 如果無效的值會當做傳入*reportType*或指定無效的模式*reportMode*， **_CrtSetReportMode**叫用無效參數處理常式做為中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**並傳回-1。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_CrtSetReportMode**指定的輸出目的地 **_CrtDbgReport**。 因為巨集會[_ASSERT](assert-asserte-assert-expr-macros.md)， [_ASSERTE](assert-asserte-assert-expr-macros.md)， [_RPT](rpt-rptf-rptw-rptfw-macros.md)，以及[_RPTF](rpt-rptf-rptw-rptfw-macros.md)呼叫 **_CrtDbgReport**， **_CrtSetReportMode**指定使用這些巨集所指定文字的輸出目的地。

當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtSetReportMode**會在前置處理期間移除。

如果您不能呼叫 **_CrtSetReportMode**若要定義輸出目的地的訊息，則下列預設值為作用中：

- 判斷提示失敗及錯誤會導向到偵錯訊息視窗。

- Windows 應用程式的警告會傳送至偵錯工具的輸出視窗。

- 主控台應用程式的警告不會顯示。

下表列出 Crtdbg.h 中定義的報表類型。

|報表類型|描述|
|-----------------|-----------------|
|**_CRT_WARN**|不需要立即注意的警告、訊息和資訊。|
|**_CRT_ERROR**|錯誤、無法復原的問題和需要立即注意的問題。|
|**_CRT_ASSERT**|判斷提示失敗 (判斷提示運算式會評估得出**FALSE**)。|

**_CrtSetReportMode**函式會指派中指定的新報表模式*reportMode*中指定的報表類型*reportType* ，並傳回先前定義報表模式*reportType*。 下表列出可用的選項，如*reportMode*和所產生的行為 **_CrtDbgReport**。 這些選項在 Crtdbg.h 中定義為位元旗標。

|報表模式|_CrtDbgReport 行為|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|將訊息寫入至偵錯工具的輸出視窗。|
|**_CRTDBG_MODE_FILE**|將訊息寫入至使用者提供的檔案控制代碼。 應呼叫 [_CrtSetReportFile](crtsetreportfile.md)，以定義特定檔案或資料流作為目的地使用。|
|**_CRTDBG_MODE_WNDW**|建立訊息方塊，顯示的訊息，連同[中止](abort.md)，**重試一次**，並**忽略**按鈕。|
|**_CRTDBG_REPORT_MODE**|傳回*reportMode*指定*reportType*:<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

每個報表類型可使用一個、兩個或三個模式進行報告，或完全不使用任何模式。 因此，您可以為單一報表類型定義多個目的地。 例如，下列程式碼片段會導致要傳送至這兩個偵錯訊息視窗和判斷提示失敗**stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

此外，可個別控制每個報表類型的一或多個報告模式。 比方說，就可以指定*reportType*的 **_CRT_WARN**會傳送至輸出偵錯字串，而 **_CRT_ASSERT**會使用偵錯訊息視窗顯示傳送至**stderr**，如先前所示。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 偵錯版本[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)只。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
