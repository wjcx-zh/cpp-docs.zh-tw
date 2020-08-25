---
title: COM 對應全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: adf4e06eb46aed74d08071dccce1db549ca31226
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833591"
---
# <a name="com-map-global-functions"></a>COM 對應全域函式

這些函式提供 COM 對應執行的支援 `IUnknown` 。

|函式|描述|
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委派至 `IUnknown` 非匯總物件的。|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|產生用來比較介面的有效率程式碼 `IUnknown` 。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a> AtlInternalQueryInterface

擷取所要求介面的指標。

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*pThis*<br/>
在物件的指標，該物件包含公開之介面的 COM 對應 `QueryInterface` 。

*pEntries*<br/>
在結構的陣列 `_ATL_INTMAP_ENTRY` ，可存取可用介面的對應。

*Iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
擴展 *Iid*中指定之介面指標的指標，如果找不到介面，則為 Null。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`AtlInternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件已匯總，則 `AtlInternalQueryInterface` 不會委派給外部未知。 您可以使用宏 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 或其中一個變體來輸入 COM map 資料表中的介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a> InlineIsEqualIUnknown

針對的特殊測試案例，呼叫此函式 `IUnknown` 。

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>參數

*rguid1*<br/>
在要比較的 GUID `IID_IUnknown` 。

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[COM 對應宏](../../atl/reference/com-map-macros.md)
