---
title: CAtlExeModuleT 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497835"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT 類別

此類別代表應用程式的模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自的`CAtlExeModuleT`類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|建構函式。|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|初始化 COM。|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|剖析命令列, 並視需要執行註冊。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|這個方法會在訊息迴圈結束之後立即呼叫。|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|在輸入訊息迴圈之前, 會立即呼叫此方法。|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|註冊類別物件。|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。|
|[CAtlExeModuleT::Run](#run)|這個方法會執行 EXE 模組中的程式碼, 以初始化、執行訊息迴圈和清除。|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|這個方法會執行訊息迴圈。|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|取消初始化 COM。|
|[CAtlExeModuleT::Unlock](#unlock)|遞減模組的鎖定計數。|
|[CAtlExeModuleT::WinMain](#winmain)|這個方法會實行執行 EXE 所需的程式碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|旗標, 表示應關閉模組的延遲。|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|用來確保在關閉前釋放所有物件的暫停值。|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|用來延遲卸載模組的超時值。|

## <a name="remarks"></a>備註

`CAtlExeModuleT`表示應用程式 (EXE) 的模組, 並包含支援建立 EXE、處理命令列、註冊類別物件、執行訊息迴圈, 以及在結束時清除的程式碼。

這個類別是設計用來在 EXE 伺服器中的 COM 物件持續建立和終結時改善效能。 在最後一個 COM 物件釋放之後, EXE 會等待[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)資料成員所指定的持續時間。 如果在這段期間沒有活動 (也就是不會建立任何 COM 物件), 就會起始關機程式。

[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)資料成員是用來判斷 EXE 是否應使用上述所定義機制的旗標。 如果設定為 false, 則模組會立即終止。

如需 ATL 中模組的詳細資訊, 請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="catlexemodulet"></a>CAtlExeModuleT:: CAtlExeModuleT

建構函式。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

如果無法初始化 EXE 模組, WinMain 會立即傳回, 而不會進一步處理。

##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

解構函式。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="initializecom"></a>CAtlExeModuleT:: InitializeCom

初始化 COM。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法是從函式呼叫, 而且可以覆寫以與預設實作為不同的方式初始化 COM。 預設的實作為會`CoInitializeEx(NULL, COINIT_MULTITHREADED)`呼叫`CoInitialize(NULL)`或, 視專案設定而定。

覆寫這個方法通常需要覆寫[CAtlExeModuleT:: UninitializeCom](#uninitializecom)。

##  <a name="m_bdelayshutdown"></a>CAtlExeModuleT:: m_bDelayShutdown

旗標, 表示應關閉模組的延遲。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[CAtlExeModuleT 總覽](../../atl/reference/catlexemodulet-class.md)。

##  <a name="m_dwpause"></a>CAtlExeModuleT:: m_dwPause

用來確保所有物件在關閉前都已消失的暫停值。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>備註

呼叫[CAtlExeModuleT:: InitializeCom](#initializecom)之後, 請變更此值, 以設定用來關閉伺服器之暫停值的毫秒數。 預設值為1000毫秒。

##  <a name="m_dwtimeout"></a>CAtlExeModuleT:: m_dwTimeOut

用來延遲卸載模組的超時值。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>備註

呼叫[CAtlExeModuleT:: InitializeCom](#initializecom)之後, 請變更此值, 以定義用來關閉伺服器的超時值所使用的毫秒數。 預設值是 5000 毫秒。 如需詳細資訊, 請參閱[CAtlExeModuleT 總覽](../../atl/reference/catlexemodulet-class.md)。

##  <a name="parsecommandline"></a>CAtlExeModuleT::P arseCommandLine

剖析命令列, 並視需要執行註冊。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>參數

*lpCmdLine*<br/>
傳遞給應用程式的命令列。

*pnRetCode*<br/>
對應至註冊的 HRESULT (如果已發生)。

### <a name="return-value"></a>傳回值

如果應用程式應該繼續執行, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

這個方法是從[CAtlExeModuleT:: WinMain](#winmain)呼叫, 而且可以覆寫以處理命令列參數。 預設的執行會檢查 **/RegServer**和 **/UnRegServer**命令列引數, 並執行登錄或取消註冊。

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

這個方法會在訊息迴圈結束之後立即呼叫。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

覆寫此方法以執行自訂應用程式清除。 預設的實值會呼叫[CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects)。

##  <a name="premessageloop"></a>CAtlExeModuleT::P reMessageLoop

在輸入訊息迴圈之前, 會立即呼叫此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
當做 WinMain 中的*nShowCmd*參數傳遞的值。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

覆寫這個方法, 以加入應用程式的自訂初始化程式碼。 預設的實作為註冊類別物件。

##  <a name="registerclassobjects"></a>CAtlExeModuleT:: RegisterClassObjects

向 OLE 註冊類別物件, 讓其他應用程式可以與其連接。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwClsContext*<br/>
指定要在其中執行類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。

*dwFlags*<br/>
判斷類別物件的連線類型。 可能的值為 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>傳回值

成功時傳回 S_OK, 如果沒有可註冊的類別, 則傳回 S_FALSE, 否則會在失敗時傳回錯誤 HRESULT。

##  <a name="revokeclassobjects"></a>CAtlExeModuleT:: RevokeClassObjects

移除類別物件。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

成功時傳回 S_OK, 如果沒有可註冊的類別, 則傳回 S_FALSE, 否則會在失敗時傳回錯誤 HRESULT。

##  <a name="run"></a>CAtlExeModuleT:: Run

這個方法會執行 EXE 模組中的程式碼, 以初始化、執行訊息迴圈和清除。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 這個參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)一節中所討論的其中一個值。 預設為 SW_HIDE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

可以覆寫這個方法。 不過, 在實務上, 最好改為覆寫[CAtlExeModuleT::P remessageloop](#premessageloop)、 [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)或[CAtlExeModuleT::P ostmessageloop](#postmessageloop) 。

##  <a name="runmessageloop"></a>CAtlExeModuleT:: RunMessageLoop

這個方法會執行訊息迴圈。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>備註

可以覆寫這個方法, 以變更訊息迴圈的行為。

##  <a name="uninitializecom"></a>CAtlExeModuleT:: UninitializeCom

取消初始化 COM。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>備註

根據預設, 這個方法只會呼叫[CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) , 並從「析構函式」呼叫。 如果您覆寫[CAtlExeModuleT:: InitializeCom](#initializecom), 請覆寫這個方法。

##  <a name="unlock"></a>CAtlExeModuleT:: Unlock

遞減模組的鎖定計數。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回可能有助於診斷或測試的值。

##  <a name="winmain"></a>CAtlExeModuleT:: WinMain

這個方法會實行執行 EXE 所需的程式碼。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 這個參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)一節中所討論的其中一個值。

### <a name="return-value"></a>傳回值

傳回可執行檔的傳回值。

### <a name="remarks"></a>備註

可以覆寫這個方法。 如果覆寫[CAtlExeModuleT::P remessageloop](#premessageloop)、 [CAtlExeModuleT::P ostmessageloop](#postmessageloop)或[CAtlExeModuleT:: RunMessageLoop](#runmessageloop)無法提供足夠的彈性, 則可以使用這個來`WinMain`覆寫函數方法.

## <a name="see-also"></a>另請參閱

[ATLDuck 範例](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
