---
title: _CrtDbgReport、_CrtDbgReportW | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405051"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport、_CrtDbgReportW

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
報告類型： **_CRT_WARN**， **_CRT_ERROR**，和 **_CRT_ASSERT**。

*filename*<br/>
發生判斷提示/報表的原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
發生判斷提示/報表的原始程式檔中的行號或**NULL**。

*moduleName*<br/>
發生判斷提示或報表之模組 (.exe 或 .dll) 的名稱的指標。

*格式*<br/>
用於建立使用者訊息之格式控制字串的指標。

*引數*<br/>
所使用的選擇性替換引數*格式*。

## <a name="return-value"></a>傳回值

針對所有報表目的地、 **_CrtDbgReport**和 **_CrtDbgReportW**傳回-1，如果發生錯誤，0，如果未發生錯誤。 但如果報表目的地是偵錯訊息視窗，且使用者按一下 [重試] 按鈕，這些函式會傳回 1。 若使用者在偵錯訊息視窗中按一下 [中止] 按鈕，這些函示會立即中止且不會傳回值。

[_RPT、 _RPTF](rpt-rptf-rptw-rptfw-macros.md)偵錯巨集呼叫 **_CrtDbgReport**若要產生偵錯報表。 這些巨集的寬字元版本，以及[_ASSERT、 _ASSERTE](assert-asserte-assert-expr-macros.md)， [_RPTW](rpt-rptf-rptw-rptfw-macros.md)和[_RPTFW](rpt-rptf-rptw-rptfw-macros.md)，使用 **_CrtDbgReportW**至產生其偵錯報表。 當 **_CrtDbgReport**或 **_CrtDbgReportW**傳回 1 時，這些巨集啟動偵錯工具，在 just-in-time (JIT) 偵錯已啟用。

## <a name="remarks"></a>備註

**_CrtDbgReport**和 **_CrtDbgReportW**可以將偵錯報表傳送至三個不同的目的地： 偵錯報表檔案、 偵錯監視器 （Visual Studio 偵錯工具） 或偵錯訊息視窗。 兩個組態函式：[_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md)，可用於指定每個報表類型的一或多個目的地。 這些函式可供分別控制報告目的地和每個報表類型的目的地。 例如，便可指定*reportType*的 **_CRT_WARN**只能傳送至偵錯監視，而*reportType*的 **_CRT_ASSERT**傳送至偵錯訊息視窗和使用者定義的報表檔案。

**_CrtDbgReportW**是寬字元版本的 **_CrtDbgReport**。 且其輸出和字串參數都會使用寬字元字串；除此之外都和單一位元組字元版本相同。

**_CrtDbgReport**和 **_CrtDbgReportW**建立偵錯報表的使用者訊息所得到*引數*[**n**] 引數到*格式*字串所定義的相同規則**printf**或**wprintf**函式。 這些函式產生偵錯報表，然後判斷目的地或目的地，根據目前的報表模組以及檔案定義*reportType*。 當報表傳送至偵錯訊息視窗， *filename*， **lineNumber**，和*moduleName*隨附在視窗中顯示的資訊。

下表列出可用的選項，針對報表模式或模式的檔案和所產生的行為的 **_CrtDbgReport**和 **_CrtDbgReportW**。 這些選項在 \<crtdbg.h> 中定義為位元旗標。

|報表模式|報表檔案|**_CrtDbgReport**， **_CrtDbgReportW**行為|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|不適用|使用 Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) API 寫入訊息。|
|**_CRTDBG_MODE_WNDW**|不適用|呼叫 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) API 建立訊息方塊，以顯示訊息和 [中止]、[重試] 與 [忽略] 按鈕。 如果使用者按一下**中止**， **_CrtDbgReport**或 **_CrtDbgReport**立即中止。 若使用者按一下 [重試]，則會傳回 1。 如果使用者按一下**忽略**，繼續執行並 **_CrtDbgReport**和 **_CrtDbgReportW**傳回 0。 請注意，如果在發生錯誤狀況時按一下 [略過]，通常會導致「未定義的行為」。|
|**_CRTDBG_MODE_FILE**|**__HFILE**|將訊息寫入至使用者提供**處理**，使用 Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx)應用程式開發介面，而且不會驗證檔案控制代碼的有效性，應用程式會負責開啟報表檔案，並傳遞有效的檔案控制代碼。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|將訊息寫入至**stderr**。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|將訊息寫入至**stdout**。|

可將報表傳送至一到三個目的地，或是傳送到沒有任何目的地。 如需指定一或多個報表模式及報表檔案的詳細資訊，請參閱 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函式。 如需使用偵錯巨集和報告函式的詳細資訊，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。

如果您的應用程式需要更多的彈性比所提供的 **_CrtDbgReport**和 **_CrtDbgReportW**，您可以撰寫自己的報告的函式，並將它連結到 C 執行階段程式庫報告使用的機制[_CrtSetReportHook](crtsetreporthook.md)函式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
