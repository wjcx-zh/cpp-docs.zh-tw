---
title: "CRBMultiMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
dev_langs:
- C++
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: a72ddfbf4944f0de5e979f7046872d594017b9cf
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="crbmultimap-class"></a>CRBMultiMap 類別
此類別代表可讓每個索引鍵可以是多個值，使用 紅黑二進位樹狀目錄相關聯的對應結構。  
  
## <a name="syntax"></a>語法  
  
```
template<typename K,
         typename V, 
         class KTraits = CElementTraits<K>, 
         class VTraits = CElementTraits<V>>  
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|建構函式。|  
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|呼叫這個方法來尋找具有指定索引鍵的第一個項目的位置。|  
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|呼叫這個方法來取得與指定索引鍵相關聯的值，並更新位置值。|  
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|呼叫這個方法來取得與指定索引鍵相關聯的項目，並更新位置值。|  
|[CRBMultiMap::Insert](#insert)|呼叫這個方法來插入對應的項目組。|  
|[CRBMultiMap::RemoveKey](#removekey)|呼叫此方法以移除所有指定的索引鍵的索引鍵/值項目。|  
  
## <a name="remarks"></a>備註  
 `CRBMultiMap`任何指定的型別，管理已排序的陣列的索引鍵的項目和值的對應陣列提供支援。 不同於[CRBMap](../../atl/reference/crbmap-class.md)類別中，每個索引鍵可以是多個值相關聯。  
  
 項目 （包含索引鍵和值） 會儲存在二進位樹狀目錄結構，使用[CRBMultiMap::Insert](#insert)方法。 可以移除項目，使用[CRBMultiMap::RemoveKey](#removekey)方法，刪除所有符合指定的索引鍵的項目。  
  
 周遊樹狀結構可使用方法如[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。 存取多個值可能每個索引鍵儘可能使用[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)， [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，和[CRBMultiMap::GetNextWithKey](#getnextwithkey)方法。 請參閱範例[CRBMultiMap::CRBMultiMap](#crbmultimap)實際上這的範例。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的特性類別。  
  
 `CRBMultiMap`衍生自[CRBTree](../../atl/reference/crbtree-class.md)，可用來實作使用紅黑演算法的二進位樹狀結構。 除了`CRBMultiMap`和`CRBMap`指由[CAtlMap](../../atl/reference/catlmap-class.md)類別。 當只有少數項目都必須儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 不同的集合類別及其功能和效能特性的更完整討論，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap  
 建構函式。  
  
```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，但使用較多資源。 預設會配置空間的 10 個項目一次。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&85;](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMultiMap:: ~ CRBMultiMap  
 解構函式。  
  
```
~CRBMultiMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
##  <a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey  
 呼叫這個方法來尋找具有指定索引鍵的第一個項目的位置。  
  
```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別要找的項目之索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果找到索引鍵時，NULL 否則會傳回第一個索引鍵/值項目的位置。  
  
### <a name="remarks"></a>備註  
 中的索引鍵`CRBMultiMap`可以有一或多個相關聯的值。 這個方法會提供該特定索引鍵相關聯的第一個值 （這可能，事實上，唯一的值） 的位置值。 傳回的位置值可以再搭配[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)取得值，並更新的位置。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 請參閱範例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey  
 呼叫這個方法來取得與指定的索引鍵相關聯的值，並更新位置值。  
  
```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 取得要呼叫的位置值， [CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)，或前一次呼叫`GetNextValueWithKey`。  
  
 `key`  
 指定識別要找的項目之索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回指定索引鍵相關聯的項目組。  
  
### <a name="remarks"></a>備註  
 位置值會更新為指向下一個索引鍵相關聯的值。 如果沒有更多的值存在，位置值是設為 NULL。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 請參閱範例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey  
 呼叫這個方法來取得與指定的索引鍵相關聯的項目，並更新位置值。  
  
```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 取得要呼叫的位置值， [CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，或前一次呼叫`GetNextWithKey`。  
  
 `key`  
 指定識別要找的項目之索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回下一個[CRBTree::CPair 類別](crbtree-class.md#cpair_class)給定的索引鍵相關聯的項目。  
  
### <a name="remarks"></a>備註  
 位置值會更新為指向下一個索引鍵相關聯的值。 如果沒有更多的值存在，位置值是設為 NULL。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
##  <a name="insert"></a>CRBMultiMap::Insert  
 呼叫這個方法來插入對應的項目組。  
  
```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CRBMultiMap`物件。  
  
 *value*  
 要加入至值`CRBMultiMap`與相關聯的物件`key`。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CRBMultiMap`物件。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 請參閱範例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="removekey"></a>CRBMultiMap::RemoveKey  
 呼叫此方法以移除所有指定的索引鍵的索引鍵/值項目。  
  
```
size_t RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別要刪除的項目之索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回指定索引鍵相關聯的值數目。  
  
### <a name="remarks"></a>備註  
 `RemoveKey`刪除所有具有相符的索引鍵的索引鍵/值項目`key`。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)如需可用的其他方法。  
  
### <a name="example"></a>範例  
 請參閱範例[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
## <a name="see-also"></a>另請參閱  
 [CRBTree 類別](../../atl/reference/crbtree-class.md)   
 [CAtlMap 類別](../../atl/reference/catlmap-class.md)   
 [CRBMap 類別](../../atl/reference/crbmap-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

