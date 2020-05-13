---
title: CAtlBaseModule 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168289"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule 類別

這個類別會在每個 ATL 專案中具現化。

## <a name="syntax"></a>語法

```cpp
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|將資源實例加入至預存控制碼清單。|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|傳回指定之資源實例的控制碼。|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|從`CAtlBaseModule`物件傳回模組實例。|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|從`CAtlBaseModule`物件傳回資源實例。|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|從預存控制碼清單中移除資源實例。|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|設定`CAtlBaseModule`物件的資源實例。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlBaseModule：： m_bInitFailed](#m_binitfailed)|指出模組初始化是否失敗的變數。|

## <a name="remarks"></a>備註

`CAtlBaseModule`名為 _AtlBaseModule 的實例存在於每個 ATL 專案中，其中包含模組實例的控制碼、包含資源之模組的控制碼（預設為一個和相同的），以及提供主要資源的模組控制碼陣列。 `CAtlBaseModule`可以安全地從多個執行緒存取。

這個類別會取代舊版 ATL 中使用的過時[CComModule](../../atl/reference/ccommodule-class.md)類別。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

將資源實例加入至預存控制碼清單。

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
要加入的資源實例。

### <a name="return-value"></a>傳回值

如果成功新增資源，則傳回 true，否則傳回 false。

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

建構函式。

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>備註

建立 `CAtlBaseModule`。

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

傳回指定之資源實例的控制碼。

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>參數

*怎樣*<br/>
資源實例的編號。

### <a name="return-value"></a>傳回值

傳回資源實例的控制碼，如果沒有對應的資源實例存在，則傳回 Null。

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

從`CAtlBaseModule`物件傳回模組實例。

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>傳回值

傳回模組實例。

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

傳回資源實例。

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>傳回值

傳回資源實例。

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule：： m_bInitFailed

指出模組初始化是否失敗的變數。

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>備註

如果模組已初始化，則為 True，如果無法初始化，則為 false。

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

從預存控制碼清單中移除資源實例。

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
要移除的資源實例。

### <a name="return-value"></a>傳回值

如果已成功移除資源，則傳回 true，否則傳回 false。

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

設定`CAtlBaseModule`物件的資源實例。

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
新的資源實例。

### <a name="return-value"></a>傳回值

傳回已更新的資源實例。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
