---
title: "CRBMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3cfa4d6fff6b46341f01b4d5ce18d9ec418738bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crbmap-class"></a>CRBMap 類別
此類別代表對應結構，使用 紅黑二進位樹狀目錄。  
  
## <a name="syntax"></a>語法  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>參數  
 `K`  
 索引鍵的項目類型。  
  
 *V*  
 值的項目型別。  
  
 `KTraits`  
 程式碼，用來複製或移動的索引鍵項目。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
 `VTraits`  
 用於複製或移動的項目值的程式碼。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|建構函式。|  
|[CRBMap:: ~ CRBMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|呼叫這個方法來查詢索引鍵或值`CRBMap`物件。|  
|[CRBMap::RemoveKey](#removekey)|呼叫這個方法來移除的項目從`CRBMap`物件，指定的索引鍵。|  
|[CRBMap::SetAt](#setat)|呼叫這個方法來插入對應中的項目組。|  
  
## <a name="remarks"></a>備註  
 `CRBMap`提供任何指定的型別，在管理索引鍵的項目和其關聯的值的已排序的陣列的對應陣列的支援。 每個索引鍵可以有只有一個相關聯的值。 （組成的索引鍵和值） 的項目會儲存在二進位樹狀目錄結構，使用[CRBMap::SetAt](#setat)方法。 可以使用 移除項目[CRBMap::RemoveKey](#removekey)方法，刪除具有指定索引鍵值的項目。  
  
 周遊樹狀結構可能.remove 方法，進行這類[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的 traits 類別。  
  
 `CRBMap`衍生自[CRBTree](../../atl/reference/crbtree-class.md)，它會實作使用紅黑演算法在二進位樹狀目錄。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是一種變化，可讓每個索引鍵的多個值。 它太衍生自`CRBTree`，並因此共用許多功能與`CRBMap`。  
  
 兩者的替代方式`CRBMap`和`CRBMultiMap`提供[CAtlMap](../../atl/reference/catlmap-class.md)類別。 當只有少數的項目都必須儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 如需更完整討論各種不同的集合類別和其功能和效能特性，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 建構函式。  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，呼叫，但使用較多資源。 預設會配置空間的 10 個項目一次。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap:: ~ CRBMap  
 解構函式。  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 呼叫這個方法來查詢索引鍵或值`CRBMap`物件。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別的項目是要查閱的索引鍵。  
  
 *值*  
 收到的查詢上值的變數。  
  
### <a name="return-value"></a>傳回值  
 第一種形式的方法會傳回 true，如果找到機碼，否則為 false。 第二個和第三個表單傳回的指標[CPair](crbtree-class.md#cpair_class)。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 呼叫這個方法來移除的項目從`CRBMap`物件，指定的索引鍵。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 您想要移除對應的項目組。  
  
### <a name="return-value"></a>傳回值  
 如果機碼找到並移除，失敗則為 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 呼叫這個方法來插入對應中的項目組。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CRBMap`物件。  
  
 *值*  
 要加入值`CRBMap`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CRBMap`物件。  
  
### <a name="remarks"></a>備註  
 `SetAt`如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，則會建立新的索引鍵/值組。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [CRBTree 類別](../../atl/reference/crbtree-class.md)   
 [CAtlMap 類別](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap 類別](../../atl/reference/crbmultimap-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
