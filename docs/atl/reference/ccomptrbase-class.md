---
title: CComPtrBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae23f641becea5a7bdb47eefbdee59e18c2f27a4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205591"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 類別
這個類別會使用以 COM 為基礎的記憶體常式的智慧型指標類別提供基礎。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 智慧型指標所要參考的物件型別。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|呼叫這個方法來建立之間的連線`CComPtrBase`的連接點和用戶端接收器。|  
|[CComPtrBase::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|呼叫這個方法來建立指定類別識別碼或計劃識別碼相關聯類別的物件|  
|[CComPtrBase::CopyTo](#copyto)|呼叫這個方法來複製`CComPtrBase`給另一個指標變數的指標。|  
|[CComPtrBase::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|  
|[CComPtrBase::IsEqualObject](#isequalobject)|呼叫這個方法來檢查是否指定`IUnknown`指向相同的物件相關聯`CComPtrBase`物件。|  
|[CComPtrBase::QueryInterface](#queryinterface)|呼叫這個方法來傳回指定的介面的指標。|  
|[CComPtrBase::Release](#release)|呼叫此方法，以釋放介面。|  
|[CComPtrBase::SetSite](#setsite)|呼叫此方法以設定的站台`CComPtrBase`物件至`IUnknown`父物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|轉換運算子。|  
|[CComPtrBase::operator ！](#operator_not)|NOT 運算子。|  
|[CComPtrBase::operator （& s)](#operator_amp)|& 運算子。|  
|[CComPtrBase::operator *](#operator_star)|\* 運算子。|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|小於-than 運算子。|  
|[CComPtrBase::operator = =](#operator_eq_eq)|等號比較運算子。|  
|[CComPtrBase::operator->](#operator_ptr)|指標至成員運算子中。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|指標的資料成員變數中。|  
  
## <a name="remarks"></a>備註  
 這個類別提供的基礎使用 COM 記憶體管理常式，例如其他智慧型指標[CComQIPtr](../../atl/reference/ccomqiptr-class.md)並[CComPtr](../../atl/reference/ccomptr-class.md)。 衍生的類別加入自己的建構函式和運算子，但所提供的方法會依賴`CComPtrBase`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  
  
##  <a name="advise"></a>  CComPtrBase::Advise  
 呼叫這個方法來建立之間的連線`CComPtrBase`的連接點和用戶端接收器。  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 指標，用戶端的`IUnknown`。  
  
 *iid*  
 連接點的 GUID。 一般而言，這是連接點所管理之輸出介面相同。  
  
 *pdw*  
 指標，可唯一識別連接 cookie。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 請參閱[AtlAdvise](connection-point-global-functions.md#atladvise)如需詳細資訊。  
  
##  <a name="attach"></a>  CComPtrBase::Attach  
 呼叫這個方法來取得現有指標的擁有權。  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>參數  
 *p2*  
 `CComPtrBase`物件會取得這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 `Attach` 呼叫[CComPtrBase::Release](#release)現有[CComPtrBase::p](#p)成員變數，然後指派*p2*至`CComPtrBase::p`。 當`CComPtrBase`物件會採用指標的擁有權，它會自動呼叫`Release`這會刪除指標和任何指標上配置如果物件上的參考計數變成 0 的資料。  
  
##  <a name="dtor"></a>  CComPtrBase:: ~ CComPtrBase  
 解構函式。  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所指向的介面`CComPtrBase`。  
  
##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance  
 呼叫這個方法來建立指定類別識別碼或計劃識別碼相關聯類別的物件  
  
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
 *szProgID*  
 ProgID，用來復原的 CLSID 指標。  
  
 *pUnkOuter*  
 如果是 NULL，表示，該物件尚未建立為彙總的一部分。 不是 NULL，如果是彙總物件的指標`IUnknown`介面 (控制`IUnknown`)。  
  
 *dwClsContext*  
 管理新建立的物件的程式碼將在其中執行的內容。  
  
 *rclsid*  
 相關聯的資料和程式碼是用來建立物件的 CLSID。  
  
### <a name="return-value"></a>傳回值  
 在成功時，或因為 REGDB_E_CLASSNOTREG、 CLASS_E_NOAGGREGATION、 CO_E_CLASSSTRING 或 E_NOINTERFACE 會傳回 S_OK，失敗。 請參閱[CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)並[CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid)如需這些錯誤的描述。  
  
### <a name="remarks"></a>備註  
 如果呼叫方法的第一個表單，則[CLSIDFromProgID](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromprogid)用來復原的 CLSID。 然後呼叫這兩種形式[CoCreateClassInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。  
  
 在偵錯組建中，判斷提示就會發生錯誤，如果[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="copyto"></a>  CComPtrBase::CopyTo  
 呼叫這個方法來複製`CComPtrBase`給另一個指標變數的指標。  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>參數  
 *ppT*  
 變數會接收位址`CComPtrBase`指標。  
  
### <a name="return-value"></a>傳回值  
 成功時，E_POINTER 失敗，會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 複本`CComPtrBase`指標*ppT*。 參考計數[CComPtrBase::p](#p)成員變數會遞增。  
  
 如果，則會傳回 HRESULT 錯誤*ppT*等於 NULL。 在偵錯組建中，判斷提示就會發生錯誤，如果*ppT*等於 NULL。  
  
##  <a name="detach"></a>  CComPtrBase::Detach  
 呼叫此方法，以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CComPtrBase::p](#p)資料成員變數為 NULL，並傳回指標的複本。  
  
##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject  
 呼叫這個方法來檢查是否指定`IUnknown`指向相同的物件相關聯`CComPtrBase`物件。  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>參數  
 *其他*  
 要比較的 `IUnknown *`。  
  
### <a name="return-value"></a>傳回值  
 如果物件為相同，否則為 false，則傳回 true。  
  
##  <a name="operator_not"></a>  CComPtrBase::operator ！  
 NOT 運算子。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回則為 true`CComHeapPtr`指標等於 NULL，則為 false 否則。  
  
##  <a name="operator_amp"></a>  CComPtrBase::operator &amp;  
 & 運算子。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回所指物件的位址`CComPtrBase`物件。  
  
##  <a name="operator_star"></a>  CComPtrBase::operator \*  
 \* 運算子。  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p); 也就是所參考的物件指標`CComPtrBase`物件。  
  
 如果偵錯組建，會發生判斷提示錯誤，如果[CComPtrBase::p](#p)不等於 NULL。  
  
##  <a name="operator_eq_eq"></a>  CComPtrBase::operator = =  
 等號比較運算子。  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *太平洋時間*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回則為 true`CComPtrBase`並*pT*指向相同的物件，則為 false 否則。  
  
##  <a name="operator_ptr"></a>  CComPtrBase::operator-&gt;  

 成員指標運算子中。  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CComPtrBase::p](#p)資料成員變數。  
  
### <a name="remarks"></a>備註  
 使用這個運算子所指的類別中呼叫方法`CComPtrBase`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CComPtrBase`資料成員指向 NULL。  
  
##  <a name="operator_lt"></a>  CComPtrBase::operator &lt;  
 小於-than 運算子。  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>參數  
 *太平洋時間*  
 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果由目前物件的指標，則傳回 true 小於要它所比較的指標。  
  
##  <a name="operator_t_star"></a>  CComPtrBase::operator T\*  
 轉換運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回類別範本中定義的物件資料類型的指標。  
  
##  <a name="p"></a>  CComPtrBase::p  
 指標的資料成員變數中。  
  
```
T* p;
```  
  
### <a name="remarks"></a>備註  
 此成員變數會保留指標資訊。  
  
##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface  
 呼叫這個方法來傳回指定的介面的指標。  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>參數  
 *Q*  
 介面指標是必要的物件型別。  
  
 *前置處理*  
 接收要求的介面指標的輸出變數位址。  
  
### <a name="return-value"></a>傳回值  
 在成功時或 E_NOINTERFACE 會傳回 S_OK，失敗。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[iunknown:: Queryinterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))。  
  
 在偵錯組建中，判斷提示就會發生錯誤，如果*pp*不等於 NULL。  
  
##  <a name="release"></a>  CComPtrBase::Release  
 呼叫此方法，以釋放介面。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>備註  
 已發行的介面，並[CComPtrBase::p](#p)設為 NULL。  
  
##  <a name="setsite"></a>  CComPtrBase::SetSite  
 呼叫此方法以設定的站台`CComPtrBase`物件至`IUnknown`父物件。  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>參數  
 *punkParent*  
 指標`IUnknown`之父代的介面。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
