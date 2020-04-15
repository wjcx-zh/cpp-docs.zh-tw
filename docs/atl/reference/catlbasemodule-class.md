---
title: CAtlBase 模組類別
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
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321501"
---
# <a name="catlbasemodule-class"></a>CAtlBase 模組類別

此類在每個 ATL 專案中都實例化。

## <a name="syntax"></a>語法

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlBase模組:CAtlBase模組](#catlbasemodule)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlBase模組::新增資源實例](#addresourceinstance)|將資源實例添加到存儲句柄清單中。|
|[CAtlBase模組::取得實例](#gethinstanceat)|將句柄返回到指定的資源實例。|
|[CAtlBase模組:取得模組實例](#getmoduleinstance)|從`CAtlBaseModule`物件返回模組實例。|
|[CAtlBase 模組:抓取資源實體](#getresourceinstance)|從`CAtlBaseModule`物件返回資源實例。|
|[CAtlBase 模組::刪除資源實例](#removeresourceinstance)|從儲存句柄清單中刪除資源實例。|
|[CAtlBase 模組::設定資源實例](#setresourceinstance)|設置`CAtlBaseModule`物件的資源實例。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlBase模組::m_bInitFailed](#m_binitfailed)|指示模組初始化是否失敗的變數。|

## <a name="remarks"></a>備註

每個 ATL 專案中都存在命名`CAtlBaseModule`_AtlBaseModule的 實例,其中包含模組實例的句柄、包含資源(預設情況下為相同)的模組句柄以及提供主資源的模組的句柄陣列。 `CAtlBaseModule`可以從多個線程安全地訪問。

此類將替換早期版本的 ATL 中使用的過時的[CComModule](../../atl/reference/ccommodule-class.md)類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBase模組::新增資源實例

將資源實例添加到存儲句柄清單中。

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
要添加的資源實例。

### <a name="return-value"></a>傳回值

如果資源已成功添加,則返回 true,否則為 false。

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBase模組:CAtlBase模組

建構函式。

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>備註

建立 `CAtlBaseModule`。

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBase模組::取得實例

將句柄返回到指定的資源實例。

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>參數

*I.*<br/>
資源實例的編號。

### <a name="return-value"></a>傳回值

如果不存在相應的資源實例,則將句柄返回給資源實例,或返回 NULL。

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBase模組:取得模組實例

從`CAtlBaseModule`物件返回模組實例。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>傳回值

返回模組實例。

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBase 模組:抓取資源實體

返回資源實例。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>傳回值

返回資源實例。

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBase模組::m_bInitFailed

指示模組初始化是否失敗的變數。

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>備註

如果模組初始化為 True,則為 false,如果模組未能初始化。"

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBase 模組::刪除資源實例

從儲存句柄清單中刪除資源實例。

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
要刪除的資源實例。

### <a name="return-value"></a>傳回值

如果資源已成功刪除,則返回 true,否則為 false。

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBase 模組::設定資源實例

設置`CAtlBaseModule`物件的資源實例。

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>參數

*hInst*<br/>
新資源實例。

### <a name="return-value"></a>傳回值

返回更新的資源實例。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)
