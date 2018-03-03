---
title: "CStringElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 025c9aa66a8647fd5d8ca9803aedb50b27ed3be1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 類別
這個類別會提供所儲存的集合類別使用的靜態函式`CString`物件。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|要用來將項目加入至集合的類別物件的資料類型。|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|（靜態）呼叫此函式來比較兩個字串元素相等。|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式來比較兩個字串元素。|  
|[CStringElementTraits::CopyElements](#copyelements)|（靜態）呼叫此函式來複製`CString`集合類別物件中儲存的項目。|  
|[CStringElementTraits::Hash](#hash)|（靜態）呼叫此函式來計算雜湊值的指定的字串的項目。|  
|[CStringElementTraits::RelocateElements](#relocateelements)|（靜態）呼叫此函式來重新放置`CString`集合類別物件中儲存的項目。|  
  
## <a name="remarks"></a>備註  
 這個類別提供靜態函式來複製、 移動和比較字串以及建立雜湊值。 當使用來儲存字串為基礎之資料的集合類別，這些函式會很有用。 使用[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)需要不區分大小寫的比較時。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)字串物件要處理做為參考。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** cstringt.h  
  
##  <a name="compareelements"></a>CStringElementTraits::CompareElements  
 呼叫此靜態函式來比較兩個字串元素相等。  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 第一個字串項目。  
  
 `str2`  
 第二個字串項目。  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
##  <a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered  
 呼叫此靜態函式來比較兩個字串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 第一個字串項目。  
  
 `str2`  
 第二個字串項目。  
  
### <a name="return-value"></a>傳回值  
 如果是相同的字串則為零，< 0 如果`str1`是小於`str2`，或 > 0 如果`str1`大於`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用來執行比較。  

  
##  <a name="copyelements"></a>CStringElementTraits::CopyElements  
 呼叫此靜態函式來複製`CString`集合類別物件中儲存的項目。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 將接收複製的資料的第一個元素的指標。  
  
 `pSrc`  
 若要複製的第一個元素的指標。  
  
 `nElements`  
 要複製的項目數目。  
  
### <a name="remarks"></a>備註  
 來源和目的地的項目不應該重疊。  
  
##  <a name="hash"></a>CStringElementTraits::Hash  
 呼叫此靜態函式來計算雜湊值的指定的字串的項目。  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 字串項目。  
  
### <a name="return-value"></a>傳回值  
 傳回使用字串的內容來計算雜湊值。  
  
##  <a name="inargtype"></a>CStringElementTraits::INARGTYPE  
 要用來將項目加入至集合的類別物件的資料類型。  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraits::OUTARGTYPE  
 要用來擷取元素的集合類別物件的資料類型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CStringElementTraits::RelocateElements  
 呼叫此靜態函式來重新放置`CString`集合類別物件中儲存的項目。  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 將會收到重新配置的資料的第一個元素的指標。  
  
 `pSrc`  
 第一個項目，即可重新定位指標。  
  
 `nElements`  
 重新定位的項目數目。  
  
### <a name="remarks"></a>備註  
 此靜態函式呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大多數的資料類型。 如果要移動的物件包含它們自己的成員的指標，此靜態函式必須覆寫。  
  
## <a name="see-also"></a>請參閱  
 [CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI 類別](../../atl/reference/cstringelementtraitsi-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
