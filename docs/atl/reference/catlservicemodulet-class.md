---
title: CAtlServiceModuleT 類
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 5d87eada997d0bbfe44cd07a819f6b012a7a3a20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321343"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 類

此類實現服務。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
來自 的`CAtlServiceModuleT`類 派生自 。

*n 服務名稱ID*<br/>
服務的資源標識碼。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtl服務模組T:CAtl服務模組T](#catlservicemodulet)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlServiceModuleT::處理程式](#handler)|服務的處理程式例程。|
|[CAtlServiceModuleT:初始化安全性](#initializesecurity)|提供服務的預設安全設置。|
|[CAtlService 模組T:安裝](#install)|安裝並創建服務。|
|[CAtlServiceModuleT:已安裝](#isinstalled)|確認已安裝該服務。|
|[CAtlServiceModuleT::日誌事件](#logevent)|寫入事件日誌。|
|[CatlService 模組T::繼續](#oncontinue)|重寫此方法以繼續服務。|
|[CAtlServiceModuleT::上查詢](#oninterrogate)|重寫此方法以詢問服務。|
|[CatlServiceModuleT::打開暫停](#onpause)|重寫此方法以暫停服務。|
|[CatlServiceModuleT::關閉時間](#onshutdown)|重寫此方法以關閉服務|
|[CatlServiceModuleT::打開](#onstop)|重寫此方法以停止服務|
|[CatlServiceModuleT:關於未知請求](#onunknownrequest)|重寫此方法以處理對服務的未知要求|
|[CAtlServiceModuleT::Parse命令熱線](#parsecommandline)|分析命令行並在必要時執行註冊。|
|[CAtl服務模組T::P重新訊息迴圈](#premessageloop)|在輸入消息迴圈之前立即調用此方法。|
|[CAtlServiceModuleT::註冊應用程式](#registerappid)|在註冊表中註冊服務。|
|[CAtlService 模組T::運行](#run)|運行服務。|
|[CAtlServiceModuleT:服務主](#servicemain)|服務控制管理器調用的方法。|
|[CAtl服務模組T:設定服務狀態](#setservicestatus)|更新服務狀態。|
|[CAtlService 模組T::開始](#start)|服務啟動`CAtlServiceModuleT::WinMain`時調用。|
|[CAtlServiceModuleT::卸載](#uninstall)|停止並刪除服務。|
|[CAtlService 模組T:解鎖](#unlock)|撤銷服務的鎖計數。|
|[CAtlServiceModuleT::未註冊AppId](#unregisterappid)|從註冊表中刪除服務。|
|[CAtlServiceModuleT::贏曼](#winmain)|此方法實現運行服務所需的代碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlServiceModuleT:m_bService](#m_bservice)|指示程式作為服務運行的標誌。|
|[CAtlServiceModuleT:m_dwThreadID](#m_dwthreadid)|存儲線程標識符的成員變數。|
|[CAtlServiceModuleT:m_hServiceStatus](#m_hservicestatus)|存儲當前服務狀態資訊結構句柄的成員變數。|
|[CAtlService 模組T:m_status](#m_status)|存儲當前服務的狀態資訊結構的成員變數。|
|[CAtlServiceModuleT:m_szServiceName](#m_szservicename)|正在註冊的服務的名稱。|

## <a name="remarks"></a>備註

`CAtlServiceModuleT`,派生自[CAtlExeModuleT,](../../atl/reference/catlexemodulet-class.md)實現 ATL 服務模組。 `CAtlServiceModuleT`提供了命令行處理、安裝、註冊和刪除的方法。 如果需要額外的功能,可以重寫這些方法和其他方法。

此會取代早期版本的 ATL 中使用的過時的[CComModule 類別](../../atl/reference/ccommodule-class.md)。 有關詳細資訊,請參閱[ATL 模組課程](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtl服務模組T:CAtl服務模組T

建構函式。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>備註

初始化數據成員並設置初始服務狀態。

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::處理程式

服務的處理程式例程。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>參數

*dwOpcode*<br/>
定義處理程式操作的開關。 有關詳細資訊,請參閱註釋。

### <a name="remarks"></a>備註

這是服務控制管理員 (SCM) 呼叫的代碼來檢索服務的狀態並發出停止或暫停等指令。 SCM 傳遞操作代碼(如下所示)`Handler`以指示服務應執行哪些操作。

|操作代碼|意義|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|停止服務。 重寫方法[CAtlServiceModuleT:atlbase.h](#onstop)中的 OnStop 以更改行為。|
|SERVICE_CONTROL_PAUSE|用戶實現。 重寫空方法[CAtlServiceModuleT:atlbase.h 中的"OnPause"](#onpause)以暫停服務。|
|SERVICE_CONTROL_CONTINUE|用戶實現。 重寫空方法[CAtlServiceModuleT::在](#oncontinue)atlbase.h 中繼續繼續繼續服務。|
|SERVICE_CONTROL_INTERROGATE|用戶實現。 重寫空方法[CAtlServiceModuleT:atlbase.h 中的"OnInterrogate"](#oninterrogate)以詢問服務。|
|SERVICE_CONTROL_SHUTDOWN|用戶實現。 重寫空方法[CAtlServiceModuleT:在](#onshutdown)atlbase.h 中關閉以關閉服務。|

如果無法辨識操作代碼,則呼叫方法[CAtlServiceModuleT:on 未知請求](#onunknownrequest)。

默認 ATL 生成的服務僅處理停止指令。 如果 SCM 通過停止指令,服務會告訴 SCM 程式即將停止。 然後,服務調用`PostThreadMessage`將退出消息發佈到自身。 這將終止消息循環,服務最終將關閉。

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT:初始化安全性

提供服務的預設安全設置。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

派生的任何`CAtlServiceModuleT`類都必須在派生類中實現此方法。

在調用 中使用 PKT 級身份驗證、RPC_C_IMP_LEVEL_IDENTIFY的類比`CoInitializeSecurity`級別以及調用 中適當的非空安全描述符。

對於嚮導生成的非屬性化服務專案,這將在

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

對於屬性化服務專案,這將在

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlService 模組T:安裝

安裝並創建服務。

```
BOOL Install() throw();
```

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

將服務安裝到服務控制管理員 (SCM) 資料庫中,然後創建服務物件。 如果無法創建服務,將顯示一個消息框,該方法將返回 FALSE。

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT:已安裝

確認已安裝該服務。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>傳回值

如果安裝了服務,則返回 TRUE,否則返回 FALSE。

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::日誌事件

寫入事件日誌。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>參數

*psz格式*<br/>
要寫入事件記錄檔的字串。

*...*<br/>
要寫入事件日誌的可選額外字串。

### <a name="remarks"></a>備註

此方法使用函數[ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)將詳細資訊寫入事件日誌。 如果沒有服務運行,則字串將發送到主控台。

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT:m_bService

指示程式作為服務運行的標誌。

```
BOOL m_bService;
```

### <a name="remarks"></a>備註

用於區分服務 EXE 和應用程式 EXE。

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT:m_dwThreadID

存儲服務線程標識符的成員變數。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>備註

此變數儲存當前線程的線程標識符。

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT:m_hServiceStatus

存儲當前服務狀態資訊結構句柄的成員變數。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>備註

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)結構包含有關服務的資訊。

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlService 模組T:m_status

存儲當前服務的狀態資訊結構的成員變數。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>備註

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)結構包含有關服務的資訊。

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT:m_szServiceName

正在註冊的服務的名稱。

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>備註

儲存服務名稱的 null 終止字串。

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CatlService 模組T::繼續

重寫此方法以繼續服務。

```
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::上查詢

重寫此方法以詢問服務。

```
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CatlServiceModuleT::打開暫停

重寫此方法以暫停服務。

```
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CatlServiceModuleT::關閉時間

重寫此方法以關閉服務。

```
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CatlServiceModuleT::打開

重寫此方法以停止服務。

```
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CatlServiceModuleT:關於未知請求

重寫此方法以處理對服務的未知請求。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>參數

*dwOpcode*<br/>
已保留。

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::Parse命令熱線

分析命令行並在必要時執行註冊。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>參數

*lpCmdline*<br/>
命令列。

*pnRet 代碼*<br/>
與註冊對應的 HRESULT(如果發生)。

### <a name="return-value"></a>傳回值

如果無法註冊命令列中提供的 RGS 檔,則在成功時返回 true,或 false。

### <a name="remarks"></a>備註

如有必要,分析命令行並註冊或取消註冊提供的 RGS 檔。 此方法呼叫[CAtlExeModuleT::Parse 命令線](../../atl/reference/catlexemodulet-class.md#parsecommandline)來檢查 **/RegServer**和 **/unregServer**。 添加參數 **-/服務**將註冊服務。

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtl服務模組T::P重新訊息迴圈

在輸入消息迴圈之前立即調用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
此參數傳遞給[CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

重寫此方法以添加服務的自定義初始化代碼。

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::註冊應用程式

在註冊表中註冊服務。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>參數

*b服務*<br/>
註冊為服務必須為 true。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlService 模組T::運行

運行服務。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 此參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中討論的值之一。 默認值為SW_HIDE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫後`Run`, 呼叫 CAtlServiceModuleT::PreMessageLoop,CAtlExeModuleT::RunMessageLoop,cAtlExeModuleT::PostMessageLoop [CAtlServiceModuleT::PreMessageLoop](#premessageloop) [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop) [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop) 。

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT:服務主

此方法由服務控制管理器調用。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>參數

*德阿格克*<br/>
argc 參數。

*lpszArgv*<br/>
argv 參數。

### <a name="remarks"></a>備註

在「控制面板」中打開服務應用程式`ServiceMain`時,服務控制管理器(SCM)會調用,選擇服務,然後單擊"開始"。

SCM 調`ServiceMain`用 後,服務必須為 SCM 提供處理程式功能。 此功能允許 SCM 獲取服務狀態並傳遞特定指令(如暫停或停止)。 隨後[,CAtlServiceModuleT:](#run)調用 Run 來執行服務的主要工作。 `Run`繼續執行,直到服務停止。

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtl服務模組T:設定服務狀態

此方法更新服務狀態。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>參數

*德沃州*<br/>
新的狀態。 有關可能的值,請參閱[設定服務狀態](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)。

### <a name="remarks"></a>備註

更新服務控制管理員的服務狀態資訊。 它由[CAtlServiceModuleT 調用::運行](#run)[,CAtl ServiceModuleT::服務Main](#servicemain)和其他處理程式方法。 狀態也儲存在成員變數[CAtlServiceModuleT::m_status](#m_status)。

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlService 模組T::開始

服務啟動`CAtlServiceModuleT::WinMain`時調用。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 此參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中討論的值之一。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CAtlServiceModuleT:WinMain](#winmain)方法既處理註冊和安裝,也處理刪除註冊表項和卸載模組所涉及的任務。 執行服務時,`WinMain`呼`Start`叫 。

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::卸載

停止並刪除服務。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

停止服務運行,並將其從服務控制管理員資料庫中刪除。

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlService 模組T:解鎖

撤銷服務的鎖計數。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

返回鎖計數,這可能可用於診斷和調試。

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::未註冊AppId

從註冊表中刪除服務。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::贏曼

此方法實現啟動服務所需的代碼。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 此參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中討論的值之一。

### <a name="return-value"></a>傳回值

返回服務的返回值。

### <a name="remarks"></a>備註

此方法處理命令列(使用[CAtlServiceModuleT::Parse命令線](#parsecommandline)),然後啟動服務(使用[CAtlServiceModuleT::開始](#start))。

## <a name="see-also"></a>另請參閱

[CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
