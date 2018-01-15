---
title: "屬性對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs: C++
helpviewer_keywords: property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfd99fa59fc5e1d97011ac3dba4d16dd222c35b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="property-map-macros"></a>屬性對應巨集
這些巨集會定義對應屬性和項目。  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|將 ATL 屬性對應的開頭的標記。|  
|[PROP_DATA_ENTRY](#prop_data_entry)|指示的範圍或維度，ActiveX 控制項。|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|輸入的屬性對應中的屬性描述、 屬性的 DISPID 與屬性頁 CLSID。|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|輸入屬性描述，DISPID，屬性頁 CLSID、 屬性和`IDispatch`屬性對應至 IID。|  
|[PROP_PAGE](#prop_page)|屬性對應到輸入屬性頁 CLSID。|  
|[END_PROP_MAP](#end_prop_map)|ATL 屬性對應結束標記。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
   
##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 標記物件的屬性對應的開頭。  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]指定包含屬性對應的類別。  
  
### <a name="remarks"></a>備註  
 屬性對應會儲存屬性描述，屬性 Dispid，屬性頁 Clsid，和`IDispatch`Iid。 類別[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)來擷取及設定這項資訊使用的屬性對應。  
  
 當您建立的物件使用 ATL 專案精靈 」 時，精靈會建立空白的屬性對應藉由指定`BEGIN_PROP_MAP`後面[END_PROP_MAP](#end_prop_map)。  
  
 `BEGIN_PROP_MAP`不會儲存外範圍 （亦即，維度） 的屬性對應，因為使用屬性對應的物件可能沒有使用者介面，因此它會不有任何範圍。 如果物件是以使用者介面的 ActiveX 控制項，其範圍。 在此情況下，您必須指定[PROP_DATA_ENTRY](#prop_data_entry)屬性對應至提供的範圍中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 指示的範圍或維度，ActiveX 控制項。  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>參數  
 `szDesc`  
 [in]屬性描述。  
  
 `member`  
 [in]包含範圍; 之資料成員例如， `m_sizeExtent`。  
  
 *vt*  
 [in]指定屬性的 VARIANT 類型。  
  
### <a name="remarks"></a>備註  
 這個巨集將會導致要保存的指定的資料成員。  
  
 當您建立 ActiveX 控制項時，精靈會將這個巨集插入屬性對應巨集後面[BEGIN_PROP_MAP](#begin_prop_map)和屬性對應巨集前面[END_PROP_MAP](#end_prop_map)。  
  
### <a name="example"></a>範例  
 在下列範例中，物件的範圍 ( `m_sizeExtent`) 會被保存。  
  
 [!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 若要將屬性描述、 屬性的 DISPID 與屬性頁 CLSID 輸入物件的屬性對應中使用這個巨集。  
  
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
 `PROP_ENTRY`巨集是不安全，並且已被取代。 取代為`PROP_ENTRY_TYPE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_PROP_MAP](#begin_prop_map)。  
  
##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
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
 [in]定義屬性的雙重介面的 IID。  
  
 `vt`  
 [in]屬性的型別。  
  
### <a name="remarks"></a>備註  
 `PROP_ENTRY_EX`巨集是不安全，並且已被取代。 取代為`PROP_ENTRY_TYPE_EX`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 下列範例會分組為的項目`IMyDual1`後面的項目`IMyDual2`。 雙重介面的群組可改進效能。  
  
 [!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="prop_page"></a>PROP_PAGE  
 若要將屬性頁 CLSID 輸入物件的屬性對應中使用這個巨集。  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in]屬性頁 CLSID。  
  
### <a name="remarks"></a>備註  
 `PROP_PAGE`類似於[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的屬性描述或 DISPID。  
  
> [!NOTE]
>  如果您已輸入 CLSID`PROP_ENTRY_TYPE`或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，您不需要建立其他項目與`PROP_PAGE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)巨集標記的屬性對應的開頭; [END_PROP_MAP](#end_prop_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="end_prop_map"></a>END_PROP_MAP  
 結束標記的物件的屬性對應。  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>備註  
 當您建立的物件使用 ATL 專案精靈 」 時，精靈會建立空白的屬性對應藉由指定[BEGIN_PROP_MAP](#begin_prop_map)後面`END_PROP_MAP`。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_PROP_MAP](#begin_prop_map)。  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)
