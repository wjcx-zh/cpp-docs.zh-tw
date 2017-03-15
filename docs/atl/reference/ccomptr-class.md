---
title: "CComPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ae7bb5e85f23492bdbef4af86d9f68fa83c991e2
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptr-class"></a>CComPtr 類別
用來管理 COM 介面指標的智慧型指標類別。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 COM 介面，指定要儲存的指標的類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|將指標指派給成員的指標。|  
  
## <a name="remarks"></a>備註  
 使用 ATL`CComPtr`和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)管理 COM 介面指標。 兩者衍生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，並同時執行自動參考計數。  
  
 **CComPtr**和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)類別可以避免發生記憶體遺漏執行自動參考計數。  下列函式同時執行相同的邏輯作業;不過，請注意如何第二個版本可能較不容易出錯使用**CComPtr**類別︰  
  
 [!code-cpp[NVC_ATL_Utilities #&130;](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities #&131;](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 在偵錯組建中，連結程式碼追蹤的 atlsd.lib。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameccomptra--ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr  
 建構函式。  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>參數  
 `lp`  
 用來初始化介面指標。  
  
 `T`  
 COM 介面。  
  
##  <a name="a-nameoperatoreqa--ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operator =  
 指派運算子。  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至更新`CComPtr`物件  
  
### <a name="remarks"></a>備註  
 現有的物件，如果存在此作業 AddRefs 新物件和版本。  
  
## <a name="see-also"></a>另請參閱  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [類別概觀](../../atl/atl-class-overview.md)

