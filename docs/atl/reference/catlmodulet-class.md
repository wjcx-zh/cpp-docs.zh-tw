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
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321417"
---
# <a name="catlmodulet-class"></a>CAtlModuleT 類別

此類實現 ATL 模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>參數

*T*<br/>
來自 的`CAtlModuleT`類 派生自 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlModuleT:CAtlModuleT](#catlmodulet)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Catlmodulet::InitLibId](#initlibid)|初始化包含當前模組 GUID 的數據成員。|
|[CAtlModuleT::註冊應用程式](#registerappid)|將 EXE 添加到註冊表。|
|[CAtlModuleT::註冊伺服器](#registerserver)|將服務添加到註冊表。|
|[CAtlModuleT::未註冊AppId](#unregisterappid)|從註冊表中刪除 EXE。|
|[CAtlModuleT::未註冊伺服器](#unregisterserver)|從註冊表中刪除服務。|
|[CAtlModuleT::更新註冊應用程式](#updateregistryappid)|更新註冊表中的 EXE 資訊。|

## <a name="remarks"></a>備註

`CAtlModuleT`,派生自[CAtlModule](../../atl/reference/catlmodule-class.md), 實現可執行 (EXE) 或服務 (EXE) ATL 模組。 可執行模組是本地、程序外伺服器,而服務模組是 Windows 應用程式,在 Windows 啟動時在後台運行。

`CAtlModuleT`支援模組的初始化、註冊和取消註冊。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT:CAtlModuleT

建構函式。

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>備註

呼叫[Catlmodulet:initLibId](#initlibid)。

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>Catlmodulet::InitLibId

初始化包含當前模組 GUID 的數據成員。

```
static void InitLibId() throw();
```

### <a name="remarks"></a>備註

由建構函數[CAtlModuleT 呼叫:CAtlModuleT](#catlmodulet)。

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::註冊應用程式

將 EXE 添加到註冊表。

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::註冊伺服器

將服務添加到註冊表。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型庫,則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要註冊的物件的 CLSID。 如果 NULL(預設值),則將註冊物件映射中的所有物件。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::未註冊AppId

從註冊表中刪除 EXE。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::未註冊伺服器

從註冊表中刪除服務。

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果類型庫也要取消註冊,則為 TRUE。

*pCLSID*<br/>
指向要未註冊的物件的 CLSID。 如果 NULL(預設值),則物件映射中的所有物件都將取消註冊。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::更新註冊應用程式

更新註冊表中的 EXE 資訊。

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>參數

*b 註冊*<br/>
已保留。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[CAtlModule 類別](../../atl/reference/catlmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)
