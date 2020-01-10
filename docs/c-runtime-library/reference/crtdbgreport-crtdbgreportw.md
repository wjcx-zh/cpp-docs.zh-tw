---
title: _CrtDbgReport、_CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 986777f755a749e858f7e51b5aa19f10090db13a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938843"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport、_CrtDbgReportW

產生具有偵錯訊息的報表，並將報表傳送至三個可能的目的地 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表類型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*filename*<br/>
發生判斷提示/報表之來源檔案的名稱指標，或為**Null**。

*linenumber*<br/>
發生判斷提示/報表之原始程式檔中的行號，或**為 Null**。

*moduleName*<br/>
發生判斷提示或報表之模組 (.exe 或 .dll) 的名稱的指標。

*格式*<br/>
用於建立使用者訊息之格式控制字串的指標。

*引數*<br/>
*格式*所使用的選擇性替代引數。

## <a name="return-value"></a>傳回值

對於所有報表目的地而言，如果發生錯誤， **_CrtDbgReport**和 **_CrtDbgReportW**會傳回-1，如果未遇到錯誤，則傳回0。 但如果報表目的地是偵錯訊息視窗，且使用者按一下 [重試] 按鈕，這些函式會傳回 1。 若使用者在偵錯訊息視窗中按一下 [中止] 按鈕，這些函示會立即中止且不會傳回值。

[_RPT，_RPTF](rpt-rptf-rptw-rptfw-macros.md) debug 宏會呼叫 **_CrtDbgReport**來產生其調試報告。 這些宏的寬字元版本以及[_ASSERT、_ASSERTE](assert-asserte-assert-expr-macros.md)、 [_RPTW](rpt-rptf-rptw-rptfw-macros.md)和[_RPTFW](rpt-rptf-rptw-rptfw-macros.md)，都使用 **_CrtDbgReportW**來產生其 debug 報告。 當 **_CrtDbgReport**或 **_CrtDbgReportW**傳回1時，這些宏會啟動偵錯工具，但前提是已啟用即時（JIT）偵錯工具。

## <a name="remarks"></a>備註

**_CrtDbgReport**和 **_CrtDbgReportW**可以將「偵錯工具」報表傳送到三個不同的目的地： debug 報表檔案、debug 監視器（Visual Studio 偵錯工具） 或 debug message 視窗。 兩個組態函式：[_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md)，可用於指定每個報表類型的一或多個目的地。 這些函式可供分別控制報告目的地和每個報表類型的目的地。 例如，您可以指定只將 **_CRT_WARN**的*reportType*傳送至「debug 監視器」，而 **_CRT_ASSERT**的*reportType*會傳送至「偵錯工具」訊息視窗和使用者定義的報表檔案。

**_CrtDbgReportW**是 **_CrtDbgReport**的寬字元版本。 且其輸出和字串參數都會使用寬字元字串；除此之外都和單一位元組字元版本相同。

**_CrtDbgReport**和 **_CrtDbgReportW**會使用**printf**或**所定義的相同規則，將引數 [n] 引數替換成格式字串，以建立用於偵錯工具的使用者訊息wprintf**函數。 然後，這些函式會根據目前的報表模式和針對*reportType*定義的檔案，產生「檢查」報表並決定目的地。 當報表傳送至 [調試訊息] 視窗時，*檔案名*、 **lineNumber**和*moduleName*會包含在視窗中顯示的資訊中。

下表列出報表模式或模式和檔案的可用選項，以及 **_CrtDbgReport**和 **_CrtDbgReportW**所產生的行為。 這些選項在 \<crtdbg.h> 中定義為位元旗標。

|報表模式|報表檔案|**_CrtDbgReport**， **_CrtDbgReportW**行為|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|不適用|使用 Windows [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) API 寫入訊息。|
|**_CRTDBG_MODE_WNDW**|不適用|呼叫 Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) API 建立訊息方塊，以顯示訊息和 [中止]、[重試] 與 [忽略] 按鈕。 如果使用者按一下 [**中止**]， **_CrtDbgReport**或 **_CrtDbgReport**會立即中止。 若使用者按一下 [重試]，則會傳回 1。 如果使用者按一下 [**忽略**]，則會繼續執行，且 **_CrtDbgReport**和 **_CrtDbgReportW**會傳回0。 請注意，如果在發生錯誤狀況時按一下 [略過]，通常會導致「未定義的行為」。|
|**_CRTDBG_MODE_FILE**|**__HFILE**|使用 Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) API 將訊息寫入至使用者提供的**控制碼**，且不會驗證檔案控制代碼的有效性;應用程式會負責開啟報表檔案，並傳遞有效的檔案控制代碼。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|將訊息寫入**stderr**。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|將訊息寫入至**stdout**。|

可將報表傳送至一到三個目的地，或是傳送到沒有任何目的地。 如需指定一或多個報表模式及報表檔案的詳細資訊，請參閱 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函式。 如需使用偵錯巨集和報告函式的詳細資訊，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。

如果您的應用程式需要比 **_CrtDbgReport**和 **_CrtDbgReportW**所提供的更多彈性，您可以撰寫自己的報告函式，並使用[_CrtSetReportHook](crtsetreporthook.md)將它連結到 C 執行時間程式庫報告機制函數.

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport**和 **_CrtDbgReportW**是 Microsoft 擴充功能。 如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

如需如何變更報表函式的範例，請參閱 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
