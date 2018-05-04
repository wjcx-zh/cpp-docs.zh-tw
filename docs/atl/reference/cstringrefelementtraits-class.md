---
title: CStringRefElementTraits 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8746bf216be417fb569aae58421b272c983914b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 類別
這個類別提供靜態函式與儲存在集合類別物件的字串。 字串物件做為參考人選。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|呼叫此靜態函式來比較兩個字串元素相等。|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|呼叫此靜態函式來比較兩個字串元素。|  
|[CStringRefElementTraits::Hash](#hash)|呼叫此靜態函式來計算雜湊值的指定的字串的項目。|  
  
## <a name="remarks"></a>備註  
 這個類別提供靜態函式來比較字串，以及如何建立雜湊值。 當使用來儲存字串為基礎之資料的集合類別，這些函式會很有用。 不同於[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits`導致`CString`做為傳遞的引數**const CString &** 參考。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 呼叫此靜態函式來比較兩個字串元素相等。  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>參數  
 `element1`  
 第一個字串項目。  
  
 `element2`  
 第二個字串項目。  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 呼叫此靜態函式來比較兩個字串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 第一個字串項目。  
  
 `str2`  
 第二個字串項目。  
  
### <a name="return-value"></a>傳回值  
 如果是相同的字串則為零，< 0 如果`str1`是小於`str2`，或 > 0 如果`str1`大於`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用來執行比較。  
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 呼叫此靜態函式來計算雜湊值的指定的字串的項目。  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>參數  
 `str`  
 字串項目。  
  
### <a name="return-value"></a>傳回值  
 傳回使用字串的內容來計算雜湊值。  
  
## <a name="see-also"></a>另請參閱  
 [CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
