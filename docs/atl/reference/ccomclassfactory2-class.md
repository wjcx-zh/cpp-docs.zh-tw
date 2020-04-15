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
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321007"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 類別

此類實現[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面。

## <a name="syntax"></a>語法

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>參數

*許可證*<br/>
實作以下靜態函數的類別:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComClass 工廠2::建立實體](#createinstance)|建立指定的 CLSID 的物件。|
|[CComClassFactory2::建立實體](#createinstancelic)|給定授權金鑰,創建指定的 CLSID 的物件。|
|[CComClass工廠2::獲取資訊](#getlicinfo)|檢索描述類工廠許可功能的資訊。|
|[CComClass 工廠2::鎖伺服器](#lockserver)|將類工廠鎖定在記憶體中。|
|[CComClass 工廠2::請求鍵](#requestlickey)|建立並返回許可證金鑰。|

## <a name="remarks"></a>備註

`CComClassFactory2`實現[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)介面,這是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的擴展。 `IClassFactory2`通過許可證控制對象創建。 在許可電腦上執行的類工廠可以提供運行時許可證密鑰。 此許可證密鑰允許應用程式在不存在完整的計算機許可證時實例化物件。

ATL 物件通常透過[CComCoClass](../../atl/reference/ccomcoclass-class.md)獲得類工廠。 此類包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory),它聲明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)為預設類工廠。 要使用`CComClassFactory2`,請在物件的類定義中指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`的`CComClassFactory2`樣本參數必須實現靜態函數`VerifyLicenseKey``GetLicenseKey``IsLicenseValid`和 。 下面是一個簡單的授權類別的範例:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`衍生與`CComClassFactory2Base`*授權*。 `CComClassFactory2Base`反過來,派生自`IClassFactory2``CComObjectRootEx< CComGlobalsThreadModel >`和 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClass 工廠2::建立實體

建立指定的 CLSID 的物件並檢索指向此物件的介面指標。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>參數

*pUnkOuter*<br/>
[在]如果對像是作為聚合的一部分創建的,則*pUnkOuter*必須是外部未知物件。 否則 *,pUnkOuter*必須為 NULL。

*riid*<br/>
[在]請求介面的 IID。 如果*pUnkOuter*是非 NULL, 則`IID_IUnknown`*riid*必須為 。

*普夫奧比*<br/>
[出]指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObj*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

要求機器獲得完全許可。 如果不存在完整的計算機許可證,請調用[Create 實例。](#createinstancelic)

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::建立實體

與[CreateInstance](#createinstance)`CreateInstanceLic`類似, 但需要許可證金鑰的除外。

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
[在]如果對像是作為聚合的一部分創建的,則*pUnkOuter*必須是外部未知物件。 否則 *,pUnkOuter*必須為 NULL。

*pUnk*<br/>
[在]未使用。 必須是 Null。

*riid*<br/>
[在]請求介面的 IID。 如果*pUnkOuter*是非 NULL, 則`IID_IUnknown`*riid*必須為 。

*bstrKey*<br/>
[在]以前從調用`RequestLicKey`獲得的運行時許可證密鑰。 創建物件需要此鍵。

*ppvObject*<br/>
[出]指向*riid*指定的介面指標的指標。 如果物件不支援此介面,*則 ppvObject*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

您可以使用[RequestLicKey](#requestlickey)取得授權金鑰。 為了在未經授權的電腦上建立物件,必須呼叫`CreateInstanceLic`。

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClass工廠2::獲取資訊

使用描述類工廠許可功能的資訊填充[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)結構。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>參數

*pLicInfo*<br/>
[出]指向結構的`LICINFO`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此`fRuntimeKeyAvail`結構的成員指示在給定許可證密鑰的情況下,類工廠是否允許在未經許可的計算機上創建物件。 *fLic 驗證*成員指示是否存在完整的計算機許可證。

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClass 工廠2::鎖伺服器

遞增與遞減模組鎖定計數分別透過呼`_Module::Lock`叫`_Module::Unlock`與 。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>參數

*羊群*<br/>
[在]如果為 TRUE,則鎖計數將遞增;如果為 TRUE,則鎖定計數將遞增。否則,鎖計數將遞減。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`_Module`指[CComModule](../../atl/reference/ccommodule-class.md)的全域實例或從它派生的類。

調用`LockServer`允許用戶端保留類工廠,以便可以快速創建多個物件。

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClass 工廠2::請求鍵

創建並返回許可證密鑰,前提是`fRuntimeKeyAvail`[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)結構的成員為 TRUE。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>參數

*dw 保留*<br/>
[在]未使用。 必須為零。

*pbstrKey*<br/>
[出]指向許可證金鑰的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

呼叫[CreateA 實體設定 Lic](#createinstancelic)以在未授權的電腦上建立物件需要授權金鑰。 如果`fRuntimeKeyAvail`為 FALSE,則只能在完全許可的電腦上創建物件。

呼叫[GetLicInfo](#getlicinfo)以`fRuntimeKeyAvail`檢索的值。

## <a name="see-also"></a>另請參閱

[CComclass 工廠自動線程類別](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClass 工廠單頓類別](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[類別概觀](../../atl/atl-class-overview.md)
