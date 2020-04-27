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
ms.openlocfilehash: 5cdf13ebbb982ad8184a52dcf1a3e30d71e4e5b0
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167704"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 類別

這個類別會提供 ATL 視窗化元件的支援。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
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

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

這個方法會初始化並加入`_AtlCreateWndData`結構。

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>參數

*pData*<br/>
要初始化並`_AtlCreateWndData`加入至目前模組之結構的指標。

*pObject*<br/>
指向物件**this**指標的指標。

### <a name="remarks"></a>備註

這個方法會呼叫初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) 。 這個結構會儲存**this**指標，用來取得視窗程式中的類別實例。

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

建構函式。

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>備註

如果初始化失敗，則會引發**EXCEPTION_NONCONTINUABLE**例外狀況。

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule：： ~ CAtlWinModule

解構函式。

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

這個方法會傳回`_AtlCreateWndData`結構的指標。

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>傳回值

傳回先前使用`_AtlCreateWndData` [CAtlWinModule：： AddCreateWndData](#addcreatewnddata)加入之結構的指標，如果沒有可用的物件，則傳回 Null。

## <a name="see-also"></a>另請參閱

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
