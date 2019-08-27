---
title: CComPtrBase 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 689221ec77b21fc8bfaed2e929aee5402a4bc676
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496979"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 類別

這個類別會使用以 COM 為基礎的記憶體常式來提供智慧型指標類別的基礎。

## <a name="syntax"></a>語法

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>參數

*T*<br/>
智慧型指標所要參考的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|呼叫這個方法, 在`CComPtrBase`的連接點和用戶端的接收之間建立連接。|
|[CComPtrBase::Attach](#attach)|呼叫此方法以取得現有指標的擁有權。|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|呼叫這個方法, 以建立與指定的類別識別碼或程式識別碼相關聯之類別的物件。|
|[CComPtrBase::CopyTo](#copyto)|呼叫這個方法, 將`CComPtrBase`指標複製到另一個指標變數。|
|[CComPtrBase::Detach](#detach)|呼叫此方法以釋放指標的擁有權。|
|[CComPtrBase::IsEqualObject](#isequalobject)|呼叫這個方法, 以檢查指定`IUnknown`的是否指向`CComPtrBase`與物件相關聯的相同物件。|
|[CComPtrBase::QueryInterface](#queryinterface)|呼叫這個方法, 以傳回指定介面的指標。|
|[CComPtrBase::Release](#release)|呼叫這個方法以釋放介面。|
|[CComPtrBase::SetSite](#setsite)|呼叫這個方法, 將`CComPtrBase`物件的網站設定`IUnknown`為父物件的。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComPtrBase:: operator T *](#operator_t_star)|Cast 運算子。|
|[CComPtrBase:: operator!](#operator_not)|NOT 運算子。|
|[CComPtrBase:: operator &](#operator_amp)|& 運算子。|
|[CComPtrBase:: operator *](#operator_star)|\* 運算子。|
|[CComPtrBase:: operator <](#ccomptrbase__operator lt)|小於運算子。|
|[CComPtrBase:: operator = =](#operator_eq_eq)|等號比較運算子。|
|[CComPtrBase:: operator->](#operator_ptr)|成員指標運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComPtrBase::p](#p)|指標資料成員變數。|

## <a name="remarks"></a>備註

這個類別會提供其他使用 COM 記憶體管理常式 (例如[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr](../../atl/reference/ccomptr-class.md)) 之智慧型指標的基礎。 衍生類別會加入自己的函式和運算子, 但依賴所提供`CComPtrBase`的方法。

## <a name="requirements"></a>需求

**標頭:** atlcomcli.h。h

##  <a name="advise"></a>CComPtrBase:: Advise

呼叫這個方法, 在`CComPtrBase`的連接點和用戶端的接收之間建立連接。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>參數

*pUnk*<br/>
用戶端的`IUnknown`指標。

*iid*<br/>
連接點的 GUID。 一般來說, 這與連接點所管理的傳出介面相同。

*pdw*<br/>
可唯一識別連接之 cookie 的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[AtlAdvise](connection-point-global-functions.md#atladvise) 。

##  <a name="attach"></a>CComPtrBase:: Attach

呼叫此方法以取得現有指標的擁有權。

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>參數

*p2*<br/>
`CComPtrBase`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

`Attach`在現有的[CComPtrBase::p](#p)成員變數上呼叫[CComPtrBase:: Release](#release) , 然後將 p2 `CComPtrBase::p`指派給。 當物件取得指標的擁有權時, 它會在指標`Release`上自動呼叫, 如果物件上的參考計數為 0, 則會刪除指標和任何已配置的資料。 `CComPtrBase`

##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase

解構函式。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>備註

釋放所指向`CComPtrBase`的介面。

##  <a name="cocreateinstance"></a>CComPtrBase:: CoCreateInstance

呼叫這個方法, 以建立與指定的類別識別碼或程式識別碼相關聯之類別的物件。

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

*szProgID*<br/>
ProgID 的指標, 用來復原 CLSID。

*pUnkOuter*<br/>
如果是 Null, 則表示物件不會建立為匯總的一部分。 如果為非 Null, 則為匯總物件`IUnknown`介面的指標 (控制`IUnknown`)。

*dwClsContext*<br/>
用來管理新建立之物件的程式碼會在其中執行的內容。

*rclsid*<br/>
與將用來建立物件的資料和程式碼相關聯的 CLSID。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回 REGDB_E_CLASSNOTREG、CLASS_E_NOAGGREGATION、CO_E_CLASSSTRING 或 E_NOINTERFACE。 如需這些錯誤的說明, 請參閱[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)和[CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) 。

### <a name="remarks"></a>備註

如果呼叫方法的第一種形式, 則會使用[CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)來復原 CLSID。 這兩個表單都會呼叫[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)。

在 debug build 中, 如果[CComPtrBase::p](#p)不等於 Null, 就會發生判斷提示錯誤。

##  <a name="copyto"></a>CComPtrBase:: CopyTo

呼叫這個方法, 將`CComPtrBase`指標複製到另一個指標變數。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>參數

*ppT*<br/>
將接收`CComPtrBase`指標的變數位址。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 失敗時傳回 E_POINTER。

### <a name="remarks"></a>備註

將指標複製到*ppT。* `CComPtrBase` [CComPtrBase::p](#p)成員變數上的參考計數會遞增。

如果*ppT*等於 Null, 將會傳回錯誤 HRESULT。 在 debug 組建中, 如果*ppT*等於 Null, 就會發生判斷提示錯誤。

##  <a name="detach"></a>CComPtrBase::D etach

呼叫此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回指標的複本。

### <a name="remarks"></a>備註

釋放指標的擁有權, 將[CComPtrBase::p](#p)資料成員變數設定為 Null, 並傳回指標的複本。

##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject

呼叫這個方法, 以檢查指定`IUnknown`的是否指向`CComPtrBase`與物件相關聯的相同物件。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>參數

*pOther*<br/>
要比較的 `IUnknown *`。

### <a name="return-value"></a>傳回值

如果物件相同, 則傳回 true, 否則傳回 false。

##  <a name="operator_not"></a>CComPtrBase:: operator!

NOT 運算子。

```
bool operator!() const throw();
```

### <a name="return-value"></a>傳回值

如果`CComHeapPtr`指標等於 Null, 則傳回 true, 否則傳回 false。

##  <a name="operator_amp"></a>CComPtrBase:: operator&amp;

& 運算子。

```
T** operator&() throw();
```

### <a name="return-value"></a>傳回值

傳回`CComPtrBase`物件所指向之物件的位址。

##  <a name="operator_star"></a>CComPtrBase:: operator\*

\* 運算子。

```
T& operator*() const throw();
```

### <a name="return-value"></a>傳回值

傳回[CComPtrBase::p](#p)的值。也就是`CComPtrBase`物件所參考物件的指標。

如果是 debug 組建, 如果[CComPtrBase::p](#p)不等於 Null, 就會發生判斷提示錯誤。

##  <a name="operator_eq_eq"></a>CComPtrBase:: operator = =

等號比較運算子。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>參數

*pT*<br/>
物件的指標。

### <a name="return-value"></a>傳回值

如果`CComPtrBase`和*pT*指向相同的物件, 則傳回 true, 否則傳回 false。

##  <a name="operator_ptr"></a>CComPtrBase:: operator-&gt;

成員指標運算子。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>傳回值

傳回[CComPtrBase::p](#p)資料成員變數的值。

### <a name="remarks"></a>備註

使用這個運算子, 即可呼叫物件所`CComPtrBase`指向之類別中的方法。 在「偵錯工具組建」中, 如果`CComPtrBase`資料成員指向 Null, 就會發生判斷提示失敗。

##  <a name="operator_lt"></a>CComPtrBase:: operator&lt;

小於運算子。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>參數

*pT*<br/>
物件的指標。

### <a name="return-value"></a>傳回值

如果目前物件所管理的指標小於正進行比較的指標, 則傳回 true。

##  <a name="operator_t_star"></a>CComPtrBase:: operator T\*

Cast 運算子。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

傳回類別樣板中所定義之物件資料類型的指標。

##  <a name="p"></a>CComPtrBase::p

指標資料成員變數。

```
T* p;
```

### <a name="remarks"></a>備註

這個成員變數會保存指標資訊。

##  <a name="queryinterface"></a>CComPtrBase:: QueryInterface

呼叫這個方法, 以傳回指定介面的指標。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>參數

*Q*<br/>
需要其介面指標的物件類型。

*pp*<br/>
接收所要求介面指標的輸出變數位址。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回 E_NOINTERFACE。

### <a name="remarks"></a>備註

這個方法會呼叫[IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))。

在 debug 組建中, 如果*pp*不等於 Null, 就會發生判斷提示錯誤。

##  <a name="release"></a>CComPtrBase:: Release

呼叫這個方法以釋放介面。

```
void Release() throw();
```

### <a name="remarks"></a>備註

介面已釋放, 而且[CComPtrBase::p](#p)設定為 Null。

##  <a name="setsite"></a>CComPtrBase:: SetSite

呼叫這個方法, 將`CComPtrBase`物件的網站設定`IUnknown`為父物件的。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>參數

*punkParent*<br/>
父系`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法會呼叫[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
