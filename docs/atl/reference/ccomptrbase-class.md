---
title: "CComPtrBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 1e6bf79ce5de5d19468b3cbb230e16882483dc30
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="ccomptrbase-class"></a>CComPtrBase 類別
這個類別會提供智慧型指標類別使用以 COM 為基礎的記憶體常式的基礎。  
  
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
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|呼叫此方法以之間建立連線`CComPtrBase`的連接點與用戶端的接收器。|  
|[CComPtrBase::Attach](#attach)|呼叫此方法以取得現有的指標的擁有權。|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|呼叫這個方法來建立與指定的類別識別碼或程式識別碼。 關聯的類別的物件|  
|[CComPtrBase::CopyTo](#copyto)|呼叫此方法以複製`CComPtrBase`給另一個指標變數的指標。|  
|[CComPtrBase::Detach](#detach)|呼叫此方法以釋放指標的擁有權。|  
|[CComPtrBase::IsEqualObject](#isequalobject)|呼叫這個方法來檢查是否指定**IUnknown**指向相同的物件相關聯`CComPtrBase`物件。|  
|[CComPtrBase::QueryInterface](#queryinterface)|呼叫此方法以傳回指定介面的指標。|  
|[CComPtrBase::Release](#release)|呼叫此方法以釋放介面。|  
|[CComPtrBase::SetSite](#setsite)|呼叫此方法以設定的站台`CComPtrBase`物件**IUnknown**父物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|轉型運算子。|  
|[CComPtrBase::operator ！](#operator_not)|NOT 運算子。|  
|[CComPtrBase::operator （& s)](#operator_amp)|& 運算子。|  
|[CComPtrBase::operator *](#operator_star)|* 運算子。|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|小於-than 運算子。|  
|[CComPtrBase::operator = =](#operator_eq_eq)|等號比較運算子。|  
|[CComPtrBase::operator->](#operator_ptr)|指標至成員運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別提供的基礎使用 COM 記憶體管理常式，例如其他智慧型指標[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)。 衍生的類別加入自己的建構函式和運算子，但會根據所提供的方法`CComPtrBase`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  
  
##  <a name="advise"></a>CComPtrBase::Advise  
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
 指標，可唯一識別連線的 cookie。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 請參閱[AtlAdvise](connection-point-global-functions.md#atladvise)如需詳細資訊。  
  
##  <a name="attach"></a>CComPtrBase::Attach  
 呼叫此方法以取得現有的指標的擁有權。  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>參數  
 `p2`  
 `CComPtrBase`物件將會採取這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 **附加**呼叫[CComPtrBase::Release](#release)現有[CComPtrBase::p](#p)成員變數，然後指派`p2`至`CComPtrBase::p`。 當`CComPtrBase`物件會使用指標的擁有權，會自動呼叫`Release`這會刪除指標，任何在指標上配置資料物件上的參考計數變成 0。  
  
##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 解構函式。  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所指介面`CComPtrBase`。  
  
##  <a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
 呼叫這個方法來建立與指定的類別識別碼或程式識別碼。 關聯的類別的物件  
  
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
 ProgID，用來復原 CLSID 指標。  
  
 `pUnkOuter`  
 如果**NULL**，表示不正在物件建立為彙總的一部分。 如果非**NULL**，彙總物件的指標**IUnknown**介面 (控制**IUnknown**)。  
  
 `dwClsContext`  
 管理新建立的物件的程式碼將在其中執行的內容。  
  
 `rclsid`  
 將用來建立物件的程式碼與資料相關聯的 CLSID。  
  
### <a name="return-value"></a>傳回值  
 在成功時，或 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE 失敗會傳回 S_OK。 請參閱[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)和[CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)如需這些錯誤的描述。  
  
### <a name="remarks"></a>備註  
 如果在呼叫方法的第一個表單， [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386)用來復原的 CLSID。 然後呼叫這兩種形式[CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="copyto"></a>CComPtrBase::CopyTo  
 呼叫此方法以複製`CComPtrBase`給另一個指標變數的指標。  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>參數  
 *ppT*  
 接收變數的位址`CComPtrBase`指標。  
  
### <a name="return-value"></a>傳回值  
 成功時，E_POINTER 失敗會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 複製`CComPtrBase`指標*ppT*。 參考計數[CComPtrBase::p](#p)成員變數就會遞增。  
  
 會傳回 HRESULT，如果錯誤*ppT*等於 NULL。 在偵錯組建，判斷提示就會發生錯誤，如果*ppT*等於 NULL。  
  
##  <a name="detach"></a>CComPtrBase::Detach  
 呼叫此方法以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CComPtrBase::p](#p)資料成員變數設為 NULL，並傳回指標的複本。  
  
##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 呼叫這個方法來檢查是否指定**IUnknown**指向相同的物件相關聯`CComPtrBase`物件。  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>參數  
 `pOther`  
 **IUnknown \*** 比較。  
  
### <a name="return-value"></a>傳回值  
 如果物件是完全相同，則為 false，則傳回 true。  
  
##  <a name="operator_not"></a>CComPtrBase::operator ！  
 NOT 運算子。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 true，否則`CComHeapPtr`指標等於 NULL，則為 false 否則。  
  
##  <a name="operator_amp"></a>CComPtrBase::operator&amp;  
 & 運算子。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回所指物件的位址`CComPtrBase`物件。  
  
##  <a name="operator_star"></a>CComPtrBase::operator *  
 * 運算子。  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p); 也就是所參考的物件的指標`CComPtrBase`物件。  
  
 如果偵錯組建效能，如果會發生判斷提示錯誤[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="operator_eq_eq"></a>CComPtrBase::operator = =  
 等號比較運算子。  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 true，否則`CComPtrBase`和*pT*指向相同物件，則為 false 否則。  
  
##  <a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 成員指標運算子。  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p)資料成員變數。  
  
### <a name="remarks"></a>備註  
 使用此運算子來呼叫所指向的類別中的方法`CComPtrBase`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CComPtrBase`點為 NULL 的資料成員。  
  
##  <a name="operator_lt"></a>CComPtrBase::operator&lt;  
 小於-than 運算子。  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果由目前物件的指標，則傳回 true 小於的指標，它會進行比較。  
  
##  <a name="operator_t_star"></a>CComPtrBase::operator T *  
 轉型運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回在類別樣板中定義的物件資料類型的指標。  
  
##  <a name="p"></a>CComPtrBase::p  
 指標的資料成員變數。  
  
```
T* p;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="queryinterface"></a>CComPtrBase::QueryInterface  
 呼叫此方法以傳回指定介面的指標。  
  
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
 在成功時或 E_NOINTERFACE 失敗會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[iunknown:: Queryinterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果*pp*不等於 NULL。  
  
##  <a name="release"></a>CComPtrBase::Release  
 呼叫此方法以釋放介面。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>備註  
 已發行的介面，和[CComPtrBase::p](#p)設為 NULL。  
  
##  <a name="setsite"></a>CComPtrBase::SetSite  
 呼叫此方法以設定的站台`CComPtrBase`物件**IUnknown**父物件。  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>參數  
 `punkParent`  
 指標**IUnknown**介面的父系。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

