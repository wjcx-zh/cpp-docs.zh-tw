---
title: "CAutoVectorPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 8234018b2f6faf8585186491413ecbd688a3b32f
ms.lasthandoff: 04/29/2017

---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 類別
這個類別表示智慧型指標物件使用向量 new 和 delete 運算子。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 指標類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|建構函式。|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。|  
|[CAutoVectorPtr::Attach](#attach)|呼叫此方法以取得現有的指標的擁有權。|  
|[CAutoVectorPtr::Detach](#detach)|呼叫此方法以釋放指標的擁有權。|  
|[CAutoVectorPtr::Free](#free)|呼叫此方法以刪除所指向的物件`CAutoVectorPtr`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|轉型運算子。|  
|[CAutoVectorPtr::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供建立和管理智慧型指標，可協助您藉由自動釋放資源，將會超出範圍時防止記憶體流失的方法。 `CAutoVectorPtr`類似於`CAutoPtr`、 唯一的差異在於，`CAutoVectorPtr`使用[向量新 &#91; &#93;](../../standard-library/new-operators.md#op_new_arr)和[向量 delete &#91; &#93;](../../standard-library/new-operators.md#op_delete_arr)地配置和釋放記憶體，而不使用 c + +**新**和**刪除**運算子。 請參閱[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果的集合類別`CAutoVectorPtr`所需。  

  
 請參閱[CAutoPtr](../../atl/reference/cautoptr-class.md)使用智慧型指標類別的範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="allocate"></a>CAutoVectorPtr::Allocate  
 呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>參數  
 `nElements`  
 陣列中的項目數。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體已成功則傳回 true 配置失敗，false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數目前會指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="attach"></a>CAutoVectorPtr::Attach  
 呼叫此方法以取得現有的指標的擁有權。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 `CAutoVectorPtr`物件需要 this 指標的擁有權。  
  
### <a name="remarks"></a>備註  
 當`CAutoVectorPtr`物件會使用指標的擁有權，則它會自動刪除的指標與任何已配置的資料離開範圍時。 如果[CAutoVectorPtr::Detach](#detach)是呼叫，程式設計人員一次的釋放任何責任，指定配置的資源。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數目前會指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 建構函式。  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 現有的指標。  
  
### <a name="remarks"></a>備註  
 `CAutoVectorPtr`物件可以建立使用現有的指標，請在此情況下它會傳送指標的擁有權。  
  
##  <a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 解構函式。  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。 呼叫[CAutoVectorPtr::Free](#free)。  
  
##  <a name="detach"></a>CAutoVectorPtr::Detach  
 呼叫此方法以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CAutoVectorPtr::m_p](#m_p)成員變數設為 NULL，並傳回指標的複本。 在呼叫**卸離**，它最多來釋放任何程式設計人員已配置的資源的`CAutoVectorPtr`物件可能先前假設責任。  
  
##  <a name="free"></a>CAutoVectorPtr::Free  
 呼叫此方法以刪除所指向的物件`CAutoVectorPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>備註  
 指向的物件`CAutoVectorPtr`釋出，而[CAutoVectorPtr::m_p](#m_p)成員變數設為 NULL。  
  
##  <a name="m_p"></a>CAutoVectorPtr::m_p  
 指標的資料成員變數。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="operator_eq"></a>CAutoVectorPtr::operator =  
 指派運算子。  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 變數的指標。  
  
### <a name="return-value"></a>傳回值  
 將參考傳回給**CAutoVectorPtr\< T >**。  
  
### <a name="remarks"></a>備註  
 指派運算子會卸離`CAutoVectorPtr`物件從目前的指標，並將新的指標，附加`p`，其所在位置。  
  
##  <a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 轉型運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回在類別樣板中定義的物件資料類型的指標。  
  
## <a name="see-also"></a>另請參閱  
 [CAutoPtr 類別](../../atl/reference/cautoptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

