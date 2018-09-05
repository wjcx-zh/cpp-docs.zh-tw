---
title: 屬性對應巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf82c48cb5b1f9bd93a9c30afe8c698699c8199b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758088"
---
# <a name="property-map-macros"></a>屬性對應巨集

這些巨集會定義屬性對應 」 和 「 項目。

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|標記的 ATL 屬性對應的開頭。|
|[PROP_DATA_ENTRY](#prop_data_entry)|表示範圍或 ActiveX 控制項的維度。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|輸入屬性對應中的屬性描述、 屬性的 DISPID，與屬性頁 CLSID。|
|[改用 PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|輸入屬性描述，屬性的 DISPID，屬性頁 CLSID、 和`IDispatch`屬性對應至 IID。|
|[PROP_PAGE](#prop_page)|輸入屬性對應中的屬性頁 CLSID。|
|[END_PROP_MAP](#end_prop_map)|結束標記的 ATL 屬性對應。|  

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

標記物件的屬性對應的開頭。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*  
[in]指定包含屬性對應的類別。

### <a name="remarks"></a>備註

屬性對應儲存屬性說明，屬性的 Dispid，屬性頁 Clsid、 和`IDispatch`Iid。 類別[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)使用屬性對應，以擷取和設定這項資訊。

當您使用 ATL 專案精靈 建立物件時，此精靈會建立空的屬性對應藉由指定後面的 BEGIN_PROP_MAP [END_PROP_MAP](#end_prop_map)。

BEGIN_PROP_MAP 不會儲存出範圍 （也就是維度） 的屬性對應，因為使用的屬性對應的物件可能沒有使用者介面，因此它會不有任何範圍。 如果物件是具有使用者介面的 ActiveX 控制項，它會有範圍。 在此情況下，您必須指定[PROP_DATA_ENTRY](#prop_data_entry)屬性對應至提供的範圍中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

表示範圍或 ActiveX 控制項的維度。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>參數

*szDesc*  
[in]屬性描述。

*成員*  
[in]包含範圍; 的資料成員比方說， `m_sizeExtent`。

*vt*  
[in]指定之屬性的 VARIANT 類型。

### <a name="remarks"></a>備註

這個巨集，會導致要保存的指定的資料成員。

當您建立 ActiveX 控制項時，此精靈之後，屬性對應巨集插入這個巨集[BEGIN_PROP_MAP](#begin_prop_map)並在 屬性對應巨集之前[END_PROP_MAP](#end_prop_map)。

### <a name="example"></a>範例

在下列範例中，物件的範圍 (`m_sizeExtent`) 會被保存。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

您可以使用這個巨集輸入物件的屬性對應的屬性描述、 屬性的 DISPID，與屬性頁 CLSID。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>參數

*szDesc*  
[in]屬性描述。

*dispid*  
[in]屬性的 DISPID。

*clsid*  
[in]相關聯的屬性頁的 CLSID。 使用特殊值 CLSID_NULL 並沒有相關聯的屬性頁的屬性。

*vt*  
[in]屬性的型別。

### <a name="remarks"></a>備註

PROP_ENTRY 巨集已受到保護，且已被取代。 已被取代 PROP_ENTRY_TYPE。

[BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭，而[END_PROP_MAP](#end_prop_map)巨集標記結尾。

### <a name="example"></a>範例

範例，請參閱[BEGIN_PROP_MAP](#begin_prop_map)。

##  <a name="prop_entry_type_ex"></a>  改用 PROP_ENTRY_TYPE_EX

類似於[PROP_ENTRY_TYPE](#prop_entry_type)，但可讓您指定特定的 IID，如果物件支援多個雙重介面。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>參數

*szDesc*  
[in]屬性描述。

*dispid*  
[in]屬性的 DISPID。

*clsid*  
[in]相關聯的屬性頁的 CLSID。 使用特殊值 CLSID_NULL 並沒有相關聯的屬性頁的屬性。

*iidDispatch*  
[in]定義該屬性的雙重介面的 IID。

*vt*  
[in]屬性的型別。

### <a name="remarks"></a>備註

PROP_ENTRY_EX 巨集已受到保護，且已被取代。 它有已改用 PROP_ENTRY_TYPE_EX 取代。

[BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭，而[END_PROP_MAP](#end_prop_map)巨集標記結尾。

### <a name="example"></a>範例

下列範例中群組項目`IMyDual1`後面的項目`IMyDual2`。 雙重介面的群組會改善效能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

您可以使用這個巨集輸入物件的屬性對應的屬性頁 CLSID。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>參數

*clsid*  
[in]屬性頁 CLSID。

### <a name="remarks"></a>備註

PROP_PAGE 大致[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的屬性描述或 DISPID。

> [!NOTE]
>  如果您已輸入 PROP_ENTRY_TYPE CLSID 或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，您不需要建立 PROP_PAGE 與其他項目。

[BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭，而[END_PROP_MAP](#end_prop_map)巨集標記結尾。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

標記物件的屬性對應的結尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>備註

當您使用 ATL 專案精靈 建立物件時，此精靈會藉由指定建立空的屬性對應[BEGIN_PROP_MAP](#begin_prop_map)後面 END_PROP_MAP。

### <a name="example"></a>範例

範例，請參閱[BEGIN_PROP_MAP](#begin_prop_map)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
