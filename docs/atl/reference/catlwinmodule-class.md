---
title: CAtlWin 模組類
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
ms.openlocfilehash: 40385fd592563837546b483bb80978cde6a56555
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321266"
---
# <a name="catlwinmodule-class"></a>CAtlWin 模組類

此類支援 ATL 視窗元件。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlWin 模組:CAtlWin 模組](#catlwinmodule)|建構函式。|
|[CAtlWin 模組:*CAtlWin 模組](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlWin模組::添加創建WndData](#addcreatewnddata)|添加數據物件。|
|[CAtlWin 模組::提取創建WndData](#extractcreatewnddata)|返回指向視窗模塊數據物件的指標。|

## <a name="remarks"></a>備註

此類支援所有需要視窗功能的 ATL 類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWin模組::添加創建WndData

此方法初始化和添加`_AtlCreateWndData`結構。

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>參數

*pData*<br/>
指向要初始`_AtlCreateWndData`化並添加到當前模組的結構的指標。

*pObject*<br/>
指向物件的**此**指標。

### <a name="remarks"></a>備註

此方法調用[AtlWinModuleAddCreatewnddata,該資料](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata)初始化了[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構。 此結構將存儲**此**指標,用於在視窗過程中獲取類實例。

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWin 模組:CAtlWin 模組

建構函式。

```
CAtlWinModule();
```

### <a name="remarks"></a>備註

如果初始化失敗,將引發**EXCEPTION_NONCONTINUABLE**異常。

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWin 模組:*CAtlWin 模組

解構函式。

```
~CAtlWinModule();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWin 模組::提取創建WndData

此方法返回指向結構的`_AtlCreateWndData`指標。

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>傳回值

返回指向以前添加的`_AtlCreateWndData` [CAtlWinModule::addCreateWndData](#addcreatewnddata)()或 NULL(如果沒有可用物件)的結構的指標。

## <a name="see-also"></a>另請參閱

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)
