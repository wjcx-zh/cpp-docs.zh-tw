---
title: "CComSafeArrayBound 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs: C++
helpviewer_keywords: CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4de823b4cdb2d7926b2a9d640b2e8f7352e389fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 類別
這個類別是包裝函式[SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d)結構。  
  
## <a name="syntax"></a>語法  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|建構函式。|  
|[GetCount](#getcount)|呼叫此方法以傳回的項目數。|  
|[GetLowerBound](#getlowerbound)|呼叫此方法以傳回下限。|  
|[GetUpperBound](#getupperbound)|呼叫此方法以傳回上限。|  
|[SetCount](#setcount)|呼叫此方法以設定項目數目。|  
|[SetLowerBound](#setlowerbound)|呼叫此方法以設定下限。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|設定`CComSafeArrayBound`為新值。|  
  
## <a name="remarks"></a>備註  
 這個類別是包裝函式**SAFEARRAYBOUND**所使用的結構[CComSafeArray](../../atl/reference/ccomsafearray-class.md)。 它提供方法的查詢及設定的單一維度的上限和下限範圍`CComSafeArray`物件和它所包含的元素數目。 多維度`CComSafeArray`物件使用的陣列`CComSafeArrayBound`物件、 一個用於每個維度。 因此，當您使用下列方法[GetCount](#getcount)，注意此方法將多維陣列中傳回項目總數。  
  
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
 如果陣列是從 Visual c + + 程式存取，建議下限定義為 0。 您可能偏好使用不同的下限值，如果陣列是以用於 Visual Basic 等其他語言的。  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 呼叫此方法以傳回的項目數。  
  
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
 上限取決於項目和下限值的數量。 例如，如果下限為 0，而項目數目為 10，上限將自動設 9。  
  
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
 將指標傳回至`CComSafeArrayBound`物件。  
  
### <a name="remarks"></a>備註  
 `CComSafeArrayBound`物件可以使用現有指派`CComSafeArrayBound`，或提供的項目數，所在案例下限預設設定為 0。  
  
##  <a name="setcount"></a>CComSafeArrayBound::SetCount  
 呼叫此方法以設定項目數目。  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `ulCount`  
 元素數。  
  
### <a name="return-value"></a>傳回值  
 傳回數字中的項目`CComSafeArrayBound`物件。  
  
##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound  
 呼叫此方法以設定下限。  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>參數  
 `lLowerBound`  
 下限。  
  
### <a name="return-value"></a>傳回值  
 傳回新的下限的`CComSafeArrayBound`物件。  
  
### <a name="remarks"></a>備註  
 如果陣列是從 Visual c + + 程式存取，建議下限定義為 0。 您可能偏好使用不同的下限值，如果陣列是以用於 Visual Basic 等其他語言的。  
  
 上限取決於項目和下限值的數量。 例如，如果下限為 0，而項目數目為 10，上限將自動設 9。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
