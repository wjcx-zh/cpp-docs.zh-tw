---
title: CAtlCom 模組類別
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
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321474"
---
# <a name="catlcommodule-class"></a>CAtlCom 模組類別

此類實現 COM 伺服器模組。

## <a name="syntax"></a>語法

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlCom 模組:CAtlcom 模組](#catlcommodule)|建構函式。|
|[CAtlCom 模組:_CAtlCom 模組](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlCom 模組::註冊伺服器](#registerserver)|調用此方法以更新物件映射中每個物件的系統註冊表。|
|[CAtlCom 模組::註冊類型 Lib](#registertypelib)|調用此方法以註冊類型庫。|
|[CAtlCom 模組::未註冊伺服器](#unregisterserver)|調用此方法以取消註冊物件映射中的每個物件。|
|[CAtlCom 模組::未註冊類型 Lib](#unregistertypelib)|調用此方法以取消註冊類型庫。|

## <a name="remarks"></a>備註

`CAtlComModule`實現 COM 伺服器模組,允許用戶端訪問模組的元件。

此類將替換早期版本的 ATL 中使用的過時的[CComModule](../../atl/reference/ccommodule-class.md)類。 有關詳細資訊,請參閱[ATL 模組課程](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlCom 模組:CAtlcom 模組

建構函式。

```
CAtlComModule() throw();
```

### <a name="remarks"></a>備註

初始化模組。

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlCom 模組:_CAtlCom 模組

解構函式。

```
~CAtlComModule();
```

### <a name="remarks"></a>備註

解放所有類工廠。

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlCom 模組::註冊伺服器

調用此方法以更新物件映射中每個物件的系統註冊表。

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型庫,則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要註冊的物件的 CLSID。 如果 NULL(預設值),則將註冊物件映射中的所有物件。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫全域函數[Atlcommodule 註冊伺服器](server-registration-global-functions.md#atlcommoduleregisterserver)。

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlCom 模組::註冊類型 Lib

調用此方法以註冊類型庫。

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
格式為"\N"\\的字串,其中 N 是 TYPELIB 資源的整數索引。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

將有關類型庫的資訊添加到系統註冊表。 如果模組實例包含多個類型庫,請使用此方法的第一個版本指定應使用的類型庫。

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlCom 模組::未註冊伺服器

調用此方法以取消註冊物件映射中的每個物件。

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果類型庫要未註冊,則為 TRUE。 預設值為 FALSE。

*pCLSID*<br/>
指向要未註冊的物件的 CLSID。 如果 NULL(預設值),則物件映射中的所有物件都將取消註冊。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫全域函數[AtlcomModuleUn寄存器伺服器](server-registration-global-functions.md#atlcommoduleunregisterserver)。

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlCom 模組::未註冊類型 Lib

調用此方法以取消註冊類型庫。

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
格式為"\N"\\的字串,其中 N 是 TYPELIB 資源的整數索引。

### <a name="remarks"></a>備註

從系統註冊表中刪除有關類型庫的資訊。 如果模組實例包含多個類型庫,請使用此方法的第一個版本指定應使用的類型庫。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="see-also"></a>另請參閱

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[類別概觀](../../atl/atl-class-overview.md)
