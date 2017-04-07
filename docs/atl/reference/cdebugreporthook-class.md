---
title: "CDebugReportHook 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1de883341e0a53a1520fa44d99e7907ee1fe10b6
ms.lasthandoff: 03/31/2017

---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 類別
使用此類別將偵錯報表傳送至具名的管道。  
  
## <a name="syntax"></a>語法  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|呼叫[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|呼叫[CDebugReportHook::RemoveHook](#removehook)。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|（靜態）連接到 C 執行階段的自訂報告函式偵錯報表的處理序。|  
|[CDebugReportHook::RemoveHook](#removehook)|呼叫這個方法，以停止偵錯報表傳送到的具名管道，並還原先前的報告攔截。|  
|[CDebugReportHook::SetHook](#sethook)|呼叫此方法以開始偵錯報表傳送到的具名管道。|  
|[CDebugReportHook::SetPipeName](#setpipename)|呼叫此方法以設定電腦和偵錯報表傳送到其中的管道名稱。|  
|[CDebugReportHook::SetTimeout](#settimeout)|呼叫這個方法來設定以毫秒為單位，這個類別會變成可用的具名管道的等候時間。|  
  
## <a name="remarks"></a>備註  
 在您的服務或應用程式偵錯報表傳送至具名管道的偵錯組建中建立此類別的執行個體。 偵錯報告由呼叫產生[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或包裝函式使用這個函式，例如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)巨集。  
  
 使用這個類別可讓您以互動方式偵錯元件在執行非互動式[視窗電台](http://msdn.microsoft.com/library/windows/desktop/ms687096)。  
  
 請注意，偵錯報表傳送使用基礎的安全性內容的執行緒。 暫時停用模擬，以便在其中的低權限的使用者進行模擬，例如在 web 應用程式的情況下，可以檢視偵錯報告。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 呼叫[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>參數  
 `szMachineName`  
 偵錯輸出應該傳送的電腦名稱。 預設為本機電腦。  
  
 `szPipeName`  
 偵錯輸出應該傳送的具名管道的名稱。  
  
 `dwTimeout`  
 以毫秒為單位，這個類別會變成可用的具名管道的等候時間。  
  
##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 呼叫[CDebugReportHook::RemoveHook](#removehook)。  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 連接到 C 執行階段的自訂報告函式偵錯報表的處理序。  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `reportType`  
 報表 （_CRT_WARN、 _CRT_ERROR 或 _CRT_ASSERT） 的類型。  
  
 `message`  
 訊息字串。  
  
 *returnValue*  
 應傳回的值[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
### <a name="return-value"></a>傳回值  
 傳回 FALSE 如果攔截處理的訊息完全而無須任何進一步的報告。 如果為 true`_CrtDbgReport`應該以一般方式報告訊息。  
  
### <a name="remarks"></a>備註  
 報告函式會嘗試開啟具名的管道和與其通訊的另一端的程序。 如果管道忙碌，報告的函式會等待管道是免費或逾時為止。 在逾時可以設定由建構函式或呼叫[CDebugReportHook::SetTimeout](#settimeout)。  
  
 在呼叫執行緒的基礎的安全性內容中執行此函式中的程式碼，也就是此函式期間停用模擬。  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 呼叫這個方法，以停止偵錯報表傳送到的具名管道，並還原先前的報告攔截。  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)還原先前的報告攔截。  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 呼叫此方法以開始偵錯報表傳送到的具名管道。  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)要將偵錯報告經[CDebugReportHookProc](#cdebugreporthookproc)具名管道。 這個類別會追蹤的先前報表攔截程序，讓它可以是還原時[RemoveHook](#removehook)呼叫。  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 呼叫此方法以設定電腦和偵錯報表傳送到其中的管道名稱。  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>參數  
 `szMachineName`  
 偵錯輸出應該傳送的電腦名稱。  
  
 `szPipeName`  
 偵錯輸出應該傳送的具名管道的名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 呼叫這個方法來設定以毫秒為單位，這個類別會變成可用的具名管道的等候時間。  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>參數  
 `dwTimeout`  
 以毫秒為單位，這個類別會變成可用的具名管道的等候時間。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)

