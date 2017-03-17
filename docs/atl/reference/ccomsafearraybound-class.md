---
title: "CComSafeArrayBound 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
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
ms.openlocfilehash: 1cc2adef85c902b7ad12b152b35a7ef68e6abacb
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 類別
這個類別是包裝函式[SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d)結構。  
  
## <a name="syntax"></a>語法  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|建構函式。|  
|[GetCount](#getcount)|呼叫這個方法傳回的項目數。|  
|[GetLowerBound](#getlowerbound)|呼叫此方法以傳回下限。|  
|[GetUpperBound](#getupperbound)|呼叫此方法以傳回上限。|  
|[SetCount](#setcount)|呼叫這個方法來設定項目數目。|  
|[SetLowerBound](#setlowerbound)|呼叫這個方法來設定下限。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|設定`CComSafeArrayBound`為新值。|  
  
## <a name="remarks"></a>備註  
 這個類別是包裝函式**SAFEARRAYBOUND**所用結構[ccomsafearray 的 Safearray](../../atl/reference/ccomsafearray-class.md)。 它提供方法來查詢及設定的上限和下限之間的單一維度的`CComSafeArray`物件和它所包含的元素數目。 多維度`CComSafeArray`物件會使用陣列`CComSafeArrayBound`物件、 一個用於每個維度。 因此，當您使用下列方法[GetCount](#getcount)，請注意，這個方法不會傳回項目總數多維陣列中。  
  
 **標頭︰** atlsafe.h  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsafe.h  
  
##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound  
 建構函式。  
  
```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `ulCount`  
 陣列中的項目數。  
  
 `lLowerBound`  
 從已編號的陣列的下限。  
  
### <a name="remarks"></a>備註  
 如果陣列是從 Visual c + + 程式存取，建議的最小值定義為 0。 您可能偏好使用不同的下限值，如果陣列是以用於其他語言，例如 Visual Basic 的。  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 呼叫這個方法傳回的項目數。  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的項目數。  
  
### <a name="remarks"></a>備註  
 如果相關聯`CComSafeArray`物件代表多維陣列，這個方法只會傳回最右邊的維度中的項目總數。 使用[CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount)取得項目總數。  
  
##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound  
 呼叫此方法以傳回下限。  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回下限為`CComSafeArrayBound`物件。  
  
##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound  
 呼叫此方法以傳回上限。  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回上限`CComSafeArrayBound`物件。  
  
### <a name="remarks"></a>備註  
 上限取決於項目和下限值的數目。 例如，如果下限為 0，而項目數目為 10，上限將自動設為 9。  
  
##  <a name="operator_eq"></a>CComSafeArrayBound::operator =  
 設定`CComSafeArrayBound`為新值。  
  
```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `bound`  
 `CComSafeArrayBound` 物件。  
  
 `ulCount`  
 元素數。  
  
### <a name="return-value"></a>傳回值  
 若要將指標傳回`CComSafeArrayBound`物件。  
  
### <a name="remarks"></a>備註  
 `CComSafeArrayBound`物件可以使用現有指派`CComSafeArrayBound`，或提供項目，以案例下限設定為 0 預設數目。  
  
##  <a name="setcount"></a>CComSafeArrayBound::SetCount  
 呼叫這個方法來設定項目數目。  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `ulCount`  
 元素數。  
  
### <a name="return-value"></a>傳回值  
 傳回數字中的項目`CComSafeArrayBound`物件。  
  
##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound  
 呼叫這個方法來設定下限。  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>參數  
 `lLowerBound`  
 下限。  
  
### <a name="return-value"></a>傳回值  
 傳回新的下限的`CComSafeArrayBound`物件。  
  
### <a name="remarks"></a>備註  
 如果陣列是從 Visual c + + 程式存取，建議的最小值定義為 0。 您可能偏好使用不同的下限值，如果陣列是以用於其他語言，例如 Visual Basic 的。  
  
 上限取決於項目和下限值的數目。 例如，如果下限為 0，而項目數目為 10，上限將自動設為 9。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

