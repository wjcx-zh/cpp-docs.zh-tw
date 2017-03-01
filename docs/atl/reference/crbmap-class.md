---
title: "CRBMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CRBMap
- CRBMap
- ATL::CRBMap
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7b1cd9e54a18746e26929e9768a990bbe0ba6553
ms.lasthandoff: 02/24/2017

---
# <a name="crbmap-class"></a>CRBMap 類別
此類別代表對應的結構，使用 紅黑二進位樹狀目錄。  
  
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
 索引鍵的項目型別。  
  
 *V*  
 值的項目型別。  
  
 `KTraits`  
 若要複製或移動索引鍵的項目使用的程式碼。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
 `VTraits`  
 用於複製或移動的項目值的程式碼。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|建構函式。|  
|[CRBMap:: ~ CRBMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|呼叫這個方法來查詢索引鍵或值`CRBMap`物件。|  
|[CRBMap::RemoveKey](#removekey)|呼叫此方法以移除項目從`CRBMap`指定索引鍵的物件。|  
|[CRBMap::SetAt](#setat)|呼叫這個方法來插入對應的項目組。|  
  
## <a name="remarks"></a>備註  
 `CRBMap`任何指定的型別，管理已排序的陣列的索引鍵的項目和其關聯的值的對應陣列提供支援。 每個金鑰都可以有只有一個相關聯的值。 項目 （包含索引鍵和值） 會儲存在二進位樹狀目錄結構，使用[CRBMap::SetAt](#setat)方法。 可以移除項目，使用[CRBMap::RemoveKey](#removekey)方法，刪除具有指定索引鍵的項目。  
  
 周遊樹狀結構可使用方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的特性類別。  
  
 `CRBMap`衍生自[CRBTree](../../atl/reference/crbtree-class.md)，可用來實作使用紅黑演算法的二進位樹狀結構。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是一種變化，可讓每個索引鍵的多個值。 它也衍生自`CRBTree`，並因此共用許多功能與`CRBMap`。  
  
 兩者的替代方案`CRBMap`和`CRBMultiMap`指由[CAtlMap](../../atl/reference/catlmap-class.md)類別。 當只有少數項目都必須儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 不同的集合類別及其功能和效能特性的更完整討論，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="a-namecrbmapa--crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap  
 建構函式。  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，但使用較多資源。 預設會配置空間的 10 個項目一次。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&81;](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="a-namedtora--crbmapcrbmap"></a><a name="dtor"></a>CRBMap:: ~ CRBMap  
 解構函式。  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
##  <a name="a-namelookupa--crbmaplookup"></a><a name="lookup"></a>CRBMap::Lookup  
 呼叫這個方法來查詢索引鍵或值`CRBMap`物件。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別的項目是要查閱的索引鍵。  
  
 *value*  
 接收查詢最多值的變數。  
  
### <a name="return-value"></a>傳回值  
 第一種形式的方法會傳回 true，如果找到索引鍵為，否則為 false。 第二個和第三個表單傳回的指標[CPair](crbtree-class.md#cpair_class)。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&82;](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="a-nameremovekeya--crbmapremovekey"></a><a name="removekey"></a>CRBMap::RemoveKey  
 呼叫此方法以移除項目從`CRBMap`指定索引鍵的物件。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 您想要移除對應的項目組。  
  
### <a name="return-value"></a>傳回值  
 如果機碼找到並移除，失敗則為 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&83;](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="a-namesetata--crbmapsetat"></a><a name="setat"></a>CRBMap::SetAt  
 呼叫這個方法來插入對應的項目組。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CRBMap`物件。  
  
 *value*  
 要加入至值`CRBMap`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CRBMap`物件。  
  
### <a name="remarks"></a>備註  
 `SetAt`如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，會建立新的索引鍵/值組。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&84;](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CRBTree 類別](../../atl/reference/crbtree-class.md)   
 [CAtlMap 類別](../../atl/reference/catlmap-class.md)   
 [CRBMultiMap 類別](../../atl/reference/crbmultimap-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

