---
title: CComClassFactory2 類別
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: e34ebffc937c3e4ef1272fdf13ddcde7513d28e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497464"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 類別

這個類別會實[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面。

## <a name="syntax"></a>語法

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>參數

*license*<br/>
實作用下列靜態函式的類別:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|建立指定之 CLSID 的物件。|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|提供授權金鑰後, 會建立指定之 CLSID 的物件。|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|抓取描述 Class Factory 授權功能的資訊。|
|[CComClassFactory2::LockServer](#lockserver)|鎖定記憶體中的 Class Factory。|
|[CComClassFactory2::RequestLicKey](#requestlickey)|建立並傳回授權金鑰。|

## <a name="remarks"></a>備註

`CComClassFactory2`會執行[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面, 這是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的延伸模組。 `IClassFactory2`透過授權控制物件的建立。 在授權的電腦上執行的 Class Factory 可以提供執行時間授權金鑰。 當完整的電腦授權不存在時, 此授權金鑰可讓應用程式具現化物件。

ATL 物件通常會藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)來取得 Class Factory。 這個類別包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), 其會將[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)宣告為預設 Class Factory。 若要`CComClassFactory2`使用, 請在物件的類別定義中指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense``CComClassFactory2`, 的樣板參數必須實作用`VerifyLicenseKey`、 `GetLicenseKey`和`IsLicenseValid`的靜態函式。 以下是簡單授權類別的範例:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`衍生自`CComClassFactory2Base`和*授權*。 `CComClassFactory2Base`接著, 衍生自`IClassFactory2`和。 `CComObjectRootEx< CComGlobalsThreadModel >`

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="createinstance"></a>CComClassFactory2:: CreateInstance

建立指定之 CLSID 的物件, 並抓取這個物件的介面指標。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在如果將物件建立為匯總的一部分, 則*pUnkOuter*必須是外部未知的。 否則, *pUnkOuter*必須是 Null。

*riid*<br/>
在所要求介面的 IID。 如果*pUnkOuter*為非 Null, 則*riid*必須是`IID_IUnknown`。

*ppvObj*<br/>
脫銷由*riid*識別之介面指標的指標。 如果物件不支援這個介面, *ppvObj*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

需要完整授權的電腦。 如果完整電腦授權不存在, 請呼叫[CreateInstanceLic](#createinstancelic)。

##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic

類似于[CreateInstance](#createinstance), 但`CreateInstanceLic`需要授權金鑰。

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
在如果將物件建立為匯總的一部分, 則*pUnkOuter*必須是外部未知的。 否則, *pUnkOuter*必須是 Null。

*pUnkReserved*<br/>
在未使用。 必須是 Null。

*riid*<br/>
在所要求介面的 IID。 如果*pUnkOuter*為非 Null, 則*riid*必須是`IID_IUnknown`。

*bstrKey*<br/>
在先前從的呼叫`RequestLicKey`取得的執行時間授權金鑰。 建立物件時需要此金鑰。

*ppvObject*<br/>
脫銷由*riid*指定之介面指標的指標。 如果物件不支援這個介面, *ppvObject*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

您可以使用[RequestLicKey](#requestlickey)取得授權金鑰。 若要在未授權的電腦上建立物件, 您必須呼叫`CreateInstanceLic`。

##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

以描述 Class Factory 授權功能的資訊填入[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)結構。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>參數

*pLicInfo*<br/>
脫銷結構的`LICINFO`指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此`fRuntimeKeyAvail`結構的成員指出, 在指定授權金鑰的情況下, Class Factory 是否允許在未授權的電腦上建立物件。 *FLicVerified*成員指出是否有完整的電腦授權存在。

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

分別呼叫`_Module::Lock`和`_Module::Unlock`, 以遞增和遞減模組鎖定計數。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>參數

*fLock*<br/>
在若為 TRUE, 則鎖定計數會遞增;否則, 鎖定計數就會遞減。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`_Module`指的是[CComModule](../../atl/reference/ccommodule-class.md)的全域實例或衍生自它的類別。

呼叫`LockServer`可讓用戶端保存到 Class Factory, 以便快速建立多個物件。

##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey

建立並傳回授權金鑰, 前提是[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)結構`fRuntimeKeyAvail`的成員為 TRUE。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
在未使用。 必須為零。

*pbstrKey*<br/>
脫銷授權金鑰的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

呼叫[CreateInstanceLic](#createinstancelic)以在未授權的電腦上建立物件時, 需要授權金鑰。 如果`fRuntimeKeyAvail`為 FALSE, 則只能在完整授權的電腦上建立物件。

呼叫[GetLicInfo](#getlicinfo)以取出的值`fRuntimeKeyAvail`。

## <a name="see-also"></a>另請參閱

[CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別總覽](../../atl/atl-class-overview.md)
