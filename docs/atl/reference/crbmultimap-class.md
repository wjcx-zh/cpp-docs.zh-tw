---
title: CRBMultiMap 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec016df268b702fd8b26d742d702ac38b95fa06
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="crbmultimap-class"></a>CRBMultiMap 類別
此類別代表可讓每個索引鍵可以是多個值，並使用 紅黑二進位樹狀目錄相關聯的對應結構。  
  
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|建構函式。|  
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|呼叫這個方法的第一個元素的位置找不到指定的索引鍵。|  
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|呼叫這個方法，取得與指定索引鍵相關聯的值，並更新位置值。|  
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|呼叫這個方法，取得與指定索引鍵相關聯的項目，並更新位置值。|  
|[CRBMultiMap::Insert](#insert)|呼叫這個方法來插入對應中的項目組。|  
|[CRBMultiMap::RemoveKey](#removekey)|呼叫這個方法來移除所有索引鍵/值項目，指定索引鍵。|  
  
## <a name="remarks"></a>備註  
 `CRBMultiMap` 提供任何指定的型別，在管理索引鍵的元素和值的已排序的陣列的對應陣列的支援。 不同於[CRBMap](../../atl/reference/crbmap-class.md)類別，每個索引鍵可以是多個值相關聯。  
  
 （組成的索引鍵和值） 的項目會儲存在二進位樹狀目錄結構，使用[CRBMultiMap::Insert](#insert)方法。 可以使用 移除項目[CRBMultiMap::RemoveKey](#removekey)方法，刪除所有符合指定的索引鍵的項目。  
  
 周遊樹狀結構可能.remove 方法，進行這類[CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition)， [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)，和[CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)。 存取多個值可能會每個索引鍵可能使用[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)， [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，和[CRBMultiMap::GetNextWithKey](#getnextwithkey)方法。 請參閱範例的[CRBMultiMap::CRBMultiMap](#crbmultimap)如需這個練習中的圖例。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的 traits 類別。  
  
 `CRBMultiMap` 衍生自[CRBTree](../../atl/reference/crbtree-class.md)，它會實作使用紅黑演算法在二進位樹狀目錄。 替代`CRBMultiMap`和`CRBMap`提供[CAtlMap](../../atl/reference/catlmap-class.md)類別。 當只有少數的項目都必須儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 如需更完整討論各種不同的集合類別和其功能和效能特性，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMultiMap`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap  
 建構函式。  
  
```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，呼叫，但使用較多資源。 預設會配置空間的 10 個項目一次。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]  
  
##  <a name="dtor"></a>  CRBMultiMap:: ~ CRBMultiMap  
 解構函式。  
  
```
~CRBMultiMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey  
 呼叫這個方法的第一個元素的位置找不到指定的索引鍵。  
  
```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別要尋找的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果找到機碼，NULL 否則會傳回第一個索引鍵/值項目的位置。  
  
### <a name="remarks"></a>備註  
 中的索引鍵`CRBMultiMap`可以有一或多個相關聯的值。 這個方法會提供該特定索引鍵相關聯的第一個值 （這可能會事實上，是唯一的值） 的位置值。 傳回的位置值可以再搭配[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)取得值，並更新位置。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey  
 呼叫這個方法，取得與指定的索引鍵相關聯的值，並更新位置值。  
  
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
 取得要呼叫的位置值， [CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextWithKey](#getnextwithkey)，或先前呼叫`GetNextValueWithKey`。  
  
 `key`  
 指定識別要尋找的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回與指定的索引鍵相關聯的項目組。  
  
### <a name="remarks"></a>備註  
 位置值會更新為指向下一個索引鍵相關聯的值。 如果沒有更多的值存在，位置值設為 NULL。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey  
 呼叫這個方法，取得與指定的索引鍵相關聯的項目，並更新位置值。  
  
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
 取得要呼叫的位置值， [CRBMultiMap::FindFirstWithKey](#findfirstwithkey)或[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)，或先前呼叫`GetNextWithKey`。  
  
 `key`  
 指定識別要尋找的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回下一個[CRBTree::CPair 類別](crbtree-class.md#cpair_class)給定索引鍵相關聯的項目。  
  
### <a name="remarks"></a>備註  
 位置值會更新為指向下一個索引鍵相關聯的值。 如果沒有更多的值存在，位置值設為 NULL。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
##  <a name="insert"></a>  CRBMultiMap::Insert  
 呼叫這個方法來插入對應中的項目組。  
  
```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CRBMultiMap`物件。  
  
 *值*  
 要加入值`CRBMultiMap`與相關聯的物件`key`。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CRBMultiMap`物件。  
  
### <a name="remarks"></a>備註  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
##  <a name="removekey"></a>  CRBMultiMap::RemoveKey  
 呼叫這個方法來移除所有索引鍵/值項目，指定索引鍵。  
  
```
size_t RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別要刪除的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回與指定的索引鍵相關聯的值數目。  
  
### <a name="remarks"></a>備註  
 `RemoveKey` 刪除所有具有相符索引鍵之索引鍵/值項目的`key`。  
  
 請參閱基底類別的文件[CRBTree](../../atl/reference/crbtree-class.md)提供之其他方法的資訊。  
  
### <a name="example"></a>範例  
 請參閱範例的[CRBMultiMap::CRBMultiMap](#crbmultimap)。  
  
## <a name="see-also"></a>另請參閱  
 [CRBTree 類別](../../atl/reference/crbtree-class.md)   
 [CAtlMap 類別](../../atl/reference/catlmap-class.md)   
 [CRBMap 類別](../../atl/reference/crbmap-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
