---
title: "CComPtrBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComPtrBase
- ATL::CComPtrBase<T>
- ATL.CComPtrBase<T>
- ATL::CComPtrBase
- CComPtrBase
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 28207e483b0bf56b9e3e98f487d174b8ae47e9e7
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptrbase-class"></a>CComPtrBase 類別
這個類別會提供使用以 COM 為基礎的記憶體常式的智慧型指標類別的基礎。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 智慧型指標所參考的物件類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|呼叫此方法以之間建立連線`CComPtrBase`的連接點與用戶端的接收器。|  
|[CComPtrBase::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|呼叫這個方法來建立與指定的類別識別碼或程式識別碼關聯之類別的物件|  
|[CComPtrBase::CopyTo](#copyto)|呼叫這個方法來複製`CComPtrBase`給另一個指標變數的指標。|  
|[CComPtrBase::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|  
|[CComPtrBase::IsEqualObject](#isequalobject)|呼叫這個方法來檢查是否已指定**IUnknown**指向相同的物件相關聯`CComPtrBase`物件。|  
|[CComPtrBase::QueryInterface](#queryinterface)|呼叫這個方法來傳回指定介面的指標。|  
|[CComPtrBase::Release](#release)|呼叫此方法，以釋放介面。|  
|[CComPtrBase::SetSite](#setsite)|呼叫這個方法來設定的站台`CComPtrBase`物件傳遞給**IUnknown**父物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|轉型運算子。|  
|[CComPtrBase::operator ！](#operator_not)|NOT 運算子。|  
|[CComPtrBase::operator i](#operator_amp)|I 運算子。|  
|[CComPtrBase::operator *](#operator_star)|* 運算子。|  
|[CComPtrBase::operator](#ccomptrbase__operator lt)|小於-運算子。|  
|[CComPtrBase::operator = =](#operator_eq_eq)|等號比較運算子。|  
|[-> CComPtrBase::operator](#operator_ptr)|指標至成員運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別提供的基礎使用 COM 記憶體管理常式，如下所示的其他智慧型指標[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)。 衍生的類別加入自己的建構函式和運算子，但會根據所提供的方法`CComPtrBase`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcomcli.h  
  
##  <a name="a-nameadvisea--ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Advise  
 呼叫此方法以之間建立連線`CComPtrBase`的連接點與用戶端的接收器。  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 用戶端的指標**IUnknown**。  
  
 `iid`  
 連接點的 GUID。 一般而言，這是輸出連接點所管理的介面相同。  
  
 `pdw`  
 指標，可唯一識別連接 cookie。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 請參閱[AtlAdvise](http://msdn.microsoft.com/library/625a2f03-6b7f-4761-be5d-d2871d1d3254)如需詳細資訊。  
  
##  <a name="a-nameattacha--ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Attach  
 呼叫這個方法來取得現有指標的擁有權。  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>參數  
 `p2`  
 `CComPtrBase`物件會取得這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 **附加**呼叫[CComPtrBase::Release](#release)現有[CComPtrBase::p](#p)成員變數，然後指派`p2`到`CComPtrBase::p`。 當`CComPtrBase`物件指標的擁有權，它會自動呼叫`Release`這會刪除指標，任何在指標上配置資料物件上的參考計數變成 0。  
  
##  <a name="a-namedtora--ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 解構函式。  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放介面所指`CComPtrBase`。  
  
##  <a name="a-namecocreateinstancea--ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
 呼叫這個方法來建立與指定的類別識別碼或程式識別碼關聯之類別的物件  
  
```
HRESULT CoCreateInstance(  
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(  
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```  
  
### <a name="parameters"></a>參數  
 `szProgID`  
 ProgID，用來復原的 CLSID 指標。  
  
 `pUnkOuter`  
 如果**NULL**，表示該物件尚未建立彙總的一部分。 如果非**NULL**、 為彙總物件的指標**IUnknown**介面 (用於控制**IUnknown**)。  
  
 `dwClsContext`  
 管理新建立的物件的程式碼會在其中執行的內容。  
  
 `rclsid`  
 將用來建立物件的程式碼與資料相關聯的 CLSID。  
  
### <a name="return-value"></a>傳回值  
 在成功時，或因為 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE 會傳回 S_OK 失敗。 請參閱[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)和[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)如需這些錯誤的說明。  
  
### <a name="remarks"></a>備註  
 如果呼叫方法的第一個表單， [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)用來復原的 CLSID。 然後呼叫這兩種形式[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="a-namecopytoa--ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo  
 呼叫這個方法來複製`CComPtrBase`給另一個指標變數的指標。  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>參數  
 *ppT*  
 變數會接收位址`CComPtrBase`指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功，E_POINTER 失敗，會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 複製`CComPtrBase`指標*ppT*。 上的參考次數[CComPtrBase::p](#p)成員變數就會遞增。  
  
 錯誤將傳回 HRESULT，如果*ppT*等於 NULL。 在偵錯組建，判斷提示就會發生錯誤，如果*ppT*等於 NULL。  
  
##  <a name="a-namedetacha--ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach  
 呼叫此方法，以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CComPtrBase::p](#p)資料成員變數為 NULL，並傳回指標的複本。  
  
##  <a name="a-nameisequalobjecta--ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 呼叫這個方法來檢查是否已指定**IUnknown**指向相同的物件相關聯`CComPtrBase`物件。  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>參數  
 `pOther`  
 **IUnknown \* **比較。  
  
### <a name="return-value"></a>傳回值  
 如果物件是完全相同，則為 false，則傳回 true。  
  
##  <a name="a-nameoperatornota--ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::operator ！  
 NOT 運算子。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 true 如果`CComHeapPtr`指標為 NULL 時，等於 false 否則。  
  
##  <a name="a-nameoperatorampa--ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::operator&amp;  
 I 運算子。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回所指物件的位址`CComPtrBase`物件。  
  
##  <a name="a-nameoperatorstara--ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::operator *  
 * 運算子。  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p); 也就是所參考之物件的指標`CComPtrBase`物件。  
  
 若偵錯組建，判斷錯誤便會發生[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="a-nameoperatoreqeqa--ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operator = =  
 等號比較運算子。  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 true 如果`CComPtrBase`和*pT*指向相同的物件，則為 false 否則。  
  
##  <a name="a-nameoperatorptra--ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 成員指標運算子。  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p)資料成員變數。  
  
### <a name="remarks"></a>備註  
 使用這個運算子所指的類別中呼叫的方法`CComPtrBase`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CComPtrBase`點為 NULL 的資料成員。  
  
##  <a name="a-nameoperatorlta--ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::operator&lt;  
 小於-運算子。  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果由目前物件的指標，則傳回 true 小於的指標，它會進行比較。  
  
##  <a name="a-nameoperatortstara--ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operator T *  
 轉型運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回類別樣板中定義的物件資料類型的指標。  
  
##  <a name="a-namepa--ccomptrbasep"></a><a name="p"></a>CComPtrBase::p  
 指標的資料成員變數。  
  
```
T* p;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="a-namequeryinterfacea--ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface  
 呼叫這個方法來傳回指定介面的指標。  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>參數  
 `Q`  
 物件類型的介面指標是必要。  
  
 `pp`  
 接收要求的介面指標的輸出變數的位址。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK 成功 」 或 「 E_NOINTERFACE 上失敗。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[Iid](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果*pp*不等於 NULL。  
  
##  <a name="a-namereleasea--ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Release  
 呼叫此方法，以釋放介面。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>備註  
 已發行的介面，和[CComPtrBase::p](#p)設為 NULL。  
  
##  <a name="a-namesetsitea--ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite  
 呼叫這個方法來設定的站台`CComPtrBase`物件傳遞給**IUnknown**父物件。  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>參數  
 `punkParent`  
 指標**IUnknown**介面的父系。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[AtlSetChildSite](http://msdn.microsoft.com/library/2a8ece19-6bfd-4e89-9d1d-e5a78f95e2df)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

