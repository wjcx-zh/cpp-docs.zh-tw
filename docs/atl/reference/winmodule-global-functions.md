---
title: WinModule 全球功能
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329353"
---
# <a name="winmodule-global-functions"></a>WinModule 全球功能

這些函數為`_AtlCreateWndData`結構操作提供支援。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreatewndData

此函式是用來初始化及加入 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
指向模組[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構的指標。

*pData*<br/>
指向要初始化並添加到當前模組[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的指標。

*pObject*<br/>
指向物件的**此**指標。

### <a name="remarks"></a>備註

初始化`_AtlCreateWndData`結構,用於存儲用於引用類實例`_ATL_WIN_MODULE70`的**此**指標,並將其添加到模塊結構引用的清單。 由[CAtlWinModule 呼叫::新增建立WndData](catlwinmodule-class.md#addcreatewnddata)。

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModule提取建立WndD資料

呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>參數

*pWinModule*<br/>
指向模組[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構的指標。

### <a name="return-value"></a>傳回值

返回指向[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構的指標。

### <a name="remarks"></a>備註

此函數將從模組`_AtlCreateWndData``_ATL_WIN_MODULE70`結構引用的清單中提取現有結構。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
