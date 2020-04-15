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
ms.openlocfilehash: a20a02a467d74a89e3cda176a6a15961be4ffd61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318978"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT 類別

此類表示應用程式的模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
來自 的`CAtlExeModuleT`類 派生自 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT:CAtlExeModuleT](#catlexemodulet)|建構函式。|
|[CAtlExeModuleT:_CAtlExeModuleT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT:初始化Com](#initializecom)|初始化 COM。|
|[CAtlExeModuleT::P](#parsecommandline)|分析命令行並在必要時執行註冊。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|此方法在消息迴圈退出后立即調用。|
|[CAtlExeModuleT::P重新消息迴圈](#premessageloop)|在輸入消息迴圈之前立即調用此方法。|
|[CAtlExeModuleT::註冊類物件](#registerclassobjects)|註冊類物件。|
|[CAtlExeModuleT::撤銷類物件](#revokeclassobjects)|撤銷類物件。|
|[CAtlExeModuleT::運行](#run)|此方法在 EXE 模組中執行代碼以初始化、運行消息迴圈和清理。|
|[CAtlExeModuleT::運行消息迴圈](#runmessageloop)|此方法執行消息迴圈。|
|[CAtlExeModuleT:取消初始化Com](#uninitializecom)|取消初始化 COM。|
|[CAtlExeModuleT:解鎖](#unlock)|撤銷模組的鎖計數。|
|[CAtlExeModuleT::贏主](#winmain)|此方法實現運行 EXE 所需的代碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT:m_bDelayShutdown](#m_bdelayshutdown)|指示關閉模組時應出現延遲的標誌。|
|[CAtlExeModuleT:m_dwPause](#m_dwpause)|用於確保所有對象的暫停值在關機之前釋放。|
|[CAtlExeModuleT:m_dwTimeOut](#m_dwtimeout)|用於延遲模組卸載的超時值。|

## <a name="remarks"></a>備註

`CAtlExeModuleT`表示應用程式 (EXE) 的模組,並包含支援創建 EXE、處理命令列、註冊類物件、運行消息迴圈和在退出時清理的代碼。

當不斷創建和銷毀 EXE 伺服器中的 COM 物件時,此類旨在提高性能。 釋放最後一個 COM 物件後,EXE 將等待[由 CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)資料成員指定的持續時間。 如果在此期間沒有活動(即未創建 COM 物件),則啟動關閉過程。

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)數據成員是一個標誌,用於確定 EXE 是否應使用上面定義的機制。 如果設置為 false,則模組將立即終止。

有關 ATL 中的模組的詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT:CAtlExeModuleT

建構函式。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

如果 EXE 模組無法初始化,WinMain 將立即返回,無需進一步處理。

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT:_CAtlExeModuleT

解構函式。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT:初始化Com

初始化 COM。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法是從建構函數調用的,可以重寫以不同於預設實現的方式初始化 COM。 預設實現調用`CoInitializeEx(NULL, COINIT_MULTITHREADED)``CoInitialize(NULL)`或取決於專案配置。

重寫此方法通常需要重寫[CAtlExeModuleT::取消初始化Com](#uninitializecom)。

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT:m_bDelayShutdown

指示關閉模組時應出現延遲的標誌。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT:m_dwPause

用於確保所有物件在關機前消失的暫停值。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>備註

在調用[CAtlExeModuleT::初始化 Com](#initializecom)後更改此值,以設置用作關閉伺服器的暫停值的毫秒數。 默認值為 1000 毫秒。

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT:m_dwTimeOut

用於延遲模組卸載的超時值。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>備註

在調用[CAtlExeModuleT::初始化 Com](#initializecom)後更改此值,以定義用作關閉伺服器超時值的毫秒數。 預設值是 5000 毫秒。 有關詳細資訊,請參閱[CAtlExeModuleT 概述](../../atl/reference/catlexemodulet-class.md)。

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::P

分析命令行並在必要時執行註冊。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>參數

*lpCmdline*<br/>
傳遞給應用程式的命令行。

*pnRet 代碼*<br/>
與註冊對應的 HRESULT(如果發生)。

### <a name="return-value"></a>傳回值

如果應用程式應繼續運行,則返回 true,否則為 false。

### <a name="remarks"></a>備註

此方法從[CAtlExeModuleT 呼叫:winMain,](#winmain)可以重寫以處理命令列交換機。 預設實現檢查 **/RegServer**和 **/unRegServer**命令列參數,並執行註冊或取消註冊。

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

此方法在消息迴圈退出后立即調用。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

重寫此方法以執行自定義應用程式清理。 預設實現呼叫[CAtlExemoduleT::撤銷類別物件](#revokeclassobjects)。

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::P重新消息迴圈

在輸入消息迴圈之前立即調用此方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
在 WinMain 中作為*nShowCmd*參數傳遞的值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

重寫此方法以添加應用程式的自定義初始化代碼。 預設實現註冊類物件。

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::註冊類物件

將類物件註冊到 OLE,以便其他應用程式可以連接到它。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwCls 上下文*<br/>
指定要在其中運行類物件的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。

*dwFlags*<br/>
確定與類對象的連接類型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>傳回值

返回成功S_OK,S_FALSE如果沒有要註冊的類,或者失敗時出現錯誤 HRESULT。

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::撤銷類物件

刪除類物件。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,S_FALSE如果沒有要註冊的類,或者失敗時出現錯誤 HRESULT。

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::運行

此方法在 EXE 模組中執行代碼以初始化、運行消息迴圈和清理。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 此參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中討論的值之一。 默認值為SW_HIDE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

可以重寫此方法。 然而,在實踐中,最好重寫[CAtlExeModuleT::P重新消息環](#premessageloop)[,CAtlExeModuleT::RunMessageLoop,](#runmessageloop)或[CAtlExmoduleT::PostMessageLoop。](#postmessageloop)

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::運行消息迴圈

此方法執行消息迴圈。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>備註

可以重寫此方法來更改消息循環的行為。

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT:取消初始化Com

取消初始化 COM。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>備註

默認情況下,此方法只需調用[CoUn 初始化](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize),並從析構函數調用。 如果重寫[CAtlExeModuleT::初始化 Com,](#initializecom)則重寫此方法。

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT:解鎖

撤銷模組的鎖計數。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

返回可用於診斷或測試的值。

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::贏主

此方法實現運行 EXE 所需的代碼。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定視窗的顯示方式。 此參數可以是[WinMain](/windows/win32/api/winbase/nf-winbase-winmain)部分中討論的值之一。

### <a name="return-value"></a>傳回值

返回可執行檔的返回值。

### <a name="remarks"></a>備註

可以重寫此方法。 如果重寫[CAtlExeModuleT::PreMessage Loop、CAtlExeModuleT::PostMessageLoop)](#premessageloop)或[CAtlExeModuleT::RunMessageLoop](#runmessageloop)不能提供足夠的靈活性,則可以`WinMain`使用此方法[CAtlExeModuleT::PostMessageLoop](#postmessageloop)重寫 函數。

## <a name="see-also"></a>另請參閱

[ATLDuck 樣品](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
