---
title: "CAutoPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
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
ms.openlocfilehash: 309a3d0ddceab2995c85e156c7db09ddd7edfa86
ms.lasthandoff: 02/24/2017

---
# <a name="cautoptr-class"></a>CAutoPtr 類別
此類別代表智慧型指標物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 指標類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|建構函式。|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|  
|[CAutoPtr::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|  
|[CAutoPtr::Free](#free)|呼叫此方法以刪除所指向的物件`CAutoPtr`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|轉型運算子。|  
|[CAutoPtr::operator =](#operator_eq)|指派運算子。|  
|[-> CAutoPtr::operator](#operator_ptr)|成員指標運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法來建立及管理智慧型指標，這有助於防止記憶體流失，藉由將會超出範圍時自動釋放資源。  
  
 此外，`CAutoPtr`的複製建構函式和指派運算子轉送擁有權的指標，將來源指標複製到目的地的指標和設定來源指標為 NULL。 因此是不可能有兩個`CAutoPtr`物件每儲存相同的指標，因此降低了兩次刪除相同的指標的可能性。  
  
 `CAutoPtr`也可以簡化建立集合的指標。 衍生的集合類別，然後覆寫解構函式，而是比較容易進行一系列`CAutoPtr`物件。 刪除集合時，`CAutoPtr`物件會超出範圍而自動刪除其本身。  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)變異運作方式與`CAutoPtr`，只不過它們配置和釋放記憶體，而不 c + + 中使用不同的堆積函式**新**和**刪除**運算子。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)類似`CAutoPtr`、 唯一的差異在於，它會使用**向量 new []**和**向量 delete []**地配置和釋放記憶體。  
  
 另請參閱[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)陣列或智慧型指標的清單時所需。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&74;](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 呼叫這個方法來取得現有指標的擁有權。  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 `CAutoPtr`物件會取得這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 當`CAutoPtr`物件會取得指標的擁有權，則它會自動刪除指標和配置的資料超出範圍時。 如果[CAutoPtr::Detach](#detach)是呼叫，程式設計人員再次負責釋放任何指定配置的資源。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗[CAutoPtr::m_p](#m_p)資料成員現在會指向現有的值; 也就是說，不等於 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="cautoptr"></a>CAutoPtr::CAutoPtr  
 建構函式。  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 現有的指標。  
  
 `TSrc`  
 受管理的另一個型別`CAutoPtr`，用來初始化目前的物件。  
  
### <a name="remarks"></a>備註  
 `CAutoPtr`物件可以建立使用現有的指標，請在此情況下傳送指標的擁有權。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="dtor"></a>CAutoPtr:: ~ CAutoPtr  
 解構函式。  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。 呼叫[CAutoPtr::Free](#free)。  
  
##  <a name="detach"></a>CAutoPtr::Detach  
 呼叫此方法，以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CAutoPtr::m_p](#m_p)資料成員變數為 NULL，並傳回指標的複本。 在呼叫**卸離**，最多來釋放任何程式設計人員配置資源的`CAutoPtr`物件可能先前假設 reponsibility。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="free"></a>CAutoPtr::Free  
 呼叫此方法以刪除所指向的物件`CAutoPtr`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>備註  
 指向物件`CAutoPtr`釋出，而[CAutoPtr::m_p](#m_p)資料成員變數設為 NULL。  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 指標的資料成員變數。  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="operator_eq"></a>CAutoPtr::operator =  
 指派運算子。  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>參數  
 `p`  
 變數的指標。  
  
 `TSrc`  
 類別型別。  
  
### <a name="return-value"></a>傳回值  
 將參考傳回給**CAutoPtr\< T >**。  
  
### <a name="remarks"></a>備註  
 指派運算子會卸離`CAutoPtr`物件從目前的指標，並將新的指標，附加`p`，在其位置。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="operator_ptr"></a>CAutoPtr::operator-&gt;  
 成員指標運算子。  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CAutoPtr::m_p](#m_p)資料成員變數。  
  
### <a name="remarks"></a>備註  
 使用這個運算子所指的類別中呼叫的方法`CAutoPtr`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CAutoPtr`點為 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
##  <a name="operator_t_star"></a>CAutoPtr::operator T *  
 轉型運算子。  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回類別樣板中定義的物件資料類型的指標。  
  
### <a name="example"></a>範例  
 請參閱範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

