---
title: WinModule 全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1a929fd0f583150e84ce5b1efa7e896bc16e4247
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229931"
---
# <a name="winmodule-global-functions"></a>WinModule 全域函式

這些函式會提供 `_AtlCreateWndData` 結構作業的支援。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

此函式是用來初始化及加入 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
模組的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構的指標。

*pData*<br/>
要初始化並加入至目前模組之[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的指標。

*pObject*<br/>
物件指標的指標 **`this`** 。

### <a name="remarks"></a>備註

初始化 `_AtlCreateWndData` 結構，用來儲存 **`this`** 用來參考類別實例的指標，並將它加入至模組結構所參考的清單 `_ATL_WIN_MODULE70` 。 由[CAtlWinModule：： AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)呼叫。

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
模組的[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構的指標。

### <a name="return-value"></a>傳回值

傳回[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的指標。

### <a name="remarks"></a>備註

此函式會 `_AtlCreateWndData` 從模組結構所參考的清單中，將現有的結構解壓縮 `_ATL_WIN_MODULE70` 。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
