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
- ATL.CDebugReportHook
- CDebugReportHook
- ATL::CDebugReportHook
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 632167d4f78ef930673450d6d087f32e91b6541f
ms.lasthandoff: 02/24/2017

---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 類別
您可以使用這個類別，將偵錯報表傳送至具名管道。  
  
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
  
|名稱|說明|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|（靜態）自訂報告函式，連結至 C 執行階段偵錯報告處理程序。|  
|[CDebugReportHook::RemoveHook](#removehook)|呼叫這個方法，以停止偵錯報表傳送到具名管道，並還原先前的報告攔截。|  
|[CDebugReportHook::SetHook](#sethook)|呼叫這個方法來啟動偵錯報表傳送到具名管道。|  
|[CDebugReportHook::SetPipeName](#setpipename)|呼叫這個方法來設定電腦和偵錯報表傳送到其中的管道名稱。|  
|[CDebugReportHook::SetTimeout](#settimeout)|呼叫這個方法，以毫秒為單位，這個類別會等待具名管道，可供設定的時間。|  
  
## <a name="remarks"></a>備註  
 在您的服務或應用程式偵錯報表傳送至具名管道的偵錯組建中建立此類別的執行個體。 藉由呼叫所產生的偵錯報告[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或包裝函式使用此功能，例如[ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e)和[ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3)巨集。  
  
 使用這個類別可讓您以互動方式偵錯元件在執行非互動式[視窗電台](http://msdn.microsoft.com/library/windows/desktop/ms687096)。  
  
 請注意，偵錯報告不會傳送使用執行緒的基礎的安全性內容。 暫時停用模擬，以便您可以在其中的低權限之使用者的模擬正在進行中，例如在 web 應用程式的情況下檢視偵錯報告。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="a-namecdebugreporthooka--cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 呼叫[SetPipeName](#setpipename)， [SetTimeout](#settimeout)，和[SetHook](#sethook)。  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>參數  
 `szMachineName`  
 偵錯輸出應該傳送電腦名稱。 預設為本機電腦。  
  
 `szPipeName`  
 偵錯輸出應該傳送的具名管道的名稱。  
  
 `dwTimeout`  
 時間 （毫秒），這個類別會等待可用的具名管道。  
  
##  <a name="a-namedtora--cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 呼叫[CDebugReportHook::RemoveHook](#removehook)。  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="a-namecdebugreporthookproca--cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 自訂報告函式，連結至 C 執行階段偵錯報告處理程序。  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>參數  
 `reportType`  
 報表 （_CRT_WARN、 _CRT_ERROR 或 _CRT_ASSERT） 的型別。  
  
 `message`  
 訊息字串。  
  
 *returnValue*  
 應傳回的值[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
### <a name="return-value"></a>傳回值  
 傳回 FALSE 如果攔截該訊息能完整處理，因此沒有進一步的報告不需要。 如果為 true`_CrtDbgReport`應該以一般方式報告訊息。  
  
### <a name="remarks"></a>備註  
 報告函式會嘗試開啟具名的管道，與另一端的程序進行通訊。 如果管道忙碌時，報告的函式會等待管道是免費的或在逾時到期。 可以設定逾時，建構函式或呼叫[CDebugReportHook::SetTimeout](#settimeout)。  
  
 在呼叫執行緒的基礎的安全性內容中執行此函式中的程式碼，也就是模擬已停用此函式的持續時間。  
  
##  <a name="a-nameremovehooka--cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::RemoveHook  
 呼叫這個方法，以停止偵錯報表傳送到具名管道，並還原先前的報告攔截。  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)還原先前的報告攔截。  
  
##  <a name="a-namesethooka--cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook  
 呼叫這個方法來啟動偵錯報表傳送到具名管道。  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)要將偵錯報告經[CDebugReportHookProc](#cdebugreporthookproc)具名管道。 這個類別會追蹤的上一個報告攔截，因此它可以是還原時[RemoveHook](#removehook)呼叫。  
  
##  <a name="a-namesetpipenamea--cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName  
 呼叫這個方法來設定電腦和偵錯報表傳送到其中的管道名稱。  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>參數  
 `szMachineName`  
 偵錯輸出應該傳送電腦名稱。  
  
 `szPipeName`  
 偵錯輸出應該傳送的具名管道的名稱。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
##  <a name="a-namesettimeouta--cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout  
 呼叫這個方法，以毫秒為單位，這個類別會等待具名管道，可供設定的時間。  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>參數  
 `dwTimeout`  
 時間 （毫秒），這個類別會等待可用的具名管道。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)

