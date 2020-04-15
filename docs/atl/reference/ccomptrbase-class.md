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
ms.openlocfilehash: 7d450f7762b39d7fa8fae07230690eecb8edbb4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327455"
---
# <a name="ccomptrbase-class"></a>CComPtrBase 類別

此類為使用基於 COM 的記憶體例程的智慧指標提供了基礎。

## <a name="syntax"></a>語法

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>參數

*T*<br/>
要由智慧指標引用的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPtrBase:*CComPtrBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComPtrBase:建議](#advise)|呼叫此方法以在`CComPtrBase`連接點和用戶端的接收器之間創建連接。|
|[CComPtrBase:附加](#attach)|調用此方法以獲取現有指標的擁有權。|
|[CComPtrBase::共同建立實體](#cocreateinstance)|呼叫此方法以建立與指定的類 ID 或程式 ID 關聯的類的物件。|
|[CComptrBase::複製到](#copyto)|調用此方法以將`CComPtrBase`指標複製到另一個指標變數。|
|[CComPtrBase::D](#detach)|調用此方法以釋放指標的擁有權。|
|[CComPtrBase:是等價物](#isequalobject)|呼叫此方法以檢查指定`IUnknown`點是否指向`CComPtrBase`與 物件關聯的同一物件。|
|[CComPtrBase:查詢介面](#queryinterface)|呼叫此方法以返回指向指定介面的指標。|
|[CComPtrBase:發佈](#release)|調用此方法以釋放介面。|
|[CComPtrBase:設定網站](#setsite)|調用此方法將`CComPtrBase`物件的網站設置為`IUnknown`父物件的網站。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComPtrBase::運算子 T*](#operator_t_star)|強制轉換運算符。|
|[CComPtrBase:操作員!](#operator_not)|NOT 運算符。|
|[CComPtrBase::操作員&](#operator_amp)|& 運算子。|
|[CComPtrBase:操作員 |](#operator_star)|\* 運算子。|
|[CComPtrBase::操作員<](#ccomptrbase__operator lt)|小於運算符。|
|[CComPtrBase:運算符 |](#operator_eq_eq)|相等運算符。|
|[CComPtrBase:運算元 ->](#operator_ptr)|指向成員的指標運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComPtrBase::p](#p)|指標數據成員變數。|

## <a name="remarks"></a>備註

此類為使用 COM 記憶體管理例程的其他智慧指標(如[CComQIPtr](../../atl/reference/ccomqiptr-class.md)和[CComPtr)](../../atl/reference/ccomptr-class.md)提供了基礎。 派生類添加自己的構造函數和運算符,但依賴於提供`CComPtrBase`的方法。

## <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase:建議

呼叫此方法以在`CComPtrBase`連接點和用戶端的接收器之間創建連接。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>參數

*龐克*<br/>
指向用戶端的`IUnknown`指標。

*Iid*<br/>
連接點的 GUID。 通常,這與連接點管理的傳出介面相同。

*pdw*<br/>
指向唯一標識連接的 Cookie 的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 Atl 建議](connection-point-global-functions.md#atladvise)。

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase:附加

調用此方法以獲取現有指標的擁有權。

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>參數

*p2*<br/>
該`CComPtrBase`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

`Attach`呼叫[CComPtrBase::釋放](#release)現有[CComPtrBase::p](#p)成員變數,然後將*p2*分配給`CComPtrBase::p`。 當物件`CComPtrBase`取得指標的擁有權時,它將自動調`Release`用 指標,如果物件的引用計數變為 0,該指標將刪除指標和任何已分配的數據。

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase:*CComPtrBase

解構函式。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>備註

釋放 所指向`CComPtrBase`的介面。

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::共同建立實體

呼叫此方法以建立與指定的類 ID 或程式 ID 關聯的類的物件。

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
指向 ProgID 的指標,用於恢復 CLSID。

*pUnkOuter*<br/>
如果 NULL,則指示物件不是作為聚合的一部分創建的。 如果非 NULL,則是指向聚合物件的介面(`IUnknown``IUnknown`控制 ) 的指標。

*dwCls 上下文*<br/>
管理新創建對象的代碼將在其中運行的上下文。

*rclsid*<br/>
與將用於創建物件的數據和代碼關聯的 CLSID。

### <a name="return-value"></a>傳回值

返回S_OK成功,或REGDB_E_CLASSNOTREG,CLASS_E_NOAGGREGATION,CO_E_CLASSSTRING或E_NOINTERFACE失敗。 有關這些錯誤的說明,請參閱[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)和[CLSID FromProgID。](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)

### <a name="remarks"></a>備註

如果呼叫方法的第一種形式,[則 CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)用於恢復 CLSID。 然後,兩個表單調用[CoCreateClassinstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)。

在除錯產生中,如果[CComPtrBase::p](#p)不等於 NULL,則會發生斷言錯誤。

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComptrBase::複製到

調用此方法以將`CComPtrBase`指標複製到另一個指標變數。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>參數

*Ppt*<br/>
將接收指標的變數的位址`CComPtrBase`。

### <a name="return-value"></a>傳回值

返回S_OK成功,E_POINTER失敗。

### <a name="remarks"></a>備註

將`CComPtrBase`指標複製到*ppT*。 [CComPtrBase::p](#p)成員變數上的引用計數遞增。

如果*ppT*等於 NULL,則將傳回錯誤 HRESULT。 在除錯產生中,如果*ppT*等於NULL,則會發生斷言錯誤。

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::D

調用此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

返回指標的副本。

### <a name="remarks"></a>備註

釋放指標的擁有權,將[CComPtrBase::p](#p)數據成員變數設置為 NULL,並返回指標的副本。

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase:是等價物

呼叫此方法以檢查指定`IUnknown`點是否指向`CComPtrBase`與 物件關聯的同一物件。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>參數

*p其他*<br/>
要比較的 `IUnknown *`。

### <a name="return-value"></a>傳回值

如果物件相同,則返回 true,否則為 false。

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase:操作員!

NOT 運算符。

```
bool operator!() const throw();
```

### <a name="return-value"></a>傳回值

如果指標等於`CComHeapPtr`NULL,則傳回 true,否則為 false。

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::運算子&amp;

& 運算子。

```
T** operator&() throw();
```

### <a name="return-value"></a>傳回值

傳回物件指向的物件的`CComPtrBase`位址 。

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::運算子\*

\* 運算子。

```
T& operator*() const throw();
```

### <a name="return-value"></a>傳回值

返回[CComPtrBase::p](#p)的值。即指向物件引用的物件的`CComPtrBase`指標。

如果除錯產生,如果[CComPtrBase::p](#p)不等於 NULL,則會發生斷言錯誤。

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase:運算符 |

相等運算符。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>參數

*鉑*<br/>
指向物件的指標。

### <a name="return-value"></a>傳回值

如果`CComPtrBase`和*pT*指向同一物件,則返回 true,否則為 false。

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase:運算子 -&gt;

指標到成員運算符。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>傳回值

返回[CComPtrBase::p](#p)資料成員變數的值。

### <a name="remarks"></a>備註

使用此運算符呼叫`CComPtrBase`物件指向的類中的方法。 在除錯產生中,如果資料成員指向 NULL,`CComPtrBase`則會發生斷言失敗。

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::運算子&lt;

小於運算符。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>參數

*鉑*<br/>
指向物件的指標。

### <a name="return-value"></a>傳回值

如果當前物件管理的指標小於要比較它的指標,則返回 true。

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::運算子 T\*

強制轉換運算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

返回指向類範本中定義的對象數據類型的指標。

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

指標數據成員變數。

```
T* p;
```

### <a name="remarks"></a>備註

此成員變數保存指標資訊。

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase:查詢介面

呼叫此方法以返回指向指定介面的指標。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>參數

*Q*<br/>
需要介面指標的物件類型。

*Pp*<br/>
接收請求的介面指標的輸出變數的位址。

### <a name="return-value"></a>傳回值

返回S_OK成功,或E_NOINTERFACE失敗。

### <a name="remarks"></a>備註

此方法呼叫[I 未知:查詢介面](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))。

在除錯產生中,如果*pp*不等於NULL,則會發生斷言錯誤。

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase:發佈

調用此方法以釋放介面。

```
void Release() throw();
```

### <a name="remarks"></a>備註

介面被釋放[,CComPtrBase::p](#p)設置為 NULL。

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase:設定網站

調用此方法將`CComPtrBase`物件的網站設置為`IUnknown`父物件的網站。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>參數

*朋克家長*<br/>
指向父級`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法呼叫[AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
