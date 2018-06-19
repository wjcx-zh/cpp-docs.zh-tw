---
title: CSimpleArray 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187dee79cd09e366fb56d9cd0e71395589476a69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364260"
---
# <a name="csimplearray-class"></a>CSimpleArray 類別
這個類別會提供管理簡單陣列的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 陣列中儲存的資料類型。  
  
 `TEqual`  
 定義項目類型的等號比較測試特性物件`T`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|簡單陣列建構函式。|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|簡單陣列解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|將新的項目加入至陣列。|  
|[CSimpleArray::Find](#find)|陣列中尋找的項目。|  
|[CSimpleArray::GetData](#getdata)|傳回陣列中儲存的資料指標。|  
|[CSimpleArray::GetSize](#getsize)|傳回儲存在陣列中元素數目。|  
|[CSimpleArray::Remove](#remove)|從陣列中移除指定的項目。|  
|[CSimpleArray::RemoveAll](#removeall)|從陣列中移除所有項目。|  
|[CSimpleArray::RemoveAt](#removeat)|從陣列中移除指定的項目。|  
|[CSimpleArray::SetAtIndex](#setatindex)|指定的元素設定陣列中。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|從陣列中擷取項目。|  
|[CSimpleArray::operator =](#operator_eq)|指派運算子。|  

  
## <a name="remarks"></a>備註  
 `CSimpleArray` 提供方法來建立及管理簡單的陣列，任何給定的類型`T`。  
  
 參數`TEqual`提供一種定義兩個項目類型的等號比較函式`T`。 藉由建立類別類似於[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，便可變更任何指定之陣列的等號比較測試的行為。 例如，當處理指標的陣列，可能很有用來定義為相等，取決於指標所參考的值。 預設實作會利用**operator=()**。  
  
 同時`CSimpleArray`和[CSimpleMap](../../atl/reference/csimplemap-class.md)專為小型的元素數目。 [CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)此陣列包含大量項目時，應使用。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpcoll.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="add"></a>  CSimpleArray::Add  
 將新的項目加入至陣列。  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>參數  
 *t*  
 要加入至陣列的項目。  
  
### <a name="return-value"></a>傳回值  
 如果項目已成功新增到陣列，FALSE 否則為 true，則傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray  
 陣列物件的建構函式。  
  
```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```     
  
### <a name="parameters"></a>參數  
 *src*  
 現有的 `CSimpleArray` 物件。  
  
### <a name="remarks"></a>備註  
 初始化資料成員，建立新的空白`CSimpleArray`物件或將現有的複本`CSimpleArray`物件。  
  
##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray  
 解構函式。  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="find"></a>  CSimpleArray::Find  
 陣列中尋找的項目。  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>參數  
 *t*  
 要搜尋項目。  
  
### <a name="return-value"></a>傳回值  
 傳回找到的項目，則為-1 的索引; 如果找不到項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="getdata"></a>  CSimpleArray::GetData  
 傳回陣列中儲存的資料指標。  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回陣列中的資料指標。  
  
##  <a name="getsize"></a>  CSimpleArray::GetSize  
 傳回儲存在陣列中元素數目。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在陣列中元素數目。  
  
##  <a name="operator_at"></a>  CSimpleArray::operator \[\]  
 從陣列中擷取項目。  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 項目索引。  
  
### <a name="return-value"></a>傳回值  
 傳回所參考的陣列的項目`nIndex`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="operator_eq"></a>  CSimpleArray::operator =  
 指派運算子。  
  
```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```  
  
### <a name="parameters"></a>參數  
 *src*  
 要複製的陣列。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到更新`CSimpleArray`物件。  
  
### <a name="remarks"></a>備註  
 複製所有項目從`CSimpleArray`所參考物件*src*成目前的陣列物件，取代所有現有的資料。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="remove"></a>  CSimpleArray::Remove  
 從陣列中移除指定的項目。  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>參數  
 *t*  
 要從陣列中移除的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回為 true，則如果項目因找到並移除，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 移除項目時，重新編號陣列中其餘的項目以填滿空的空間。  
  
##  <a name="removeall"></a>  CSimpleArray::RemoveAll  
 從陣列中移除所有項目。  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 移除目前儲存在陣列中的所有項目。  
  
##  <a name="removeat"></a>  CSimpleArray::RemoveAt  
 從陣列中移除指定的項目。  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要移除的項目所指向的索引。  
  
### <a name="return-value"></a>傳回值  
 為 true，則會傳回項目是否已移除，如果索引不正確，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 移除項目時，重新編號陣列中其餘的項目以填滿空的空間。  
  
##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex  
 陣列中設定指定的項目。  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 若要變更項目的索引。  
  
 *t*  
 要指派給指定項目的值。  
  
### <a name="return-value"></a>傳回值  
 如果，傳回 TRUE 成功，則為 FALSE 如果索引不正確。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
