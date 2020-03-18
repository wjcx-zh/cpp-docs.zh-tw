---
title: CAtlWinModule 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418024"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 類別

這個類別會提供 ATL 視窗化元件的支援。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|建構函式。|
|[CAtlWinModule：： ~ CAtlWinModule](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|加入資料物件。|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|傳回 window 模組資料物件的指標。|

## <a name="remarks"></a>備註

這個類別可支援所有需要視窗化功能的 ATL 類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

這個方法會初始化並加入 `_AtlCreateWndData` 結構。

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>參數

*pData*<br/>
要初始化並加入至目前模組之 `_AtlCreateWndData` 結構的指標。

*pObject*<br/>
指向物件**this**指標的指標。

### <a name="remarks"></a>備註

這個方法會呼叫初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) 。 這個結構會儲存**this**指標，用來取得視窗程式中的類別實例。

##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

建構函式。

```
CAtlWinModule();
```

### <a name="remarks"></a>備註

如果初始化失敗，則會引發**EXCEPTION_NONCONTINUABLE**例外狀況。

##  <a name="dtor"></a>CAtlWinModule：： ~ CAtlWinModule

解構函式。

```
~CAtlWinModule();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

這個方法會傳回 `_AtlCreateWndData` 結構的指標。

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>傳回值

傳回先前以[CAtlWinModule：： AddCreateWndData](#addcreatewnddata)加入之 `_AtlCreateWndData` 結構的指標，如果沒有可用的物件，則傳回 Null。

## <a name="see-also"></a>另請參閱

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
