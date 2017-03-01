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
- ATL::CAutoVectorPtr
- ATL.CAutoVectorPtr
- ATL.CAutoVectorPtr<T>
- CAutoVectorPtr
- ATL::CAutoVectorPtr<T>
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bb4bbd110552d1e3cf604add44de7e428d2703ee
ms.lasthandoff: 02/24/2017

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
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|建構函式。|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。|  
|[CAutoVectorPtr::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|  
|[CAutoVectorPtr::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|  
|[CAutoVectorPtr::Free](#free)|呼叫此方法以刪除所指向的物件`CAutoVectorPtr`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|轉型運算子。|  
|[CAutoVectorPtr::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法來建立及管理智慧型指標，這有助於防止記憶體流失，藉由將會超出範圍時自動釋放資源。 `CAutoVectorPtr`類似於`CAutoPtr`、 唯一的差異在於，`CAutoVectorPtr`使用[向量 new []](../../standard-library/new-operators.md#operator_new_arr)和[向量 delete []](../../standard-library/new-operators.md#operator_delete_arr)地配置和釋放記憶體，而 c + + 不**新**和**刪除**運算子。 請參閱[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果集合類別的`CAutoVectorPtr`所需。  

  
 請參閱[CAutoPtr](../../atl/reference/cautoptr-class.md)使用智慧型指標類別的範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameallocatea--cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Allocate  
 呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>參數  
 `nElements`  
 陣列中的項目數。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體成功則傳回 true 配置失敗 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數現在指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="a-nameattacha--cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Attach  
 呼叫這個方法來取得現有指標的擁有權。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 `CAutoVectorPtr`物件會取得這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 當`CAutoVectorPtr`物件會取得指標的擁有權，則它會自動刪除指標和配置的資料超出範圍時。 如果[CAutoVectorPtr::Detach](#detach)是呼叫，程式設計人員再次負責釋放任何指定配置的資源。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數現在指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="a-namecautovectorptra--cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
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
 `CAutoVectorPtr`物件可以建立使用現有的指標，請在此情況下傳送指標的擁有權。  
  
##  <a name="a-namedtora--cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 解構函式。  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。 呼叫[CAutoVectorPtr::Free](#free)。  
  
##  <a name="a-namedetacha--cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach  
 呼叫此方法，以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CAutoVectorPtr::m_p](#m_p)成員變數為 NULL，並傳回指標的複本。 在呼叫**卸離**，最多來釋放任何程式設計人員配置資源的`CAutoVectorPtr`物件可能先前假設責任。  
  
##  <a name="a-namefreea--cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Free  
 呼叫此方法以刪除所指向的物件`CAutoVectorPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>備註  
 指向物件`CAutoVectorPtr`釋出，而[CAutoVectorPtr::m_p](#m_p)成員變數設為 NULL。  
  
##  <a name="a-namempa--cautovectorptrmp"></a><a name="m_p"></a>CAutoVectorPtr::m_p  
 指標的資料成員變數。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="a-nameoperatoreqa--cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operator =  
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
 指派運算子會卸離`CAutoVectorPtr`物件從目前的指標，並將新的指標，附加`p`，在其位置。  
  
##  <a name="a-nameoperatortstara--cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 轉型運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回類別樣板中定義的物件資料類型的指標。  
  
## <a name="see-also"></a>另請參閱  
 [CAutoPtr 類別](../../atl/reference/cautoptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

