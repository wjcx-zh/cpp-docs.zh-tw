---
title: _CrtSetReportMode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b7e3cb7562fb63467ef0e0ee28861936fb820fa3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="crtsetreportmode"></a>_CrtSetReportMode
指定 `_CrtDbgReport` 以及任何呼叫 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 之巨集 (例如 [_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)；[_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)；[_RPT、_RPTF、_RPTW、_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)；以及 [_RPT、_RPTF、_RPTW、_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)) 所產生之特定報表類型的一或多個目的地 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `reportType`  
 報表類型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportMode`  
 `reportType` 的一或多個新報表模式。  
  
## <a name="return-value"></a>傳回值  
 成功完成時，`_CrtSetReportMode` 會傳回 `reportType` 中指定之報表類型的先前報表模式。 如果當做 `reportType` 傳入的值無效，或為 `reportMode` 指定的模式無效，`_CrtSetReportMode` 會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 -1。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_CrtSetReportMode`指定 `_CrtDbgReport` 的輸出目的地。 由於巨集 `_ASSERT`、`_ASSERTE`、`_RPT` 和 `_RPTF` 呼叫 `_CrtDbgReport`，因此 `_CrtSetReportMode` 會指定使用這些巨集指定之文字的輸出目的地。  
  
 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetReportMode` 的呼叫。  
  
 如果您未呼叫 `_CrtSetReportMode` 定義訊息的輸出目的地，則下列預設值會立即生效：  
  
-   判斷提示失敗及錯誤會導向到偵錯訊息視窗。  
  
-   Windows 應用程式的警告會傳送至偵錯工具的輸出視窗。  
  
-   主控台應用程式的警告不會顯示。  
  
 下表列出 Crtdbg.h 中定義的報表類型。  
  
|報表類型|描述|  
|-----------------|-----------------|  
|`_CRT_WARN`|不需要立即注意的警告、訊息和資訊。|  
|`_CRT_ERROR`|錯誤、無法復原的問題和需要立即注意的問題。|  
|`_CRT_ASSERT`|判斷提示失敗 (評估為 `FALSE` 的判斷提示運算式)。|  
  
 `_CrtSetReportMode` 函式會將 `reportMode` 中指定的新報表模式指派給 `reportType` 中指定的報表類型，並傳回先前為 `reportType` 定義的報表模式。 下表列出 `reportMode` 的可用選項及 `_CrtDbgReport` 的結果行為。 這些選項在 Crtdbg.h 中定義為位元旗標。  
  
|報表模式|_CrtDbgReport 行為|  
|-----------------|-----------------------------|  
|`_CRTDBG_MODE_DEBUG`|將訊息寫入至偵錯工具的輸出視窗。|  
|`_CRTDBG_MODE_FILE`|將訊息寫入至使用者提供的檔案控制代碼。 應呼叫 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md)，以定義特定檔案或資料流作為目的地使用。|  
|`_CRTDBG_MODE_WNDW`|建立訊息方塊，以顯示訊息和 `Abort`、`Retry` 與 `Ignore` 按鈕。|  
|`_CRTDBG_REPORT_MODE`|傳回指定之 `reportType` 的 `reportMode`：<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 每個報表類型可使用一個、兩個或三個模式進行報告，或完全不使用任何模式。 因此，您可以為單一報表類型定義多個目的地。 例如，下列程式碼片段會將判斷提示失敗同時傳送至偵錯訊息視窗和 `stderr`：  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 此外，可個別控制每個報表類型的一或多個報告模式。 例如，您可以指定將 `_CRT_WARN` 的 `reportType` 傳送至輸出偵錯字串，同時使用偵錯訊息視窗顯示 `_CRT_ASSERT` 並將其傳送至 `stderr`，如先前所示。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportMode`|\<crtdbg.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
