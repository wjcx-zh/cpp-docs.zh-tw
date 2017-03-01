---
title: "屬性對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fbbed22766f9029456f15c4a554ae91322e6a275
ms.lasthandoff: 02/24/2017

---
# <a name="property-map-macros"></a>屬性對應巨集
這些巨集定義的對應屬性和項目。  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|標記的 ATL 屬性對應的開頭。|  
|[PROP_DATA_ENTRY](#prop_data_entry)|表示的範圍或維度，ActiveX 控制項。|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|輸入屬性對應的屬性描述、 屬性的 DISPID，與屬性頁的 CLSID。|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|輸入屬性描述，屬性 CLSID、 屬性頁的 DISPID 和`IDispatch`屬性對應到 IID。|  
|[PROP_PAGE](#prop_page)|輸入屬性對應的屬性頁的 CLSID。|  
|[END_PROP_MAP](#end_prop_map)|ATL 屬性對應結束標記。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
   
##  <a name="a-namebeginpropmapa--beginpropmap"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 標記物件的屬性對應的開頭。  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]指定包含屬性對應的類別。  
  
### <a name="remarks"></a>備註  
 屬性對應會儲存屬性描述，屬性 Dispid，屬性頁的 Clsid，和`IDispatch`Iid。 類別[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)用於擷取和設定這項資訊的屬性對應。  
  
 當您使用 ATL 專案精靈 」 建立的物件時，精靈會建立空白的屬性對應藉由指定`BEGIN_PROP_MAP`後面[END_PROP_MAP](#end_prop_map)。  
  
 `BEGIN_PROP_MAP`不會儲存出屬性對應的範圍 （亦即，維度），因為使用屬性對應的物件沒有使用者介面，因此它會不有任何範圍。 如果物件是 ActiveX 控制項與使用者介面，其範圍。 在此情況下，您必須指定[PROP_DATA_ENTRY](#prop_data_entry)屬性對應至提供範圍中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&103;](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="a-namepropdataentrya--propdataentry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 表示的範圍或維度，ActiveX 控制項。  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>參數  
 `szDesc`  
 [in]屬性描述。  
  
 `member`  
 [in]包含範圍; 之資料成員例如， `m_sizeExtent`。  
  
 *vt*  
 [in]指定屬性的 VARIANT 型別。  
  
### <a name="remarks"></a>備註  
 這個巨集將會導致要保存的指定的資料成員。  
  
 當您建立 ActiveX 控制項時，精靈就會將這個巨集之後屬性對應巨集[BEGIN_PROP_MAP](#begin_prop_map)屬性對應巨集之前[END_PROP_MAP](#end_prop_map)。  
  
### <a name="example"></a>範例  
 在下列範例中，物件的範圍 ( `m_sizeExtent`) 會被保存。  
  
 [!code-cpp[NVC_ATL_Windowing #&131;](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&132;](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="a-namepropentrytypea--propentrytype"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 您可以使用這個巨集輸入物件的屬性對應的屬性描述、 屬性的 DISPID，與屬性頁的 CLSID。  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>參數  
 `szDesc`  
 [in]屬性描述。  
  
 `dispid`  
 [in]屬性的 DISPID。  
  
 `clsid`  
 [in]相關聯的屬性頁的 CLSID。 使用特殊值`CLSID_NULL`沒有相關聯的屬性頁的屬性。  
  
 `vt`  
 [in]屬性的型別。  
  
### <a name="remarks"></a>備註  
 `PROP_ENTRY`巨集就是受到保護，且已被取代。 已被取代`PROP_ENTRY_TYPE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
##  <a name="a-namepropentrytypeexa--propentrytypeex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 類似於[PROP_ENTRY_TYPE](#prop_entry_type)，但可以讓您指定特定的 IID，如果物件支援多個雙重介面。  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>參數  
 `szDesc`  
 [in]屬性描述。  
  
 `dispid`  
 [in]屬性的 DISPID。  
  
 `clsid`  
 [in]相關聯的屬性頁的 CLSID。 使用特殊值`CLSID_NULL`沒有相關聯的屬性頁的屬性。  
  
 `iidDispatch`  
 [in]定義該屬性的雙重介面的 IID。  
  
 `vt`  
 [in]屬性的型別。  
  
### <a name="remarks"></a>備註  
 `PROP_ENTRY_EX`巨集就是受到保護，且已被取代。 已被取代`PROP_ENTRY_TYPE_EX`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 下列範例將群組項目`IMyDual1`後面的項目`IMyDual2`。 雙重介面的群組將可改善效能。  
  
 [!code-cpp[NVC_ATL_Windowing #&133;](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="a-nameproppagea--proppage"></a><a name="prop_page"></a>PROP_PAGE  
 您可以使用這個巨集輸入物件的屬性對應的屬性頁的 CLSID。  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in]屬性頁的 CLSID。  
  
### <a name="remarks"></a>備註  
 `PROP_PAGE`類似於[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的屬性描述或 DISPID。  
  
> [!NOTE]
>  如果您已經輸入 CLSID`PROP_ENTRY_TYPE`或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，您不需要建立與其他項目`PROP_PAGE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&134;](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="a-nameendpropmapa--endpropmap"></a><a name="end_prop_map"></a>END_PROP_MAP  
 標記物件的屬性對應的結尾。  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>備註  
 當您使用 ATL 專案精靈 」 建立的物件時，精靈會建立空白的屬性對應藉由指定[BEGIN_PROP_MAP](#begin_prop_map)後面`END_PROP_MAP`。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

