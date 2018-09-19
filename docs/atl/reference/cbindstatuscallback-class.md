---
title: CBindStatusCallback 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
dev_langs:
- C++
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a816d10a0cb9665938e77ae8c649464b7b6768c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108478"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 類別

這個類別會實作 `IBindStatusCallback` 介面。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
您包含收到資料時所呼叫的函式的類別。

*nBindFlags*<br/>
指定所傳回的繫結旗標[GetBindInfo](#getbindinfo)。 預設實作設定繫結還是非同步、 擷取資料/物件的最新版本並不會儲存在磁碟快取中擷取的資料。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|建構函式。|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|啟動下載程序的靜態方法會建立`CBindStatusCallback`物件，並呼叫`StartAsyncDownload`。|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|呼叫所建立的繫結的型別上的要求資訊的非同步 moniker。|
|[CBindStatusCallback::GetPriority](#getpriority)|若要取得繫結作業的優先順序非同步 moniker 所呼叫。 ATL 實作會傳回`E_NOTIMPL`。|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|呼叫以提供資料給您的應用程式，可供使用。 會讀取資料，然後呼叫函式傳遞給它使用的資料。|
|[CBindStatusCallback::OnLowResource](#onlowresource)|當資源過低時呼叫。 ATL 實作會傳回 S_OK。|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|呼叫非同步 moniker，將您的應用程式的物件介面指標。 ATL 實作會傳回 S_OK。|
|[CBindStatusCallback::OnProgress](#onprogress)|呼叫以表示資料下載程序的進度。 ATL 實作會傳回 S_OK。|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|在啟動繫結時呼叫。|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|當非同步資料傳輸已停止時呼叫。|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|初始化可用位元組，並為零，讀取位元組從 URL，並呼叫建立推播類型的資料流物件`OnDataAvailable`每次資料可供使用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|可讀取的位元組數目。|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|讀取的位元組總數。|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|當資料可供使用時，就會呼叫之函式指標。|
|[CBindStatusCallback::m_pT](#m_pt)|要求非同步資料傳輸物件的指標。|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|指標[IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx)目前繫結作業的介面。|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|指標`IBinding`目前繫結作業的介面。|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|指標[IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)介面要使用的 URL。|
|[CBindStatusCallback::m_spStream](#m_spstream)|指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)資料傳輸的介面。|

## <a name="remarks"></a>備註

`CBindStatusCallback` 類別會實作 `IBindStatusCallback` 介面。 `IBindStatusCallback` 必須實作您的應用程式讓它可以從非同步資料傳輸接收的通知。 使用系統提供的非同步 moniker`IBindStatusCallback`方法來傳送和接收非同步資料的相關資訊傳送至並從您的物件。

一般而言，`CBindStatusCallback`物件與特定的繫結作業有關聯。 例如，在[非同步](../../visual-cpp-samples.md)範例中，當您設定 [URL] 屬性中，它會建立`CBindStatusCallback`呼叫中的物件`Download`:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

非同步 moniker 會使用回呼函式`OnData`時要呼叫您的應用程式資料。 非同步 moniker 是系統所提供。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

建構函式。

```
CBindStatusCallback();
```

### <a name="remarks"></a>備註

建立要接收通知相關的非同步資料傳輸物件。 一般而言，每個繫結作業會建立一個物件。

建構函式也會初始化[m_pT](#m_pt)並[m_pFunc](#m_pfunc)為 NULL。

##  <a name="dtor"></a>  CBindStatusCallback:: ~ CBindStatusCallback

解構函式。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="download"></a>  CBindStatusCallback::Download

會建立`CBindStatusCallback`物件並呼叫`StartAsyncDownload`開始以非同步方式下載資料，從指定的 URL。

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
[in]要求非同步資料傳輸物件的指標。 `CBindStatusCallback`物件這個物件的類別樣板化。

*pFunc*<br/>
[in]接收資料讀取函式的指標。 函式是物件的類別型別的成員`T`。 請參閱[StartAsyncDownload](#startasyncdownload)如語法和範例。

*Ibttransportconfig*<br/>
[in]若要取得資料的 URL。 可以是任何有效的 URL 或檔案名稱。 不可以是 NULL。 例如: 

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in]`IUnknown`的容器。 預設為 NULL。

*bRelative*<br/>
[in]旗標，指出 URL 相對或絕對。 根據預設，這表示 URL 的 FALSE 是絕對路徑。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

每次的資料傳送至物件，可透過`OnDataAvailable`。 `OnDataAvailable` 讀取資料，並指向函式會呼叫*pFunc* （例如，若要將資料儲存或列印至螢幕）。

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

呼叫以告知如何繫結的 moniker。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>參數

*pgrfBSCF*<br/>
[out]BINDF 列舉值，表示如何繫結作業應該就會發生指標。 根據預設，設定下列的列舉值：

BINDF_ASYNCHRONOUS 非同步下載。

BINDF_ASYNCSTORAGE`OnDataAvailable`資料尚無法使用而不是封鎖，直到有可用資料時，傳回 E_PENDING。

BINDF_GETNEWESTVERSION 繫結作業應該擷取資料的最新版本。

繫結作業不應該儲存的 BINDF_NOWRITECACHE 擷取磁碟快取中的資料。

*pbindinfo*<br/>
[in、 out]指標`BINDINFO`結構讓物件如何想發生的繫結的詳細資訊。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

預設實作會設定為非同步，並將資料推送模型繫結。 在資料推入模型中，moniker 驅動非同步繫結作業，並持續在每當有新資料可用時通知用戶端。

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

若要取得繫結作業的優先順序非同步 moniker 所呼叫。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>參數

*pnPriority*<br/>
[out]位址**長**，成功時，接收變數的優先順序。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

可用來儲存可供讀取的位元組數目。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>備註

初始化為零`StartAsyncDownload`。

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

在非同步資料傳送的讀取位元組累計總數。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>備註

每次遞增`OnDataAvailable`呼叫實際讀取的位元組數目。 初始化為零`StartAsyncDownload`。

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

函式所指向`m_pFunc`會呼叫`OnDataAvailable`它讀取可用的資料 （例如，若要將資料儲存或列印至螢幕） 之後。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>備註

此函式所指的`m_pFunc`是物件之類別的成員，而且具有下列語法：

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

要求非同步資料傳輸物件的指標。

```
T* m_pT;
```

### <a name="remarks"></a>備註

`CBindStatusCallback`物件這個物件的類別樣板化。

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

指標[IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx)介面，可提供的繫結內容 （儲存特定的 moniker 繫結作業的相關資訊的物件） 的存取。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>備註

在初始化`StartAsyncDownload`。

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

指標`IBinding`目前繫結作業的介面。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>備註

在初始化`OnStartBinding`及發行的`OnStopBinding`。

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

指標[IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)介面要使用的 URL。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>備註

在初始化`StartAsyncDownload`。

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)目前繫結作業的介面。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>備註

在初始化`OnDataAvailable`從`STGMEDIUM`結構 BCSF 旗標是 BCSF_FIRSTDATANOTIFICATION 和釋放 BCSF 旗標時 BCSF_LASTDATANOTIFICATION 時。

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

系統提供的非同步 moniker 呼叫`OnDataAvailable`提供資料給物件，可供使用。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>參數

*grfBSCF*<br/>
[in]BSCF 列舉值。 一或多個項目： BSCF_FIRSTDATANOTIFICATION、 BSCF_INTERMEDIARYDATANOTIFICATION 或 BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
[in]（以位元組為單位） 的繫結開始之後，您可以使用資料的累積數量。 可以是零，表示的資料量無關，或特定數量變成可用。

*pformatetc*<br/>
[in]指標[FORMATETC](/windows/desktop/com/the-formatetc-structure)結構，其中包含可用的資料格式。 如果沒有任何格式，可以是 CF_NULL。

*pstgmed*<br/>
[in]指標[STGMEDIUM](/windows/desktop/com/the-stgmedium-structure)結構，其中保存目前可用的實際資料。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

`OnDataAvailable` 會讀取資料，然後呼叫您的物件類別 （例如，若要將資料儲存或列印至螢幕） 的方法。 請參閱[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)如需詳細資訊。

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

當資源過低時呼叫。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留的。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

呼叫非同步 moniker，將您的應用程式的物件介面指標。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>參數

*riid*<br/>
所要求介面的介面識別項。 未使用。

*punk*<br/>
IUnknown 介面的位址。 未使用。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

呼叫以表示資料下載程序的進度。

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>參數

*ulProgress*<br/>
不帶正負號的長整數。 未使用。

*ulProgressMax*<br/>
不帶正負號的長整數未使用。

*ulStatusCode*<br/>
不帶正負號的長整數。 未使用。

*szStatusText*<br/>
字串值的位址。 未使用。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

設定資料成員[m_spBinding](#m_spbinding)要`IBinding`中的指標*pBinding*。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留供未來使用。

*pBinding*<br/>
[in]在目前的 IBinding 介面位址繫結作業。 這不能是 NULL。 用戶端應該在繫結物件的參考，將這個指標上呼叫 AddRef。

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

版本`IBinding`中的資料成員的指標[m_spBinding](#m_spbinding)。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>參數

*hresult*<br/>
繫結作業所傳回的狀態碼。

*szError*<br/>
字串值的位址。 未使用。

### <a name="remarks"></a>備註

表示繫結作業結束，系統提供的非同步 moniker 所呼叫。

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

啟動非同步下載資料，從指定的 URL。

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
[in]要求非同步資料傳輸物件的指標。 `CBindStatusCallback`物件這個物件的類別樣板化。

*pFunc*<br/>
[in]函式來接收所讀取的資料指標。 函式是物件的類別型別的成員`T`。 請參閱**備註**如語法和範例。

*Ibttransportconfig*<br/>
[in]若要取得資料的 URL。 可以是任何有效的 URL 或檔案名稱。 不可以是 NULL。 例如: 

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in]`IUnknown`的容器。 預設為 NULL。

*bRelative*<br/>
[in]旗標，指出 URL 相對或絕對。 根據預設，這表示 URL 的 FALSE 是絕對路徑。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

每次的資料傳送至物件，可透過`OnDataAvailable`。 `OnDataAvailable` 讀取資料，並指向函式會呼叫*pFunc* （例如，若要將資料儲存或列印至螢幕）。

此函式所指向*pFunc*是物件之類別的成員，而且具有下列語法：

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

在下列範例 (取自[非同步](../../visual-cpp-samples.md)範例)，此函式`OnData`將接收的資料寫入至文字方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
