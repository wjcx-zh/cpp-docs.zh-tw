---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938455"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

指定 **_CrtDbgReport**所產生之特定報表類型的目的地或目的地，以及呼叫[_CrtDbgReport，_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)的任何宏，例如[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)、 [_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)、 [_RPT、_RPTF、_RPTW、_RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)和[_RPT、](rpt-rptf-rptw-rptfw-macros.md) _RPTF、_RPTW、_RPTFW 宏（僅限 debug 版本）。

## <a name="syntax"></a>語法

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表類型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*reportMode*<br/>
新的報表模式或*reportType*模式。

## <a name="return-value"></a>傳回值

成功完成時， **_CrtSetReportMode**會傳回*reportType*中指定之報表類型的先前報表模式或模式。 如果將不正確值當做*reportType*傳入，或為*reportMode*指定了不正確模式，則 **_CrtSetReportMode**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回-1。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_CrtSetReportMode**指定 **_CrtDbgReport**的輸出目的地。 由於宏[_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md)、 [_RPT](rpt-rptf-rptw-rptfw-macros.md)和[_RPTF](rpt-rptf-rptw-rptfw-macros.md)呼叫 **_CrtDbgReport**， **_CrtSetReportMode**會指定以這些宏指定之文字的輸出目的地。

未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtSetReportMode**的呼叫。

如果您未呼叫 **_CrtSetReportMode**來定義訊息的輸出目的地，則下列預設值會生效：

- 判斷提示失敗及錯誤會導向到偵錯訊息視窗。

- Windows 應用程式的警告會傳送至偵錯工具的輸出視窗。

- 主控台應用程式的警告不會顯示。

下表列出 Crtdbg.h 中定義的報表類型。

|報表類型|描述|
|-----------------|-----------------|
|**_CRT_WARN**|不需要立即注意的警告、訊息和資訊。|
|**_CRT_ERROR**|錯誤、無法復原的問題和需要立即注意的問題。|
|**_CRT_ASSERT**|判斷提示失敗（評估為**FALSE**的宣告運算式）。|

**_CrtSetReportMode**函數會將*reportMode*中指定的新報表模式指派給*reportType*中指定的報表類型，並傳回先前為*reportType*定義的報表模式。 下表列出*reportMode*的可用選項，以及 **_CrtDbgReport**的結果行為。 這些選項在 Crtdbg.h 中定義為位元旗標。

|報表模式|_CrtDbgReport 行為|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|將訊息寫入至偵錯工具的輸出視窗。|
|**_CRTDBG_MODE_FILE**|將訊息寫入至使用者提供的檔案控制代碼。 應呼叫 [_CrtSetReportFile](crtsetreportfile.md)，以定義特定檔案或資料流作為目的地使用。|
|**_CRTDBG_MODE_WNDW**|建立訊息方塊，以顯示訊息和 [[中止](abort.md)]、[**重試**] 和 [**忽略**] 按鈕。|
|**_CRTDBG_REPORT_MODE**|傳回指定之*reportType*的*reportMode* ：<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

每個報表類型可使用一個、兩個或三個模式進行報告，或完全不使用任何模式。 因此，您可以為單一報表類型定義多個目的地。 例如，下列程式碼片段會導致判斷提示失敗同時傳送至 [偵錯工具] 視窗和**stderr**：

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

此外，可個別控制每個報表類型的一或多個報告模式。 例如，您可以指定將 **_CRT_WARN**的*reportType*傳送至輸出 Debug 字串，而 **_CRT_ASSERT**會使用 [debug] 訊息視窗來顯示並傳送至**stderr**（如先前所述）。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**僅限[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的 Debug 版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
