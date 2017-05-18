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
ms.openlocfilehash: f46ff072bcd0f772dac1bba52b114d82ee433112
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 類別
這個類別會提供使用的儲存的集合類別的靜態函式`CString`物件。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|若要使用項目加入集合類別物件的資料型別。|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|要用來擷取項目從集合類別物件的資料類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|（靜態）呼叫此函式來比較兩個字串項目相等。|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式來比較兩個字串的項目。|  
|[CStringElementTraits::CopyElements](#copyelements)|（靜態）呼叫此函式來複製`CString`集合類別物件中儲存項目。|  
|[CStringElementTraits::Hash](#hash)|（靜態）呼叫此函式來計算雜湊值的指定的字串的項目。|  
|[CStringElementTraits::RelocateElements](#relocateelements)|（靜態）呼叫此函式來重新放置`CString`集合類別物件中儲存項目。|  
  
## <a name="remarks"></a>備註  
 這個類別提供靜態函式來複製、 移動和比較字串，以及建立雜湊值。 使用集合類別來儲存字串為基礎的資料時，這些函式是很有用。 使用[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)需要區分大小寫比較時。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)來做為參考進行處理時字串物件。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** cstringt.h  
  
##  <a name="compareelements"></a>CStringElementTraits::CompareElements  
 呼叫此靜態函式來比較兩個字串項目相等。  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 第一個字串項目。  
  
 `str2`  
 第二個字串的項目。  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
##  <a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered  
 呼叫此靜態函式來比較兩個字串的項目。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 第一個字串項目。  
  
 `str2`  
 第二個字串的項目。  
  
### <a name="return-value"></a>傳回值  
 如果字串完全相同，零< 0="" if="">`str1`是小於`str2`，或 > 0 如果`str1`大於`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用來執行比較。  

  
##  <a name="copyelements"></a>CStringElementTraits::CopyElements  
 呼叫此靜態函式來複製`CString`集合類別物件中儲存項目。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>參數  
 `pDest`  
 接收複製的資料的第一個元素的指標。  
  
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
 傳回使用字串的內容計算的雜湊值。  
  
##  <a name="inargtype"></a>CStringElementTraits::INARGTYPE  
 若要使用項目加入集合類別物件的資料型別。  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraits::OUTARGTYPE  
 要用來擷取項目從集合類別物件的資料類型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CStringElementTraits::RelocateElements  
 呼叫此靜態函式來重新放置`CString`集合類別物件中儲存項目。  
  
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
 若要重新配置的第一個元素的指標。  
  
 `nElements`  
 重新定位項目數目。  
  
### <a name="remarks"></a>備註  
 靜態函式呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大部分的資料類型。 如果要移動的物件包含它們自己的成員的指標，此靜態函式必須覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI 類別](../../atl/reference/cstringelementtraitsi-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

