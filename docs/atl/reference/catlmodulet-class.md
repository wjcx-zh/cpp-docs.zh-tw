---
title: CAtlModuleT 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: b07e60265570e66337a2d13007e9ad57c6f369e4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167859"
---
# <a name="catlmodulet-class"></a>CAtlModuleT 類別

這個類別會實行 ATL 模組。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的`CAtlModuleT`類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|初始化包含目前模組之 GUID 的資料成員。|
|[CAtlModuleT::RegisterAppId](#registerappid)|將 EXE 新增至登錄。|
|[CAtlModuleT::RegisterServer](#registerserver)|將服務新增至登錄。|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|從登錄中移除 EXE。|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|從登錄中移除服務。|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|更新登錄中的 EXE 資訊。|

## <a name="remarks"></a>備註

`CAtlModuleT`衍生自[CAtlModule](../../atl/reference/catlmodule-class.md)，它會執行可執行檔（exe）或服務（EXE） ATL 模組。 可執行模組是本機的跨進程伺服器，而服務模組是 windows 應用程式，會在 Windows 啟動時于背景中執行。

`CAtlModuleT`提供初始化、註冊及取消註冊模組的支援。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

建構函式。

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>備註

呼叫[CAtlModuleT：： InitLibId](#initlibid)。

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

初始化包含目前模組之 GUID 的資料成員。

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>備註

由[CAtlModuleT：： CAtlModuleT](#catlmodulet)函式呼叫。

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

將 EXE 新增至登錄。

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

將服務新增至登錄。

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型程式庫，則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要註冊之物件的 CLSID。 如果為 Null （預設值），則會註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

從登錄中移除 EXE。

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

從登錄中移除服務。

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果類型程式庫也要取消註冊，則為 TRUE。

*pCLSID*<br/>
指向要取消註冊之物件的 CLSID。 如果為 Null （預設值），則會取消註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

更新登錄中的 EXE 資訊。

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>參數

*bRegister*<br/>
已保留。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CAtlModule 類別](../../atl/reference/catlmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
