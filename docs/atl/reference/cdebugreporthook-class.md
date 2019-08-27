---
title: CDebugReportHook 類別
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496779"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook 類別

使用這個類別, 即可將 debug 報表傳送到具名管道。

## <a name="syntax"></a>語法

```
class CDebugReportHook
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|會呼叫[SetPipeName](#setpipename)、 [SetTimeout](#settimeout)和[SetHook](#sethook)。|
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|呼叫[CDebugReportHook:: RemoveHook](#removehook)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|靜止連結至 C 執行時間 debug 報告程式的自訂報告函數。|
|[CDebugReportHook::RemoveHook](#removehook)|呼叫這個方法, 以停止將 debug 報表傳送到具名管道, 並還原先前的報表攔截。|
|[CDebugReportHook::SetHook](#sethook)|呼叫這個方法, 以開始將 debug 報表傳送至具名管道。|
|[CDebugReportHook::SetPipeName](#setpipename)|呼叫這個方法, 以設定要將其傳送到其上的「偵測」報告的電腦和「管道」名稱。|
|[CDebugReportHook::SetTimeout](#settimeout)|呼叫這個方法來設定這個類別將等候具名管道變成可用的時間 (以毫秒為單位)。|

## <a name="remarks"></a>備註

在您的服務或應用程式的「debug 組建」中, 建立這個類別的實例, 以將「偵測報表」傳送至具名管道。 藉由呼叫[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或使用此函式的包裝函式 (例如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏), 即可產生 Debug 報表。

使用此類別可讓您以互動的方式, 在非互動式[視窗工作站](/windows/win32/winstation/window-stations)中執行元件的調試。

請注意, 您可以使用執行緒的基礎安全性內容來傳送 debug 報表。 模擬已暫時停用, 以便在模擬低許可權使用者 (例如 web 應用程式) 的情況時, 可以查看 debug 報表。

## <a name="requirements"></a>需求

**標頭:** atlutil。h

##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

會呼叫[SetPipeName](#setpipename)、 [SetTimeout](#settimeout)和[SetHook](#sethook)。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>參數

*szMachineName*<br/>
應將調試輸出傳送至其中的電腦名稱稱。 預設為本機電腦。

*szPipeName*<br/>
應將調試輸出傳送至其中的具名管道名稱。

*dwTimeout*<br/>
這個類別將等候具名管道變成可用的時間 (以毫秒為單位)。

##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook

呼叫[CDebugReportHook:: RemoveHook](#removehook)。

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

連結至 C 執行時間 debug 報告程式的自訂報告函數。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表的類型 (_CRT_WARN、_CRT_ERROR 或 _CRT_ASSERT)。

*message*<br/>
訊息字串。

*returnValue*<br/>
應由[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)傳回的值。

### <a name="return-value"></a>傳回值

如果攔截程式完全處理問題中的訊息, 而不需要進一步的報告, 則傳回 FALSE。 如果`_CrtDbgReport`應該以一般方式報告訊息, 則傳回 TRUE。

### <a name="remarks"></a>備註

報告函式會嘗試開啟具名管道, 並與另一端的進程進行通訊。 如果管道忙碌中, 報告函式會等到管道可用或超時時間過期。 此超時時間可由函式或[CDebugReportHook:: SetTimeout](#settimeout)的呼叫來設定。

此函式中的程式碼會在呼叫執行緒的基礎安全性內容中執行, 也就是在此函式的持續時間停用模擬功能。

##  <a name="removehook"></a>CDebugReportHook::RemoveHook

呼叫這個方法, 以停止將 debug 報表傳送到具名管道, 並還原先前的報表攔截。

```
void RemoveHook() throw();
```

### <a name="remarks"></a>備註

呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)以還原先前的報表攔截。

##  <a name="sethook"></a>CDebugReportHook::SetHook

呼叫這個方法, 以開始將 debug 報表傳送至具名管道。

```
void SetHook() throw();
```

### <a name="remarks"></a>備註

呼叫[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) , 讓 debug 報表透過[CDebugReportHookProc](#cdebugreporthookproc)路由傳送至具名管道。 這個類別會追蹤先前的報表連結, 以便在呼叫[RemoveHook](#removehook)時進行還原。

##  <a name="setpipename"></a>CDebugReportHook::SetPipeName

呼叫這個方法, 以設定要將其傳送到其上的「偵測」報告的電腦和「管道」名稱。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>參數

*szMachineName*<br/>
應將調試輸出傳送至其中的電腦名稱稱。

*szPipeName*<br/>
應將調試輸出傳送至其中的具名管道名稱。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

##  <a name="settimeout"></a>CDebugReportHook:: SetTimeout

呼叫這個方法來設定這個類別將等候具名管道變成可用的時間 (以毫秒為單位)。

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>參數

*dwTimeout*<br/>
這個類別將等候具名管道變成可用的時間 (以毫秒為單位)。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)
