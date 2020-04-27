---
title: CAtlServiceModuleT 類別
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
ms.openlocfilehash: 0985fba4e534b6e2f6efb58ed2a8685c390dd3bd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167792"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 類別

這個類別會執行服務。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的`CAtlServiceModuleT`類別。

*nServiceNameID*<br/>
服務的資源識別碼。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlServiceModuleT：： CAtlServiceModuleT](#catlservicemodulet)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlServiceModuleT：： Handler](#handler)|服務的處理常式常式。|
|[CAtlServiceModuleT：： InitializeSecurity](#initializesecurity)|提供服務的預設安全性設定。|
|[CAtlServiceModuleT：： Install](#install)|安裝並建立服務。|
|[CAtlServiceModuleT：： IsInstalled](#isinstalled)|確認服務已安裝。|
|[CAtlServiceModuleT：： LogEvent](#logevent)|寫入事件記錄檔。|
|[CAtlServiceModuleT：： OnContinue](#oncontinue)|覆寫此方法以繼續服務。|
|[CAtlServiceModuleT：： OnInterrogate](#oninterrogate)|覆寫此方法以詢問服務。|
|[CAtlServiceModuleT：： OnPause](#onpause)|覆寫此方法以暫停服務。|
|[CAtlServiceModuleT：： OnShutdown](#onshutdown)|覆寫此方法以關閉服務|
|[CAtlServiceModuleT：： OnStop](#onstop)|覆寫此方法以停止服務|
|[CAtlServiceModuleT：： OnUnknownRequest](#onunknownrequest)|覆寫此方法以處理服務的未知要求|
|[CAtlServiceModuleT：:P arseCommandLine](#parsecommandline)|剖析命令列，並視需要執行註冊。|
|[CAtlServiceModuleT：:P reMessageLoop](#premessageloop)|在輸入訊息迴圈之前，會立即呼叫此方法。|
|[CAtlServiceModuleT：： RegisterAppId](#registerappid)|在登錄中註冊服務。|
|[CAtlServiceModuleT：： Run](#run)|執行服務。|
|[CAtlServiceModuleT：： ServiceMain](#servicemain)|服務控制管理員所呼叫的方法。|
|[CAtlServiceModuleT：： SetServiceStatus](#setservicestatus)|更新服務狀態。|
|[CAtlServiceModuleT：： Start](#start)|`CAtlServiceModuleT::WinMain`當服務啟動時呼叫。|
|[CAtlServiceModuleT：： Uninstall](#uninstall)|停止和移除服務。|
|[CAtlServiceModuleT：： Unlock](#unlock)|遞減服務的鎖定計數。|
|[CAtlServiceModuleT：： UnregisterAppId](#unregisterappid)|從登錄中移除服務。|
|[CAtlServiceModuleT：： WinMain](#winmain)|這個方法會實執行服務所需的程式碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlServiceModuleT：： m_bService](#m_bservice)|表示程式是以服務方式執行的旗標。|
|[CAtlServiceModuleT：： m_dwThreadID](#m_dwthreadid)|儲存執行緒識別碼的成員變數。|
|[CAtlServiceModuleT：： m_hServiceStatus](#m_hservicestatus)|成員變數，用於儲存目前服務的狀態資訊結構的控制碼。|
|[CAtlServiceModuleT：： m_status](#m_status)|儲存目前服務之狀態資訊結構的成員變數。|
|[CAtlServiceModuleT：： m_szServiceName](#m_szservicename)|正在註冊之服務的名稱。|

## <a name="remarks"></a>備註

`CAtlServiceModuleT`衍生自[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)，它會實作為 ATL 服務模組。 `CAtlServiceModuleT`提供命令列處理、安裝、註冊和移除的方法。 如果需要額外的功能，可以覆寫這些和其他方法。

這個類別會取代舊版 ATL 中使用的過時[CComModule 類別](../../atl/reference/ccommodule-class.md)。 如需詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT：： CAtlServiceModuleT

建構函式。

```cpp
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>備註

初始化資料成員，並設定初始服務狀態。

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT：： Handler

服務的處理常式常式。

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>參數

*dwOpcode*<br/>
定義處理常式作業的參數。 如需詳細資訊，請參閱備註。

### <a name="remarks"></a>備註

這是服務控制管理員（SCM）所呼叫的程式碼，用來抓取服務的狀態併發出指示，例如停止或暫停。 SCM 會將如下所示的作業程式碼傳遞`Handler`至，以指示服務應該執行的作業。

|作業程式碼|意義|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|停止服務。 覆寫 atlbase.h 中的[CAtlServiceModuleT：： OnStop](#onstop)方法，以變更行為。|
|SERVICE_CONTROL_PAUSE|使用者已執行。 覆寫 atlbase.h 中的空白方法[CAtlServiceModuleT：： OnPause](#onpause)以暫停服務。|
|SERVICE_CONTROL_CONTINUE|使用者已執行。 覆寫 atlbase.h 中的空白方法[CAtlServiceModuleT：： OnContinue](#oncontinue)以繼續服務。|
|SERVICE_CONTROL_INTERROGATE|使用者已執行。 覆寫 atlbase.h 中的空白方法[CAtlServiceModuleT：： OnInterrogate](#oninterrogate)以詢問服務。|
|SERVICE_CONTROL_SHUTDOWN|使用者已執行。 覆寫 atlbase.h 中的空白方法[CAtlServiceModuleT：： OnShutdown](#onshutdown)以關閉服務。|

如果無法辨識作業程式碼，則會呼叫[CAtlServiceModuleT：： OnUnknownRequest](#onunknownrequest)方法。

預設 ATL 產生的服務只會處理停止指令。 如果 SCM 通過停止指令，服務會告訴 SCM 該程式即將停止。 然後，服務會`PostThreadMessage`呼叫以將結束訊息張貼至其本身。 這會終止訊息迴圈，而服務最後會關閉。

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT：： InitializeSecurity

提供服務的預設安全性設定。

```cpp
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

任何衍生自`CAtlServiceModuleT`的類別都必須在衍生類別中執行此方法。

在的呼叫中，使用 PKT 層級驗證、RPC_C_IMP_LEVEL_IDENTIFY 的模擬層級和適當的非 null 安全`CoInitializeSecurity`描述項。

針對 wizard 產生的非特性化服務專案，這會位於

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

對於屬性化服務專案，這會位於

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT：： Install

安裝並建立服務。

```cpp
BOOL Install() throw();
```

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

將服務安裝到服務控制管理員（SCM）資料庫，然後建立服務物件。 如果無法建立服務，則會顯示訊息方塊，且方法會傳回 FALSE。

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT：： IsInstalled

確認服務已安裝。

```cpp
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>傳回值

如果已安裝服務，則傳回 TRUE，否則傳回 FALSE。

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT：： LogEvent

寫入事件記錄檔。

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
要寫入事件記錄檔的字串。

*...*<br/>
要寫入事件記錄檔的選擇性額外字串。

### <a name="remarks"></a>備註

這個方法會使用[ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw)函數，將詳細資料寫入事件記錄檔。 如果沒有任何服務正在執行，則會將字串傳送至主控台。

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT：： m_bService

表示程式是以服務方式執行的旗標。

```cpp
BOOL m_bService;
```

### <a name="remarks"></a>備註

用來區別服務 EXE 與應用程式 EXE。

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT：： m_dwThreadID

儲存服務之執行緒識別碼的成員變數。

```cpp
DWORD m_dwThreadID;
```

### <a name="remarks"></a>備註

這個變數會儲存目前線程的執行緒識別碼。

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT：： m_hServiceStatus

成員變數，用於儲存目前服務的狀態資訊結構的控制碼。

```cpp
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>備註

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)結構包含服務的相關資訊。

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT：： m_status

儲存目前服務之狀態資訊結構的成員變數。

```cpp
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>備註

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)結構包含服務的相關資訊。

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT：： m_szServiceName

正在註冊之服務的名稱。

```cpp
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>備註

以 null 終止的字串，用來儲存服務的名稱。

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT：： OnContinue

覆寫此方法以繼續服務。

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT：： OnInterrogate

覆寫此方法以詢問服務。

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT：： OnPause

覆寫此方法以暫停服務。

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT：： OnShutdown

覆寫此方法以關閉服務。

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT：： OnStop

覆寫此方法以停止服務。

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT：： OnUnknownRequest

覆寫這個方法，以處理服務的未知要求。

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>參數

*dwOpcode*<br/>
已保留。

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT：:P arseCommandLine

剖析命令列，並視需要執行註冊。

```cpp
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>參數

*lpCmdLine*<br/>
命令列。

*pnRetCode*<br/>
對應至註冊的 HRESULT （如果已發生）。

### <a name="return-value"></a>傳回值

如果成功，則傳回 true，如果無法註冊在命令列中提供的 RGS 檔案，則傳回 false。

### <a name="remarks"></a>備註

剖析命令列，並在必要時，註冊或取消註冊提供的 RGS 檔案。 這個方法會呼叫[CAtlExeModuleT：:P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline)來檢查 **/RegServer**和 **/UnregServer**。 新增引數 **-/Service**將會註冊服務。

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT：:P reMessageLoop

在輸入訊息迴圈之前，會立即呼叫此方法。

```cpp
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
這個參數會傳遞至[CAtlExeModuleT：:P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop)。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

覆寫這個方法，以加入服務的自訂初始化程式碼。

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT：： RegisterAppId

在登錄中註冊服務。

```cpp
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>參數

*bService*<br/>
必須為 true，才能註冊為服務。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT：： Run

執行服務。

```cpp
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 這個參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)一節中所討論的其中一個值。 預設值為 SW_HIDE。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`Run`呼叫之後，會呼叫[CAtlServiceModuleT：:P remessageloop](#premessageloop)、 [CAtlExeModuleT：： RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)和[CAtlExeModuleT：:P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop)。

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT：： ServiceMain

這個方法是由服務控制管理員所呼叫。

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>參數

*dwArgc*<br/>
Argc 引數。

*lpszArgv*<br/>
Argv 引數。

### <a name="remarks"></a>備註

當您開啟 [控制台] 中的`ServiceMain` [服務] 應用程式、選取服務，然後按一下 [啟動] 時，會呼叫服務控制管理員（SCM）。

在 SCM 呼叫`ServiceMain`之後，服務必須為 SCM 提供處理常式函式。 此函式可讓 SCM 取得服務的狀態，並傳遞特定的指示（例如暫停或停止）。 之後，會呼叫[CAtlServiceModuleT：： Run](#run)來執行服務的主要工作。 `Run`會繼續執行，直到服務停止為止。

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT：： SetServiceStatus

這個方法會更新服務狀態。

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>參數

*dwState*<br/>
新的狀態。 如需可能的值，請參閱[SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) 。

### <a name="remarks"></a>備註

更新服務的服務控制管理員的狀態資訊。 它是由[CAtlServiceModuleT：： Run](#run)、 [CAtlServiceModuleT：： ServiceMain](#servicemain)和其他處理常式方法所呼叫。 狀態也會儲存在成員變數[CAtlServiceModuleT：： m_status](#m_status)中。

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT：： Start

`CAtlServiceModuleT::WinMain`當服務啟動時呼叫。

```cpp
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 這個參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)一節中所討論的其中一個值。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CAtlServiceModuleT：： WinMain](#winmain)方法會處理註冊和安裝，以及移除登錄專案和卸載模組所需的工作。 當服務執行時， `WinMain`會呼叫`Start`。

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT：： Uninstall

停止和移除服務。

```cpp
BOOL Uninstall() throw();
```

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

停止執行服務，並將它從服務控制管理員資料庫中移除。

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT：： Unlock

遞減服務的鎖定計數。

```cpp
LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回鎖定計數，這可能有助於診斷和偵錯工具。

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT：： UnregisterAppId

從登錄中移除服務。

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT：： WinMain

這個方法會執行啟動服務所需的程式碼。

```cpp
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 這個參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)一節中所討論的其中一個值。

### <a name="return-value"></a>傳回值

傳回服務的傳回值。

### <a name="remarks"></a>備註

這個方法會處理命令列（使用[CAtlServiceModuleT：:P arsecommandline](#parsecommandline)），然後啟動服務（使用[CAtlServiceModuleT：： Start](#start)）。

## <a name="see-also"></a>另請參閱

[CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
