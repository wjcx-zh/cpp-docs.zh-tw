---
title: CAtlServiceModuleT 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c81df88dfdf2b40b5196d219159b48023d9db6d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT 類別
這個類別會實作服務。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, UINT nServiceNameID>  
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別衍生自`CAtlServiceModuleT`。  
  
 *nServiceNameID*  
 服務的資源識別碼。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::Handler](#handler)|服務的處理常式。|  
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|提供服務的安全性設定的預設值。|  
|[CAtlServiceModuleT::Install](#install)|安裝及建立服務。|  
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|確認已安裝服務。|  
|[CAtlServiceModuleT::LogEvent](#logevent)|寫入事件記錄檔。|  
|[CAtlServiceModuleT::OnContinue](#oncontinue)|覆寫這個方法，以繼續服務。|  
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|覆寫這個方法，以查閱服務。|  
|[CAtlServiceModuleT::OnPause](#onpause)|覆寫這個方法，以暫停服務。|  
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|覆寫這個方法，以關閉服務|  
|[CAtlServiceModuleT::OnStop](#onstop)|覆寫這個方法，以停止服務|  
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|覆寫此方法以處理未知的服務要求|  
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|剖析命令列，並視需要執行登錄。|  
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|輸入訊息迴圈之前，立即呼叫此方法。|  
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|在登錄中註冊服務。|  
|[CAtlServiceModuleT::Run](#run)|執行服務。|  
|[CAtlServiceModuleT::ServiceMain](#servicemain)|由服務控制管理員所呼叫的方法。|  
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|更新服務狀態。|  
|[CAtlServiceModuleT::Start](#start)|由呼叫`CAtlServiceModuleT::WinMain`在服務啟動時。|  
|[CAtlServiceModuleT::Uninstall](#uninstall)|停止並移除服務。|  
|[CAtlServiceModuleT::Unlock](#unlock)|服務的鎖定計數遞減。|  
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|從登錄移除服務。|  
|[CAtlServiceModuleT::WinMain](#winmain)|這個方法會實作來執行服務的程式碼。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlServiceModuleT::m_bService](#m_bservice)|旗標，指出程式以服務方式執行。|  
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|成員變數儲存的執行緒識別項。|  
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|儲存目前的服務的狀態資訊結構的控制代碼的成員變數。|  
|[CAtlServiceModuleT::m_status](#m_status)|儲存目前的服務的狀態資訊結構的成員變數。|  
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|正在註冊之服務的名稱。|  
  
## <a name="remarks"></a>備註  
 `CAtlServiceModuleT`衍生自[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)，ATL 服務模組的實作。 `CAtlServiceModuleT` 提供命令列處理、 安裝、 註冊和移除方法。 如果需要額外的功能，這些和其他方法可以覆寫。  
  
 這個類別會取代過時[CComModule 類別](../../atl/reference/ccommodule-class.md)舊版 ATL 中使用 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT  
 建構函式。  
  
```
CAtlServiceModuleT() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化資料成員，並設定初始服務狀態。  
  
##  <a name="handler"></a>  CAtlServiceModuleT::Handler  
 服務的處理常式。  
  
```
void Handler(DWORD dwOpcode) throw();
```  
  
### <a name="parameters"></a>參數  
 *dwOpcode*  
 定義處理常式作業參數。 如需詳細資訊，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 這是要擷取的服務和問題的指示，例如停止的狀態或暫停的服務控制管理員 (SCM) 呼叫的程式碼。 SCM 會傳遞至下面顯示作業程式碼`Handler`表示應該執行的服務。  
  
|作業程式碼|意義|  
|--------------------|-------------|  
|SERVICE_CONTROL_STOP|停止服務。 覆寫方法[CAtlServiceModuleT::OnStop](#onstop)中 atlbase.h 變更的行為。|  
|SERVICE_CONTROL_PAUSE|實作的使用者。 覆寫空方法[CAtlServiceModuleT::OnPause](#onpause) atlbase.h 暫停服務中。|  
|SERVICE_CONTROL_CONTINUE|實作的使用者。 覆寫空方法[CAtlServiceModuleT::OnContinue](#oncontinue) atlbase.h 以繼續使用服務中。|  
|SERVICE_CONTROL_INTERROGATE|實作的使用者。 覆寫空方法[CAtlServiceModuleT::OnInterrogate](#oninterrogate) atlbase.h 來詢問服務中。|  
|SERVICE_CONTROL_SHUTDOWN|實作的使用者。 覆寫空方法[CAtlServiceModuleT::OnShutdown](#onshutdown) atlbase.h 關閉服務中。|  
  
 如果不辨識作業程式碼，方法[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)呼叫。  
  
 預設 ATL 產生服務只會處理停止指令。 如果 SCM 通過 stop 指令，服務會告知 SCM 程式即將停止。 然後呼叫服務`PostThreadMessage`公佈至其本身的結束的訊息。 這樣會結束的訊息迴圈，服務會完全關閉。  
  
##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity  
 提供服務的安全性設定的預設值。  
  
```
HRESULT InitializeSecurity() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 在 Visual Studio.NET 2003 中，不是基底類別中實作這個方法。 Visual Studio 專案精靈產生的程式碼中包含這個方法，但如果使用 ATL 7.1 編譯較早版本的 Visual c + + 中建立的專案，會發生編譯錯誤。 任何衍生自的類別`CAtlServiceModuleT`必須在衍生類別中實作這個方法。  
  
 呼叫中使用 PKT 層級驗證、 RPC_C_IMP_LEVEL_IDENTIFY 的模擬層級和適當的非 null 安全性描述元**CoInitializeSecurity**。  
  
 精靈產生的非屬性化的服務專案中，這會在  
  
 [!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]  
  
 針對屬性化的服務專案，這會在  
  
 [!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]  
  
##  <a name="install"></a>  CAtlServiceModuleT::Install  
 安裝及建立服務。  
  
```
BOOL Install() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 將服務安裝到服務控制管理員 (SCM) 資料庫，然後建立服務物件。 如果無法建立服務，會顯示訊息方塊，而且方法會傳回 FALSE。  
  
##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled  
 確認已安裝服務。  
  
```
BOOL IsInstalled() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 TRUE 的服務是否已安裝，則為 FALSE 否則。  
  
##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent  
 寫入事件記錄檔。  
  
```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszFormat`  
 要寫入事件記錄檔的字串。  
  
 ...  
 要寫入事件記錄檔的選擇性額外字串。  
  
### <a name="remarks"></a>備註  
 這個方法將詳細資料寫出至事件記錄檔，使用函數[ReportEvent](http://msdn.microsoft.com/library/windows/desktop/aa363679)。 如果沒有服務執行時，字串會傳送至主控台。  
  
##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService  
 旗標，指出程式以服務方式執行。  
  
```
BOOL m_bService;
```  
  
### <a name="remarks"></a>備註  
 用來從應用程式 EXE 區別服務 EXE。  
  
##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID  
 成員變數儲存服務的執行緒識別項。  
  
```
DWORD m_dwThreadID;
```  
  
### <a name="remarks"></a>備註  
 此變數會儲存目前執行緒的執行緒識別項。  
  
##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus  
 儲存目前的服務的狀態資訊結構的控制代碼的成員變數。  
  
```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```  
  
### <a name="remarks"></a>備註  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996)結構包含服務的相關資訊。  
  
##  <a name="m_status"></a>  CAtlServiceModuleT::m_status  
 儲存目前的服務的狀態資訊結構的成員變數。  
  
```
SERVICE_STATUS m_status;
```  
  
### <a name="remarks"></a>備註  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996)結構包含服務的相關資訊。  
  
##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName  
 正在註冊之服務的名稱。  
  
```
TCHAR [256] m_szServiceName;
```  
  
### <a name="remarks"></a>備註  
 以 null 結束的字串儲存服務的名稱。  
  
##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue  
 覆寫這個方法，以繼續服務。  
  
```
void OnContinue() throw();
```  
  
##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate  
 覆寫這個方法，以查閱服務。  
  
```
void OnInterrogate() throw();
```  
  
##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause  
 覆寫這個方法，以暫停服務。  
  
```
void OnPause() throw();
```  
  
##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown  
 覆寫這個方法，以關閉服務。  
  
```
void OnShutdown() throw();
```  
  
##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop  
 覆寫這個方法，以停止服務。  
  
```
void OnStop() throw();
```  
  
##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest  
 覆寫此方法以處理未知的要求傳送至服務。  
  
```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```  
  
### <a name="parameters"></a>參數  
 */\* dwOpcode \*/*  
 保留的。  
  
##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine  
 剖析命令列，並視需要執行登錄。  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpCmdLine`  
 命令列。  
  
 `pnRetCode`  
 （如果它發生），來註冊對應的 HRESULT。  
  
### <a name="return-value"></a>傳回值  
 在成功時或在命令列中提供的 RGS 檔無法登錄為 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 剖析命令列註冊及取消註冊提供的 RGS 檔案如有必要。 這個方法會呼叫[CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline)檢查 **/RegServer**和 **/UnregServer**。 新增引數 **-/ 服務**會註冊服務。  
  
##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop  
 輸入訊息迴圈之前，立即呼叫此方法。  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>參數  
 `nShowCmd`  
 這個參數會傳遞至[CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以加入自訂的初始化程式碼服務。  
  
##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId  
 在登錄中註冊服務。  
  
```
inline HRESULT RegisterAppId(bool bService = false) throw();
```  
  
### <a name="parameters"></a>參數  
 *bService*  
 必須註冊為服務，則為 true。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="run"></a>  CAtlServiceModuleT::Run  
 執行服務。  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>參數  
 `nShowCmd`  
 指定要顯示在視窗的方式。 這個參數可以是其中一個值中討論[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) > 一節。 預設值是 SW_HIDE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 之後，呼叫**執行**呼叫[CAtlServiceModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)，和[CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop)。  
  
##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain  
 由服務控制管理員時，會呼叫這個方法。  
  
```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```  
  
### <a name="parameters"></a>參數  
 *dwArgc*  
 Argc 引數。  
  
 *lpszArgv*  
 Argv 引數。  
  
### <a name="remarks"></a>備註  
 服務控制管理員 (SCM) 呼叫`ServiceMain`當您在控制台中開啟 服務應用程式，選取服務，並按一下 啟動。  
  
 SCM 之後呼叫`ServiceMain`，服務必須提供 SCM 處理常式函式。 此函式可讓 SCM 取得服務的狀態並傳遞 （例如暫停或停止） 的特定指示。 接著， [CAtlServiceModuleT::Run](#run)呼叫以執行服務的主要工作。 **執行**會繼續執行直到服務已停止。  
  
##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus  
 這個方法會更新服務狀態。  
  
```
void SetServiceStatus(DWORD dwState) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwState`  
 新的狀態。 請參閱[SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)可能的值。  
  
### <a name="remarks"></a>備註  
 更新服務的服務控制管理員的狀態資訊。 呼叫此方法[CAtlServiceModuleT::Run](#run)， [CAtlServiceModuleT::ServiceMain](#servicemain)和其他處理常式方法。 狀態也會儲存在成員變數[CAtlServiceModuleT::m_status](#m_status)。  
  
##  <a name="start"></a>  CAtlServiceModuleT::Start  
 由呼叫`CAtlServiceModuleT::WinMain`在服務啟動時。  
  
```
HRESULT Start(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>參數  
 `nShowCmd`  
 指定要顯示在視窗的方式。 這個參數可以是其中一個值中討論[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) > 一節。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 [CAtlServiceModuleT::WinMain](#winmain)方法會處理註冊和安裝，以及工作涉及在移除登錄項目及解除安裝模組中。 執行服務時，`WinMain`呼叫**啟動**。  
  
##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall  
 停止並移除服務。  
  
```
BOOL Uninstall() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 停止執行服務，並從服務控制管理員資料庫中移除。  
  
##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock  
 服務的鎖定計數遞減。  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的鎖定計數，這可能有助於診斷和偵錯。  
  
##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId  
 從登錄移除服務。  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain  
 這個方法會實作來啟動服務的程式碼。  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>參數  
 `nShowCmd`  
 指定要顯示在視窗的方式。 這個參數可以是其中一個值中討論[WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) > 一節。  
  
### <a name="return-value"></a>傳回值  
 傳回服務的傳回值。  
  
### <a name="remarks"></a>備註  
 這個方法會處理命令列 (與[CAtlServiceModuleT::ParseCommandLine](#parsecommandline))，然後啟動服務 (使用[CAtlServiceModuleT::Start](#start))。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
