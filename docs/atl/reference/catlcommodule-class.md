---
title: CAtlComModule 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863159"
---
# <a name="catlcommodule-class"></a>CAtlComModule 類別

這個類別會實行 COM 伺服器模組。

## <a name="syntax"></a>語法

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|建構函式。|
|[CAtlComModule：： ~ CAtlComModule](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|呼叫這個方法，以更新物件對應中每個物件的系統登錄。|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|呼叫這個方法來註冊類型程式庫。|
|[CAtlComModule::UnregisterServer](#unregisterserver)|呼叫這個方法，以取消註冊物件對應中的每個物件。|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|呼叫此方法可取消註冊類型程式庫。|

## <a name="remarks"></a>備註

`CAtlComModule` 會執行 COM 伺服器模組，讓用戶端可以存取模組的元件。

這個類別會取代舊版 ATL 中使用的過時[CComModule](../../atl/reference/ccommodule-class.md)類別。 如需詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule

建構函式。

```
CAtlComModule() throw();
```

### <a name="remarks"></a>備註

初始化模組。

##  <a name="dtor"></a>CAtlComModule：： ~ CAtlComModule

解構函式。

```
~CAtlComModule();
```

### <a name="remarks"></a>備註

釋放所有 class factory。

##  <a name="registerserver"></a>CAtlComModule::RegisterServer

呼叫這個方法，以更新物件對應中每個物件的系統登錄。

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型程式庫，則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要註冊之物件的 CLSID。 如果為 Null （預設值），則會註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫全域函式[AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)。

##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

呼叫這個方法來註冊類型程式庫。

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
格式為 "\\\N" 的字串，其中 N 是 TYPELIB 資源的整數索引。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

將類型程式庫的相關資訊新增至系統登錄。 如果模組實例包含多個類型程式庫，請使用這個方法的第一個版本來指定應該使用的類型程式庫。

##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer

呼叫這個方法，以取消註冊物件對應中的每個物件。

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要將類型程式庫取消註冊，則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要取消註冊之物件的 CLSID。 如果為 Null （預設值），則會取消註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫全域函式[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)。

##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

呼叫此方法可取消註冊類型程式庫。

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
格式為 "\\\N" 的字串，其中 N 是 TYPELIB 資源的整數索引。

### <a name="remarks"></a>備註

從系統登錄移除類型程式庫的相關資訊。 如果模組實例包含多個類型程式庫，請使用這個方法的第一個版本來指定應該使用的類型程式庫。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[類別總覽](../../atl/atl-class-overview.md)
