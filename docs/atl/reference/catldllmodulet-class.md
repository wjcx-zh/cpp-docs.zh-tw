---
title: CAtlDllModuleT 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863158"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 類別

此類別代表 DLL 的模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自 `CAtlDllModuleT`的類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlDllModuleT：： CAtlDllModuleT](#catldllmodulet)|建構函式。|
|[CAtlDllModuleT：： ~ CAtlDllModuleT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlDllModuleT：:D llCanUnloadNow](#dllcanunloadnow)|測試 DLL 是否可以卸載。|
|[CAtlDllModuleT：:D llGetClassObject](#dllgetclassobject)|傳回 Class Factory。|
|[CAtlDllModuleT：:D llMain](#dllmain)|動態連結程式庫（DLL）中的選擇性進入點。|
|[CAtlDllModuleT：:D llRegisterServer](#dllregisterserver)|將專案新增至 DLL 中物件的系統登錄。|
|[CAtlDllModuleT：:D llUnregisterServer](#dllunregisterserver)|針對 DLL 中的物件，移除系統登錄中的專案。|
|[CAtlDllModuleT：： GetClassObject](#getclassobject)|傳回 Class Factory。 由[DllGetClassObject](#dllgetclassobject)叫用。|

## <a name="remarks"></a>備註

`CAtlDllModuleT` 代表動態連結程式庫（DLL）的模組，並提供所有 DLL 專案所使用的函式。 這項[CAtlModuleT](../../atl/reference/catlmodulet-class.md)類別的特製化包含註冊的支援。

如需 ATL 中模組的詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="catldllmodulet"></a>CAtlDllModuleT：： CAtlDllModuleT

建構函式。

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>CAtlDllModuleT：： ~ CAtlDllModuleT

解構函式。

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>CAtlDllModuleT：:D llCanUnloadNow

測試 DLL 是否可以卸載。

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>傳回值

如果 DLL 可以卸載，則傳回 S_OK，如果無法卸載，則傳回 S_FALSE。

##  <a name="dllgetclassobject"></a>CAtlDllModuleT：:D llGetClassObject

傳回 Class Factory。

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
要建立之物件的 CLSID。

*riid*<br/>
所要求介面的 IID。

*ppv*<br/>
由*riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppv*會設定為 Null。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

##  <a name="dllmain"></a>CAtlDllModuleT：:D llMain

動態連結程式庫（DLL）中的選擇性進入點。

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>參數

*dwReason*<br/>
如果設定為 DLL_PROCESS_ATTACH，就會停用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知呼叫。

*lpReserved*<br/>
已保留。

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

停用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知呼叫對於具有許多 Dll、經常建立和刪除線程，而且其 Dll 不需要附件/表示中斷連結之執行緒層級通知的多執行緒應用程式而言，是很有用的優化。

##  <a name="dllregisterserver"></a>CAtlDllModuleT：:D llRegisterServer

將專案新增至 DLL 中物件的系統登錄。

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型程式庫，則為 TRUE。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

##  <a name="dllunregisterserver"></a>CAtlDllModuleT：:D llUnregisterServer

針對 DLL 中的物件，移除系統登錄中的專案。

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果要從登錄中移除類型程式庫，則為 TRUE。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

##  <a name="getclassobject"></a>CAtlDllModuleT：： GetClassObject

建立指定之 CLSID 的物件。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
要建立之物件的 CLSID。

*riid*<br/>
所要求介面的 IID。

*ppv*<br/>
由*riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppv*會設定為 Null。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法是由[CAtlDllModuleT：:D llgetclassobject](#dllgetclassobject)所呼叫，並包含以提供回溯相容性。

## <a name="see-also"></a>另請參閱

[CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT 類別](../../atl/reference/catlexemodulet-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
