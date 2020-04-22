---
title: CDebug報告胡克類
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
ms.openlocfilehash: 8380556bbe007326156bf0ec0eefc23052e8e056
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747729"
---
# <a name="cdebugreporthook-class"></a>CDebug報告胡克類

使用此類將除錯報告發送到命名管道。

## <a name="syntax"></a>語法

```
class CDebugReportHook
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C調試報告鉤::C調試報告鉤](#cdebugreporthook)|呼叫[設定導管名稱](#setpipename)、[設定逾時](#settimeout)與設定[Hook](#sethook)。|
|[C除錯報告鉤:*C除錯報告鉤](#dtor)|呼叫[CDebug 報告鉤::刪除胡克](#removehook)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C調試報告鉤::C調試報告胡克](#cdebugreporthookproc)|(靜態)掛接到 C 運行時調試報告流程的自定義報告函數。|
|[CDebug報告鉤::刪除胡克](#removehook)|呼叫此方法停止向命名管道發送調試報告並還原上一個報表掛鉤。|
|[CDebug報告鉤::設置胡克](#sethook)|呼叫此方法開始向命名管道發送除錯報告。|
|[CDebug 報告鉤::設定管道名稱](#setpipename)|呼叫此方法以設定將除錯報告傳送到的管道的電腦和名稱。|
|[CDebug 報告鉤:設定超時](#settimeout)|呼叫此方法以設定此類將等待命名管道變為可用的時間(以毫秒為單位)。|

## <a name="remarks"></a>備註

在服務或應用程式的調試版本中創建此類的實例,以將除錯報告發送到命名管道。 調試報告是通過調用[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)或使用包裝器來生成此函數(如[ATLTRACE](debugging-and-error-reporting-macros.md#atltrace)和[ATLASSERT](debugging-and-error-reporting-macros.md#atlassert)宏)。

使用此類允許您以互動方式除錯在非互動式[視窗站](/windows/win32/winstation/window-stations)中執行的元件。

請注意,除錯報告是使用線程的基礎安全上下文發送的。 暫時關閉模擬,以便在正在類比低特權用戶的情況下(如 Web 應用程式中)查看調試報告。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>C調試報告鉤::C調試報告鉤

呼叫[設定導管名稱](#setpipename)、[設定逾時](#settimeout)與設定[Hook](#sethook)。

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>參數

*szMachine名稱*<br/>
應向其發送調試輸出的電腦的名稱。 默認值為本地電腦。

*szPipe名稱*<br/>
應向其發送調試輸出的命名管道的名稱。

*dwTimeout*<br/>
此類將等待命名管道變為可用的時間(以毫秒為單位)。

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>C除錯報告鉤:*C除錯報告鉤

呼叫[CDebug 報告鉤::刪除胡克](#removehook)。

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>C調試報告鉤::C調試報告胡克

掛接到 C 運行時調試報告流程的自定義報告函數。

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>參數

*報表類型*<br/>
報表的類型(_CRT_WARN、_CRT_ERROR 或_CRT_ASSERT)。

*message*<br/>
訊息字串。

*返回值*<br/>
應由[_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)返回的值。

### <a name="return-value"></a>傳回值

如果挂鉤完全處理有問題的消息,則返回 FALSE,以便無需進一步報告。 傳回 TRUE,如果`_CrtDbgReport`要以正常方式報告訊息。

### <a name="remarks"></a>備註

報告函數嘗試打開命名管道,並在另一端與進程通信。 如果管道繁忙,報告功能將等待管道空閒或超時過期。 超時可以由建構函數設定,也可以由[CDebug 報告Hook 的呼叫設定:設定超時](#settimeout)。

此函數中的代碼在調用線程的基礎安全上下文中執行,也就是說,在此函數的持續時間內禁用類比。

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebug報告鉤::刪除胡克

呼叫此方法停止向命名管道發送調試報告並還原上一個報表掛鉤。

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>備註

調用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)以還原上一個報表挂鉤。

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebug報告鉤::設置胡克

呼叫此方法開始向命名管道發送除錯報告。

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>備註

調用[_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)通過[CDebugReportHookProc](#cdebugreporthookproc)路由調試報告到命名管道。 此類跟蹤上一個報表掛鉤,以便在調用[RemoveHook](#removehook)時還原它。

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebug 報告鉤::設定管道名稱

呼叫此方法以設定將除錯報告傳送到的管道的電腦和名稱。

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>參數

*szMachine名稱*<br/>
應向其發送調試輸出的電腦的名稱。

*szPipe名稱*<br/>
應向其發送調試輸出的命名管道的名稱。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebug 報告鉤:設定超時

呼叫此方法以設定此類將等待命名管道變為可用的時間(以毫秒為單位)。

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>參數

*dwTimeout*<br/>
此類將等待命名管道變為可用的時間(以毫秒為單位)。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)
