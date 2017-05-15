---
title: _CrtSetReportFile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 16
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
ms.openlocfilehash: 339da058334fa394aa10f2eb33707203f4f1be7b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="crtsetreportfile"></a>_CrtSetReportFile
使用 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 指定 `_CRTDBG_MODE_FILE` 之後，您可以指定要接收訊息文字的檔案控制代碼。 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 也會使用 `_CrtSetReportFile` 指定文字的目的地 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### <a name="parameters"></a>參數  
 `reportType`  
 報表類型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportFile`  
 `reportType` 的新報表檔案。  
  
## <a name="return-value"></a>傳回值  
 成功完成時，`_CrtSetReportFile` 會傳回為 `reportType` 中指定之報表類型定義的先前報表檔案。 如果針對 `reportType` 傳入的值無效，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `_CRTDBG_HFILE_ERROR`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_CrtSetReportFile` 可搭配 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函式使用，以定義 `_CrtDbgReport` 所產生之特定報表類型的一或多個目的地。 呼叫 `_CrtSetReportMode` 為特定報表類型指派 `_CRTDBG_MODE_FILE` 報告模式之後，應接著呼叫 `_CrtSetReportFile` 定義要作為目的地使用的特定檔案或資料流。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetReportFile` 的呼叫。  
  
 下表顯示 `reportFile` 的可用選項及 `_CrtDbgReport` 的結果行為清單。 這些選項在 Crtdbg.h 中定義為位元旗標。  
  
 `file handle`  
 將作為訊息目的地的檔案控制代碼。 不會嘗試驗證此控制代碼的有效性。 您必須開啟和關閉檔案控制代碼。 例如：  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 將訊息寫入至可如下重新導向的 `stderr`：  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 將訊息寫入至您可以重新導向的 `stdout`。  
  
 `_CRTDBG_REPORT_FILE`  
 傳回目前的報表模式。  
  
 可個別控制每個報表類型所使用的報表檔案。 例如，您可以指定將 `_CRT_ERROR` 的 `reportType` 回報給 `stderr`，並將 `_CRT_ASSERT` 的 `reportType` 回報給使用者定義的檔案控制代碼或資料流。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportFile`|\<crtdbg.h>|\<errno.h>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 (`stdin`、`stdout` 和 `stderr`) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
