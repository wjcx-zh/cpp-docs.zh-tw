---
title: "_CrtDbgReport、_CrtDbgReportW | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4720053f96972c6ff0d846b9641d9ddc2d256f20
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport、_CrtDbgReportW
產生具有偵錯訊息的報表，並將報表傳送至三個可能的目的地 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `reportType`  
 報表類型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `filename`  
 發生判斷提示/報表之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 發生判斷提示/報表之原始程式檔中的行號，或為 `NULL`。  
  
 `moduleName`  
 發生判斷提示或報表之模組 (.exe 或 .dll) 的名稱的指標。  
  
 `format`  
 用於建立使用者訊息之格式控制字串的指標。  
  
 `argument`  
 `format` 使用的選擇性替換引數。  
  
## <a name="return-value"></a>傳回值  
 針對所有報表目的地、`_CrtDbgReport`和`_CrtDbgReportW`傳回-1，如果發生錯誤，0，如果未發生錯誤。 但如果報表目的地是偵錯訊息視窗，且使用者按一下 [重試] 按鈕，這些函式會傳回 1。 若使用者在偵錯訊息視窗中按一下 [中止] 按鈕，這些函示會立即中止且不會傳回值。  
  
 [_RPT、_RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 偵錯巨集會呼叫 `_CrtDbgReport` 以產生偵錯報告。 這些巨集的寬字元版本以及 [_ASSERT&#91;E&#93;](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)、`_RPTW n` 和 `_RPTFW n`，均會使用 `_CrtDbgReportW` 產生偵錯報告。 若有啟用 Just-In-Time (JIT) 偵錯，則當 `_CrtDbgReport` 或 `_CrtDbgReportW` 傳回 1 時，這些巨集就會啟動偵錯工具。  
  
## <a name="remarks"></a>備註  
 `_CrtDbgReport` 和 `_CrtDbgReportW` 可以將偵錯報表傳送至三個不同的目的地：偵錯報表檔案、偵錯監視器 ([!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 偵錯工具) 或偵錯訊息視窗。 兩個組態函式：[_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md)，可用於指定每個報表類型的一或多個目的地。 這些函式可供分別控制報告目的地和每個報表類型的目的地。 例如，可能指定只有 `reportType` 的 `_CRT_WARN` 要傳送至偵錯監視器，而 `reportType` 的 `_CRT_ASSERT` 則要傳送至偵錯訊息視窗和使用者定義的報表檔案。  
  
 `_CrtDbgReportW` 是寬字元版本的 `_CrtDbgReport`。 且其輸出和字串參數都會使用寬字元字串；除此之外都和單一位元組字元版本相同。  
  
 `_CrtDbgReport` 和 `_CrtDbgReportW` 會使用 `argument` 或 `n` 函式所定義的相同規則，透過將 `format`[`printf`] 引數取代為 `wprintf` 字串，來建立偵錯報表的使用者訊息。 然後這些函式會根據目前的報表模組以及針對 `reportType` 所定義的檔案，產生偵錯報表並決定一或多個目的地。 當報表是傳送至偵錯訊息視窗時，會在顯示於視窗中的資訊裡包含 `filename`、`lineNumber` 和 `moduleName`。  
  
 下表列出針對報表的一或多個模式和檔案，以及 `_CrtDbgReport` 和 `_CrtDbgReportW` 的結果行為所提供的選擇。 這些選項在 \<crtdbg.h> 中定義為位元旗標。  
  
|報表模式|報表檔案|`_CrtDbgReport`、`_CrtDbgReportW` 行為|  
|-----------------|-----------------|------------------------------------------------|  
|`_CRTDBG_MODE_DEBUG`|不適用|使用 Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) API 寫入訊息。|  
|`_CRTDBG_MODE_WNDW`|不適用|呼叫 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) API 建立訊息方塊，以顯示訊息和 [中止]、[重試] 與 [忽略] 按鈕。 若使用者按一下 [中止]，`_CrtDbgReport` 或 `_CrtDbgReport` 會立即中止。 若使用者按一下 [重試]，則會傳回 1。 若使用者按一下 [略過]，執行會繼續，且 `_CrtDbgReport` 和 `_CrtDbgReportW` 會傳回 0。 請注意，如果在發生錯誤狀況時按一下 [略過]，通常會導致「未定義的行為」。|  
|`_CRTDBG_MODE_FILE`|`__HFILE`|使用 Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) API，將訊息寫入至使用者提供的 `HANDLE`，且不驗證檔案控制代碼的有效性；應用程式會負責開啟報表檔案並傳遞有效的檔案控制代碼。|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDERR`|將訊息寫入至 `stderr`。|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDOUT`|將訊息寫入至 `stdout`。|  
  
 可將報表傳送至一到三個目的地，或是傳送到沒有任何目的地。 如需指定一或多個報表模式及報表檔案的詳細資訊，請參閱 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函式。 如需使用偵錯巨集和報告函式的詳細資訊，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。  
  
 若您的應用程式需要比 `_CrtDbgReport` 和 `_CrtDbgReportW` 所提供的更多彈性，您可以自行撰寫報告函式，並使用 [_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md) 函式，將該報告函式連結到 C 執行階段程式庫報告機制。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtDbgReport`|\<crtdbg.h>|  
|`_CrtDbgReportW`|\<crtdbg.h>|  
  
 `_CrtDbgReport` 和 `_CrtDbgReportW` 是 Microsoft 擴充功能。 如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_crtdbgreport.c  
#include <crtdbg.h>  
  
int main(int argc, char *argv[]) {  
#ifdef _DEBUG  
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);  
#endif  
}  
```  
  
 如需如何變更報表函式的範例，請參閱 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)   
 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [_DEBUG](../../c-runtime-library/debug.md)