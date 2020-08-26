---
title: 屬性對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 5e14c3cb82b9b7527ed8af42e181581097218360
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834667"
---
# <a name="property-map-macros"></a>屬性對應宏

這些宏會定義屬性對應和專案。

|名稱|描述|
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|標記 ATL 屬性對應的開頭。|
|[PROP_DATA_ENTRY](#prop_data_entry)|指出 ActiveX 控制項的範圍或維度。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|在屬性對應中輸入屬性描述、屬性 DISPID 和屬性頁 CLSID。|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|在屬性對應中輸入屬性描述、屬性 DISPID、屬性頁 CLSID 和 `IDispatch` IID。|
|[PROP_PAGE](#prop_page)|在屬性對應中輸入屬性頁 CLSID。|
|[END_PROP_MAP](#end_prop_map)|標記 ATL 屬性對應的結尾。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a> BEGIN_PROP_MAP

標記物件的屬性對應開頭。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
在指定包含屬性對應的類別。

### <a name="remarks"></a>備註

屬性對應會儲存屬性描述、屬性 Dispid、屬性頁 Clsid 和 `IDispatch` iid。 類別 [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)、 [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)、 [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)和 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 會使用屬性對應來取得和設定這類資訊。

當您使用 [ATL 專案嚮導] 建立物件時，Wizard 會指定 BEGIN_PROP_MAP 後接著 [END_PROP_MAP](#end_prop_map)，以建立空的屬性對應。

BEGIN_PROP_MAP 不會將範圍 (也就是屬性對應的維度) ，因為使用屬性對應的物件可能沒有使用者介面，所以不會有任何範圍。 如果物件是具有使用者介面的 ActiveX 控制項，它會有一個範圍。 在此情況下，您必須在屬性對應中指定 [PROP_DATA_ENTRY](#prop_data_entry) ，以提供範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a> PROP_DATA_ENTRY

指出 ActiveX 控制項的範圍或維度。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>參數

*szDesc*<br/>
在屬性描述。

*成員*<br/>
在包含範圍的資料成員;例如， `m_sizeExtent` 。

*vt*<br/>
在指定屬性的 VARIANT 類型。

### <a name="remarks"></a>備註

此宏會保存指定的資料成員。

當您建立 ActiveX 控制項時，wizard 會在屬性對應宏 [BEGIN_PROP_MAP](#begin_prop_map) 之後，以及屬性對應宏 [END_PROP_MAP](#end_prop_map)之前，插入這個宏。

### <a name="example"></a>範例

在下列範例中，會保存物件 () 的範圍 `m_sizeExtent` 。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a> PROP_ENTRY_TYPE

使用這個宏可將屬性描述、屬性 DISPID 和屬性頁 CLSID 輸入至物件的屬性對應。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>參數

*szDesc*<br/>
在屬性描述。

*dispid*<br/>
在屬性的 DISPID。

*Clsid*<br/>
在相關聯之屬性頁的 CLSID。 針對沒有相關聯屬性頁的屬性，請使用 [特殊值 CLSID_Null]。

*vt*<br/>
在屬性的類型。

### <a name="remarks"></a>備註

PROP_ENTRY 宏不安全且已被取代。 它已被 PROP_ENTRY_TYPE 取代。

[BEGIN_PROP_MAP](#begin_prop_map)宏會標示屬性對應的開頭;[END_PROP_MAP](#end_prop_map)宏會標示結尾。

### <a name="example"></a>範例

請參閱 [BEGIN_PROP_MAP](#begin_prop_map)的範例。

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a> PROP_ENTRY_TYPE_EX

類似于 [PROP_ENTRY_TYPE](#prop_entry_type)，但如果您的物件支援多個雙重介面，則可讓您指定特定的 IID。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>參數

*szDesc*<br/>
在屬性描述。

*dispid*<br/>
在屬性的 DISPID。

*Clsid*<br/>
在相關聯之屬性頁的 CLSID。 針對沒有相關聯屬性頁的屬性，請使用 [特殊值 CLSID_Null]。

*iidDispatch*<br/>
在定義屬性之雙重介面的 IID。

*vt*<br/>
在屬性的類型。

### <a name="remarks"></a>備註

PROP_ENTRY_EX 宏不安全且已被取代。 它已被 PROP_ENTRY_TYPE_EX 取代。

[BEGIN_PROP_MAP](#begin_prop_map)宏會標示屬性對應的開頭;[END_PROP_MAP](#end_prop_map)宏會標示結尾。

### <a name="example"></a>範例

下列範例會將 `IMyDual1` 後面接著專案的專案分組 `IMyDual2` 。 依雙重介面進行分組將可改善效能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a> PROP_PAGE

使用此宏在物件的屬性對應中輸入屬性頁 CLSID。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>參數

*Clsid*<br/>
在屬性頁的 CLSID。

### <a name="remarks"></a>備註

PROP_PAGE 類似 [PROP_ENTRY_TYPE](#prop_entry_type)，但不需要屬性描述或 DISPID。

> [!NOTE]
> 如果您已經使用 PROP_ENTRY_TYPE 或 [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)輸入 CLSID，則不需要使用 PROP_PAGE 建立額外的專案。

[BEGIN_PROP_MAP](#begin_prop_map)宏會標示屬性對應的開頭;[END_PROP_MAP](#end_prop_map)宏會標示結尾。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a> END_PROP_MAP

標記物件的屬性對應結尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>備註

當您使用 [ATL 專案嚮導] 建立物件時，Wizard 會指定 [BEGIN_PROP_MAP](#begin_prop_map) 後接著 END_PROP_MAP，以建立空的屬性對應。

### <a name="example"></a>範例

請參閱 [BEGIN_PROP_MAP](#begin_prop_map)的範例。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
