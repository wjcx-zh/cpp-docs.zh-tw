---
title: 屬性對應巨集
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
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326096"
---
# <a name="property-map-macros"></a>屬性對應巨集

這些宏定義屬性映射和條目。

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|標記 ATL 屬性映射的開頭。|
|[PROP_DATA_ENTRY](#prop_data_entry)|指示 ActiveX 控制件的範圍或尺寸。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|在屬性映射中輸入屬性說明、屬性 DISPID 和屬性頁 CLSID。|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|在屬性映射中輸入屬性說明、屬性 DISPID、屬性`IDispatch`頁 CLSID 和 IID。|
|[PROP_PAGE](#prop_page)|在屬性映射中輸入屬性頁 CLSID。|
|[END_PROP_MAP](#end_prop_map)|標記 ATL 屬性映射的末尾。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

標記物件屬性映射的開頭。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]指定包含屬性對應的類別。

### <a name="remarks"></a>備註

屬性映射儲存屬性描述、屬性 DISPID、屬性頁 CLSID 和`IDispatch`ID。 類[IPerProperty瀏覽](../../atl/reference/iperpropertybrowsingimpl-class.md)Impl、IPersistPropertyBagimpl、IPersistStreamInitimpl[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)和[I指定屬性PagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)使用屬性映射來檢索和設置此資訊[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)。

使用 ATL 專案精靈建立物件時,向導將通過指定BEGIN_PROP_MAP後跟[END_PROP_MAP](#end_prop_map)創建空屬性映射。

BEGIN_PROP_MAP不會保存屬性映射的範圍(即維度),因為使用屬性映射的物件可能沒有用戶介面,因此它將沒有範圍。 如果物件是具有使用者介面的 ActiveX 控制項,則具有擴充區。 在這種情況下,必須在屬性映射中指定[PROP_DATA_ENTRY](#prop_data_entry)以提供範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

指示 ActiveX 控制件的範圍或尺寸。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>參數

*什德斯茨*<br/>
[在]屬性描述。

*成員*<br/>
[在]包含範圍的數據成員;例如, `m_sizeExtent`.

*vt*<br/>
[在]指定屬性的 VARIANT 類型。

### <a name="remarks"></a>備註

此宏會導致保留指定的數據成員。

創建 ActiveX 控制件時,嚮導在屬性映射宏[BEGIN_PROP_MAP](#begin_prop_map)和屬性映射宏[END_PROP_MAP](#end_prop_map)之前插入此宏。

### <a name="example"></a>範例

在下面的範例中,物件(`m_sizeExtent`) 的範圍正在持久化。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

使用此宏在物件的屬性映射中輸入屬性說明、屬性 DISPID 和屬性頁 CLSID。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>參數

*什德斯茨*<br/>
[在]屬性描述。

*不一部分*<br/>
[在]酒店的 DISPID。

*Clsid*<br/>
[在]關聯屬性頁的 CLSID。 對於沒有關聯屬性頁的屬性,請使用特殊值CLSID_NULL。

*vt*<br/>
[在]屬性的類型。

### <a name="remarks"></a>備註

PROP_ENTRY宏不安全且棄用。 它已替換為PROP_ENTRY_TYPE。

[BEGIN_PROP_MAP](#begin_prop_map)宏標記屬性映射的開頭;[END_PROP_MAP](#end_prop_map)宏標記結束。

### <a name="example"></a>範例

請參閱[BEGIN_PROP_MAP](#begin_prop_map)的示例。

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

與[PROP_ENTRY_TYPE](#prop_entry_type)類似 ,但允許您指定特定的 IID,如果物件支援多個雙介面。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>參數

*什德斯茨*<br/>
[在]屬性描述。

*不一部分*<br/>
[在]酒店的 DISPID。

*Clsid*<br/>
[在]關聯屬性頁的 CLSID。 對於沒有關聯屬性頁的屬性,請使用特殊值CLSID_NULL。

*iidDispatch*<br/>
[在]定義屬性的雙介面的 IID。

*vt*<br/>
[在]屬性的類型。

### <a name="remarks"></a>備註

PROP_ENTRY_EX宏不安全且棄用。 它已被替換為PROP_ENTRY_TYPE_EX。

[BEGIN_PROP_MAP](#begin_prop_map)宏標記屬性映射的開頭;[END_PROP_MAP](#end_prop_map)宏標記結束。

### <a name="example"></a>範例

以下示例將 條目分`IMyDual1`組 ,`IMyDual2`後跟 的條目。 按雙介面分組將提高性能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

使用此宏將屬性頁 CLSID 輸入到物件的屬性對應中。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>參數

*Clsid*<br/>
[在]屬性頁的 CLSID。

### <a name="remarks"></a>備註

PROP_PAGE與[PROP_ENTRY_TYPE](#prop_entry_type)類似,但不需要屬性描述或 DISPID。

> [!NOTE]
> 如果您已輸入具有PROP_ENTRY_TYPE或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)的 CLSID,則無需使用PROP_PAGE進行附加條目。

[BEGIN_PROP_MAP](#begin_prop_map)宏標記屬性映射的開頭;[END_PROP_MAP](#end_prop_map)宏標記結束。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

標記物件的屬性映射的末尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>備註

使用 ATL 專案精靈建立物件時,向導將透過指定[BEGIN_PROP_MAP](#begin_prop_map)後跟END_PROP_MAP創建空屬性映射。

### <a name="example"></a>範例

請參閱[BEGIN_PROP_MAP](#begin_prop_map)的示例。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
