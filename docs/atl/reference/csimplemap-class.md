---
title: "CSimpleMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMap
- ATL.CSimpleMap
- CSimpleMap
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 21
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
ms.openlocfilehash: c02ef1d9d3fafebf38abaaa55d77511f4476a02f
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemap-class"></a>CSimpleMap 類別
這個類別會提供簡單對應陣列的支援。  
  
## <a name="syntax"></a>語法  
  
```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>  
class CSimpleMap
```  
  
#### <a name="parameters"></a>參數  
 `TKey`  
 索引鍵的項目型別。  
  
 `TVal`  
 值的項目型別。  
  
 `TEqual`  
 定義項目類型的等號比較測試特性物件`T`。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|實值類型的 Typedef。|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|索引鍵類型的 Typedef。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|建構函式。|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|將索引鍵和相關聯的值加入至對應陣列中。|  
|[CSimpleMap::FindKey](#findkey)|尋找特定的索引鍵。|  
|[CSimpleMap::FindVal](#findval)|尋找特定的值。|  
|[CSimpleMap::GetKeyAt](#getkeyat)|擷取指定之索引鍵。|  
|[CSimpleMap::GetSize](#getsize)|傳回對應陣列中的項目數。|  
|[CSimpleMap::GetValueAt](#getvalueat)|擷取指定的值。|  
|[CSimpleMap::Lookup](#lookup)|傳回指定索引鍵相關聯的值。|  
|[CSimpleMap::Remove](#remove)|移除索引鍵和值相符。|  
|[CSimpleMap::RemoveAll](#removeall)|移除所有索引鍵和值。|  
|[CSimpleMap::RemoveAt](#removeat)|移除特定索引鍵和值相符。|  
|[CSimpleMap::ReverseLookup](#reverselookup)|傳回給定值相關聯的金鑰。|  
|[CSimpleMap::SetAt](#setat)|設定指定的索引鍵相關聯的值。|  
|[CSimpleMap::SetAtIndex](#setatindex)|設定特定索引鍵和值。|  
  
## <a name="remarks"></a>備註  
 `CSimpleMap`支援任何指定類型的簡單對應陣列`T`，管理未排序的索引鍵的項目和其關聯的值陣列。  
  
 參數`TEqual`提供一種定義兩個項目類型的等號比較函式`T`。 建立類別類似於[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，就可以變更任何指定之陣列的等號比較測試的行為。 例如，處理時的指標陣列，可能可以定義為相等，取決於指標參考的值。 預設實作會利用**operator==()**。  
  
 同時`CSimpleMap`和[CSimpleArray](../../atl/reference/csimplearray-class.md)釋放先前 ATL 與相容性，而提供更完整且有效的集合實作會提供[CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)。  
  
 不同於其他 ATL 和 MFC 中的對應集合，這個類別簡單的陣列，以實作和查詢搜尋需要線性搜尋。 `CAtlMap`陣列會包含大量項目時，應該使用。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpcoll.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&91;](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]  
  
##  <a name="a-nameadda--csimplemapadd"></a><a name="add"></a>CSimpleMap::Add  
 將索引鍵和相關聯的值加入至對應陣列中。  
  
```
BOOL Add(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 索引鍵。  
  
 *val*  
 相關聯的值。  
  
### <a name="return-value"></a>傳回值  
 如果索引鍵和值已成功新增，則為 FALSE 否則為 true，則傳回。  
  
### <a name="remarks"></a>備註  
 每個索引鍵和值組加入對應陣列的記憶體被釋放並重新配置，以確保每個資料一律連續儲存的原因。 也就是說，第二個索引鍵的項目一律直接會遵循在記憶體中的第一個索引鍵的元素，依此類推。  
  
##  <a name="a-namearrayelementtypea--csimplemaparrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType  
 索引鍵類型的 typedef。  
  
```
typedef TVal _ArrayElementType;
```  
  
##  <a name="a-namearraykeytypea--csimplemaparraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType  
 實值型別之 typedef。  
  
```
typedef TKey _ArrayKeyType;
```  
  
##  <a name="a-namecsimplemapa--csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap  
 建構函式。  
  
```
CSimpleMap();
```  
  
### <a name="remarks"></a>備註  
 資料成員初始化。  
  
##  <a name="a-namedtora--csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap:: ~ CSimpleMap  
 解構函式。  
  
```
~CSimpleMap();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="a-namefindkeya--csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey  
 尋找特定的索引鍵。  
  
```
int FindKey(const TKey& key) const;
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要搜尋的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回的索引鍵，如果找到，否則會傳回-1。  
  
##  <a name="a-namefindvala--csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal  
 尋找特定的值。  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>參數  
 *val*  
 要搜尋值。  
  
### <a name="return-value"></a>傳回值  
 傳回值的索引找到它，否則傳回-1。  
  
##  <a name="a-namegetkeyata--csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt  
 擷取指定索引處的索引鍵。  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要傳回之索引鍵索引。  
  
### <a name="return-value"></a>傳回值  
 傳回所參考的索引鍵`nIndex`。  
  
### <a name="remarks"></a>備註  
 所傳遞的索引`nIndex`必須是有效的傳回值為有意義。  
  
##  <a name="a-namegetsizea--csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize  
 傳回對應陣列中的項目數。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>傳回值  
 對應陣列中傳回的項目數 （索引鍵和值是一個項目）。  
  
##  <a name="a-namegetvalueata--csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt  
 擷取特定索引處的值。  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要傳回之值的索引。  
  
### <a name="return-value"></a>傳回值  
 傳回所參考的值`nIndex`。  
  
### <a name="remarks"></a>備註  
 所傳遞的索引`nIndex`必須是有效的傳回值為有意義。  
  
##  <a name="a-namelookupa--csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup  
 傳回指定索引鍵相關聯的值。  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>參數  
 `key`  
 索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回相關聯的值。 如果沒有相符的索引鍵找不到 NULL 會傳回。  
  
##  <a name="a-nameremovea--csimplemapremove"></a><a name="remove"></a>CSimpleMap::Remove  
 移除索引鍵和值相符。  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 索引鍵。  
  
### <a name="return-value"></a>傳回值  
 如果索引鍵和相符的值，已成功移除，則為 FALSE 否則為 true，則傳回。  
  
##  <a name="a-nameremovealla--csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll  
 移除所有索引鍵和值。  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 移除對應陣列物件的所有索引鍵和值。  
  
##  <a name="a-nameremoveata--csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt  
 移除機碼和相關聯的值，指定索引處。  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 金鑰和相關聯的值，若要移除的索引。  
  
### <a name="return-value"></a>傳回值  
 為 true，則傳回 FALSE 如果成功，如果指定的索引是無效的索引。  
  
##  <a name="a-namereverselookupa--csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup  
 傳回給定值相關聯的金鑰。  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>參數  
 *val*  
 數值。  
  
### <a name="return-value"></a>傳回值  
 傳回相關聯的索引鍵。 如果沒有相符的索引鍵找不到 NULL 會傳回。  
  
##  <a name="a-namesetata--csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt  
 設定指定的索引鍵相關聯的值。  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 索引鍵。  
  
 *val*  
 若要指派新值。  
  
### <a name="return-value"></a>傳回值  
 如果找不到索引鍵和值程式已成功變更，則為 FALSE，傳回 TRUE。  
  
##  <a name="a-namesetatindexa--csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex  
 設定指定索引處的索引鍵和值。  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 參考的索引鍵和值配對來變更索引。  
  
 `key`  
 新的索引鍵。  
  
 *val*  
 新值。  
  
### <a name="return-value"></a>傳回值  
 如果，傳回 TRUE 成功，則為 FALSE 如果索引不正確。  
  
### <a name="remarks"></a>備註  
 更新索引鍵和值所指`nIndex`。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

