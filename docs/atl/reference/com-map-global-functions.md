---
title: COM 對應全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: 9f3f5e1c5ec1d845962783b8768404a89727edc8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458782"
---
# <a name="com-map-global-functions"></a>COM 對應全域函式

這些函式會提供 COM 對應中的支援`IUnknown`實作。

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委派給`IUnknown`的非彙總的物件。|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|會產生有效率的程式碼，來比較介面的`IUnknown`。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

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
[in]包含的介面公開至 COM 對應物件的指標`QueryInterface`。

*pEntries*<br/>
[in]陣列`_ATL_INTMAP_ENTRY`存取的可用的介面對應的結構。

*iid*<br/>
[in]所要求介面的 GUID。

*ppvObject*<br/>
[out]在指定的介面指標的指標*iid*，或如果找不到介面則為 NULL。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

`AtlInternalQueryInterface` 只處理 COM 對應表格中的介面。 如果您的物件已彙總，`AtlInternalQueryInterface`不會不會委派給外部未知。 您可以將介面輸入到 COM 對應表格巨集[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其中一個變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

呼叫此函式的特殊案例的測試`IUnknown`。

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>參數

*rguid1*<br/>
[in]比較 GUID `IID_IUnknown`。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[COM 對應巨集](../../atl/reference/com-map-macros.md)
