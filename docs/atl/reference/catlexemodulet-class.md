---
title: Catldllmodulet 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9b19888f6eae3efe7baf4429ec1174432f99a10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118553"
---
# <a name="catlexemodulet-class"></a>Catldllmodulet 類別

此類別代表應用程式的模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別衍生自`CAtlExeModuleT`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|建構函式。|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|初始化 com。|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|剖析命令列，並執行必要的註冊。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|這個方法是只有在訊息迴圈結束之後，立即呼叫。|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|輸入訊息迴圈之前，立即會呼叫這個方法。|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|註冊類別物件。|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。|
|[CAtlExeModuleT::Run](#run)|這個方法來初始化、 執行訊息迴圈的 EXE 模組中執行的程式碼，並清除。|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|這個方法會執行訊息迴圈。|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|取消初始化 com。|
|[CAtlExeModuleT::Unlock](#unlock)|模組的鎖定計數遞減。|
|[CAtlExeModuleT::WinMain](#winmain)|這個方法會實作程式碼，以執行 EXE。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|旗標，指出應該在關閉此模組的延遲。|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|暫停值，用來確保關機前在釋放所有物件。|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|逾時值，用來延遲卸載模組。|

## <a name="remarks"></a>備註

`CAtlExeModuleT` 代表應用程式 (EXE) 的模組，並包含支援建立 EXE、 處理命令列、 註冊類別物件、 執行訊息迴圈，以及清除結束的程式碼。

此類別被設計來改善效能，當 EXE 伺服器中的 COM 物件持續建立和終結。 所指定的持續時間內的最後一個的 COM 物件發行後，等候 EXE [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)資料成員。 如果沒有任何活動，在這段期間 （也就是會建立任何 COM 物件，） 起始關機程序。

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)資料成員是用來判斷是否將 EXE 應該使用以上定義的機制的旗標。 如果它設定為 false，則會立即終止該模組。

如需有關在 ATL 中的模組的詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

建構函式。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

如果 EXE 模組無法初始化，WinMain 會立即傳回而不需要進一步處理。

##  <a name="dtor"></a>  CAtlExeModuleT:: ~ CAtlExeModuleT

解構函式。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

初始化 com。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法會從建構函式呼叫，並可以覆寫預設實作不同的方式初始化 COM。 預設實作是呼叫`CoInitializeEx(NULL, COINIT_MULTITHREADED)`或`CoInitialize(NULL)`視專案設定而定。

覆寫此方法時，通常需要覆寫[CAtlExeModuleT::UninitializeCom](#uninitializecom)。

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

旗標，指出應該在關閉此模組的延遲。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>備註

請參閱[CAtlExeModuleT 概觀](../../atl/reference/catlexemodulet-class.md)如需詳細資訊。

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

用來確保所有的物件會進入關機之前暫停值。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>備註

將此值變更之後呼叫[CAtlExeModuleT::InitializeCom](#initializecom)設定做為伺服器正在關閉暫停值的毫秒數。 預設值為 1000年毫秒。

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

逾時值，用來延遲卸載模組。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>備註

將此值變更之後呼叫[CAtlExeModuleT::InitializeCom](#initializecom)來定義的逾時值為用於伺服器正在關閉的毫秒數。 預設值是 5000 毫秒。 請參閱[CAtlExeModuleT 概觀](../../atl/reference/catlexemodulet-class.md)如需詳細資訊。

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

剖析命令列，並執行必要的註冊。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>參數

*lpCmdLine*<br/>
命令列傳遞至應用程式。

*pnRetCode*<br/>
對應至註冊 （如果它發生） 的 HRESULT。

### <a name="return-value"></a>傳回值

如果應用程式應該繼續執行，否則為 false 的傳回 true。

### <a name="remarks"></a>備註

這個方法會從呼叫[CAtlExeModuleT::WinMain](#winmain)可覆寫來處理命令列參數。 預設實作會檢查 **/RegServer**並 **/UnRegServer**命令列引數，並執行註冊或取消註冊。

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

這個方法是只有在訊息迴圈結束之後，立即呼叫。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

覆寫這個方法，以執行自訂的應用程式的清除作業。 預設實作會呼叫[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)。

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

輸入訊息迴圈之前，立即會呼叫這個方法。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
做為傳遞的值*nShowCmd* WinMain 中的參數。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

覆寫這個方法，以加入應用程式的自訂初始化程式碼。 預設實作會註冊類別物件。

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

讓其他應用程式可以連線到它，則您可以向 OLE 類別物件。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwClsContext*<br/>
指定要執行的類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。

*dwFlags*<br/>
決定類別物件的連接類型。 可能的值為 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。

### <a name="return-value"></a>傳回值

在成功、 S_FALSE，如果沒有任何類別，若要註冊或失敗的錯誤 HRESULT 會傳回 S_OK。

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

移除類別的物件。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

在成功、 S_FALSE，如果沒有任何類別，若要註冊或失敗的錯誤 HRESULT 會傳回 S_OK。

##  <a name="run"></a>  CAtlExeModuleT::Run

這個方法來初始化、 執行訊息迴圈的 EXE 模組中執行的程式碼，並清除。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定要顯示的視窗的方式。 這個參數可以是其中一個值所述[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)一節。 預設為 SW_HIDE。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

可以覆寫此方法。 不過，在實務上最好是覆寫[CAtlExeModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::RunMessageLoop](#runmessageloop)，或[CAtlExeModuleT::PostMessageLoop](#postmessageloop)改為。

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

這個方法會執行訊息迴圈。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>備註

若要變更訊息迴圈的行為，可以覆寫此方法。

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

取消初始化 com。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>備註

依預設這個方法只會呼叫[CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize) ，而從解構函式呼叫。 覆寫這個方法，如果您覆寫[CAtlExeModuleT::InitializeCom](#initializecom)。

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

模組的鎖定計數遞減。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回值，這個值可能是適用於診斷或測試。

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

這個方法會實作程式碼，以執行 EXE。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>參數

*nShowCmd*<br/>
指定要顯示的視窗的方式。 這個參數可以是其中一個值所述[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)一節。

### <a name="return-value"></a>傳回值

傳回可執行檔的傳回值。

### <a name="remarks"></a>備註

可以覆寫此方法。 如果覆寫[CAtlExeModuleT::PreMessageLoop](#premessageloop)， [CAtlExeModuleT::PostMessageLoop](#postmessageloop)，或[CAtlExeModuleT::RunMessageLoop](#runmessageloop)未提供足夠的彈性可覆寫`WinMain`函式使用此方法。

## <a name="see-also"></a>另請參閱

[ATLDuck 範例](../../visual-cpp-samples.md)<br/>
[CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
