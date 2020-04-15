---
title: COM 對應全域函數
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326687"
---
# <a name="com-map-global-functions"></a>COM 對應全域函數

這些函數為 COM`IUnknown`映射 實現提供支援。

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委託給`IUnknown`非聚合物件的。|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|生成用於比較介面與`IUnknown`的有效代碼。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>atl 內部查詢介面

擷取所要求介面的指標。

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*p*<br/>
[在]指向物件的指標,其中包含向 公開的介面的 COM`QueryInterface`映射 。

*p 項目*<br/>
[在]訪問可用介面`_ATL_INTMAP_ENTRY`對應的結構陣組。

*Iid*<br/>
[在]請求的介面的 GUID。

*ppvObject*<br/>
[出]指向*iid*中指定的介面指標,如果找不到介面,則指向 NULL 中的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

`AtlInternalQueryInterface` 只處理 COM 對應表格中的介面。 如果物件是聚合的,`AtlInternalQueryInterface`則不委託給外部未知物件。 您可以使用巨[集COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其變體之一在 COM 地圖表中輸入介面。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>內聯不相等

調用此函數,用於測試`IUnknown`的特殊情況。

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>參數

*rguid1*<br/>
[在]要與`IID_IUnknown`的GUID進行比較。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[COM 對應巨集](../../atl/reference/com-map-macros.md)
