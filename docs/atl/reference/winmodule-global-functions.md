---
title: WinModule 全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1f1dcb325f8844a74b3dd831a51050083e7ea552
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834397"
---
# <a name="winmodule-global-functions"></a>WinModule 全域函式

這些函數會提供 `_AtlCreateWndData` 結構作業的支援。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a> AtlWinModuleAddCreateWndData

此函式是用來初始化及加入 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
模組 [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) 結構的指標。

*.Pdata*<br/>
要初始化並加入至目前模組的 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) 結構指標。

*pObject*<br/>
物件指標的指標 **`this`** 。

### <a name="remarks"></a>備註

初始化 `_AtlCreateWndData` 結構，這個結構是用來儲存 **`this`** 用來參考類別實例的指標，並將它加入至模組結構所參考的清單 `_ATL_WIN_MODULE70` 。 由 [CAtlWinModule：： AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)呼叫。

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a> AtlWinModuleExtractCreateWndData

呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
模組 [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) 結構的指標。

### <a name="return-value"></a>傳回值

傳回 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) 結構的指標。

### <a name="remarks"></a>備註

此函數會 `_AtlCreateWndData` 從模組結構所參考的清單中，將現有的結構解壓縮 `_ATL_WIN_MODULE70` 。

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
