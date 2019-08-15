---
title: CBindStatusCallback 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497607"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 類別

這個類別會實作 `IBindStatusCallback` 介面。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別包含將會在收到資料時呼叫的函數。

*nBindFlags*<br/>
指定[GetBindInfo](#getbindinfo)所傳回的系結旗標。 預設的執行會將系結設定為非同步, 並抓取最新版本的資料/物件, 而不會將抓取的資料儲存在磁碟快取中。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|建構函式。|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|會啟動下載程式、建立`CBindStatusCallback`物件, 以及呼叫`StartAsyncDownload`的靜態方法。|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|由非同步標記呼叫, 以要求要建立之系結類型的資訊。|
|[CBindStatusCallback::GetPriority](#getpriority)|由非同步標記呼叫以取得系結作業的優先順序。 ATL 執行`E_NOTIMPL`會傳回。|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|呼叫以提供資料給您的應用程式, 因為它可供使用。 讀取資料, 然後呼叫傳遞給它的函式來使用資料。|
|[CBindStatusCallback::OnLowResource](#onlowresource)|當資源不足時呼叫。 ATL 實作為傳回 S_OK。|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|由非同步標記呼叫, 將物件介面指標傳遞至您的應用程式。 ATL 實作為傳回 S_OK。|
|[CBindStatusCallback::OnProgress](#onprogress)|呼叫以指出資料下載進程的進度。 ATL 實作為傳回 S_OK。|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|在啟動系結時呼叫。|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|停止非同步資料傳輸時呼叫。|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|將可用的位元組和讀取的位元組初始化為零、從 URL 建立推播類型資料流程物件, 並在`OnDataAvailable`每次可用資料時呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|可讀取的位元組數目。|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|讀取的位元組總數。|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|當資料可供使用時, 所呼叫之函式的指標。|
|[CBindStatusCallback::m_pT](#m_pt)|要求非同步資料傳輸之物件的指標。|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|目前系結作業的[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)介面指標。|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|目前系結作業介面的指標。`IBinding`|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|要使用之 URL 的[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面指標。|
|[CBindStatusCallback::m_spStream](#m_spstream)|資料傳輸之[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。|

## <a name="remarks"></a>備註

`CBindStatusCallback` 類別會實作 `IBindStatusCallback` 介面。 `IBindStatusCallback`必須由您的應用程式實作為, 讓它可以接收來自非同步資料傳輸的通知。 系統所提供的非同步標記會使用`IBindStatusCallback`方法, 來傳送和接收與您的物件之間的非同步資料傳輸相關資訊。

一般而言, `CBindStatusCallback`物件會與特定的系結作業相關聯。 例如, 在[非同步](../../overview/visual-cpp-samples.md)範例中, 當您設定 URL 屬性時, 它會`CBindStatusCallback` `Download`在對的呼叫中建立物件:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

非同步標記會在有資料時`OnData` , 使用回呼函式來呼叫您的應用程式。 非同步標記是由系統所提供。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

建構函式。

```
CBindStatusCallback();
```

### <a name="remarks"></a>備註

建立物件, 以接收有關非同步資料傳輸的通知。 通常會針對每個系結作業建立一個物件。

此函數也會將[m_pT](#m_pt)和[M_PFUNC](#m_pfunc)初始化為 Null。

##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback

解構函式。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="download"></a>CBindStatusCallback::D 下載

建立物件, 並呼叫`StartAsyncDownload`以從指定的 URL 以非同步方式開始下載資料。 `CBindStatusCallback`

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>參數

*pT*<br/>
在要求非同步資料傳輸之物件的指標。 `CBindStatusCallback`物件是在這個物件的類別上範本化。

*pFunc*<br/>
在函式的指標, 這個函式會接收讀取的資料。 函式是物件的類型`T`類別的成員。 如需語法和範例, 請參閱[StartAsyncDownload](#startasyncdownload) 。

*bstrURL*<br/>
在要從中取得資料的 URL。 可以是任何有效的 URL 或檔案名。 不可以是 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
在`IUnknown`容器的。 預設值為 Null。

*bRelative*<br/>
在指出 URL 為相對或絕對的旗標。 預設為 FALSE, 表示 URL 是絕對的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

每次資料可供使用時, 都會透過`OnDataAvailable`傳送給物件。 `OnDataAvailable`讀取資料, 並呼叫*pFunc*所指向的函式 (例如, 儲存資料或將其列印至螢幕)。

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

呼叫以告知標記如何系結。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>參數

*pgrfBSCF*<br/>
脫銷BINDF 列舉值的指標, 指出系結作業的執行方式。 根據預設, 會使用下列列舉值來設定:

BINDF_ASYNCHRONOUS 非同步下載。

當`OnDataAvailable`資料無法使用時, BINDF_ASYNCSTORAGE 會傳回 E_PENDING, 而不是封鎖, 直到資料可供使用為止。

BINDF_GETNEWESTVERSION 系結作業應該會取得最新版本的資料。

BINDF_NOWRITECACHE 系結作業不應將抓取的資料儲存在磁碟快取中。

*pbindinfo*<br/>
[in、out]`BINDINFO`結構的指標, 提供有關物件要如何進行系結的詳細資訊。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

預設的執行會將系結設定為非同步, 並使用資料推送模型。 在資料推送模型中, 標記會驅動非同步系結作業, 並在有可用的新資料時持續通知用戶端。

##  <a name="getpriority"></a>CBindStatusCallback:: GetPriority

由非同步標記呼叫以取得系結作業的優先順序。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>參數

*pnPriority*<br/>
脫銷成功時, 會收到優先順序的**長**變數位址。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

可以用來儲存可讀取的位元組數目。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>備註

在中`StartAsyncDownload`初始化為零。

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

在非同步資料傳輸中讀取的累計位元組總數。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>備註

每次`OnDataAvailable`由實際讀取的位元組數目所呼叫時, 都會遞增。 在中`StartAsyncDownload`初始化為零。

##  <a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

在讀取可用的資料`m_pFunc` `OnDataAvailable`之後, 會呼叫所指向的函式 (例如, 用來儲存資料或將其列印至螢幕)。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>備註

所指向`m_pFunc`的函式是物件類別的成員, 且具有下列語法:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

要求非同步資料傳輸之物件的指標。

```
T* m_pT;
```

### <a name="remarks"></a>備註

`CBindStatusCallback`物件是在這個物件的類別上範本化。

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)介面的指標, 可提供系結內容 (儲存特定標記系結作業相關資訊的物件) 的存取權。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>備註

在中`StartAsyncDownload`初始化。

##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

目前系結作業`IBinding`介面的指標。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>備註

在中`OnStartBinding`初始化, 並`OnStopBinding`在中發行。

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

要使用之 URL 的[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面指標。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>備註

在中`StartAsyncDownload`初始化。

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

目前系結作業之[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>備註

當 BCSF `OnDataAvailable`旗標`STGMEDIUM`為 BCSF_FIRSTDATANOTIFICATION 時, 從結構中初始化, 並在 BCSF 旗標為 BCSF_LASTDATANOTIFICATION 時釋放。

##  <a name="ondataavailable"></a>CBindStatusCallback:: OnDataAvailable

系統提供的非同步標記會呼叫`OnDataAvailable` , 以便在物件可供使用時, 提供資料給它。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>參數

*grfBSCF*<br/>
在BSCF 列舉值。 下列一或多個動作:BSCF_FIRSTDATANOTIFICATION、BSCF_INTERMEDIARYDATANOTIFICATION 或 BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
在自系結開始後可用的資料累計量 (以位元組為單位)。 可以是零, 表示資料量不相關, 或沒有可用的特定數量。

*pformatetc*<br/>
在[FORMATETC](/windows/win32/com/the-formatetc-structure)結構的指標, 其中包含可用資料的格式。 如果沒有格式, 可以 CF_Null。

*pstgmed*<br/>
在[STGMEDIUM](/windows/win32/com/the-stgmedium-structure)結構的指標, 其中包含目前可用的實際資料。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

`OnDataAvailable`讀取資料, 然後呼叫物件之類別的方法 (例如, 儲存資料或將其列印至螢幕)。 如需詳細資訊, 請參閱[CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) 。

##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource

當資源不足時呼叫。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留的。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

由非同步標記呼叫, 將物件介面指標傳遞至您的應用程式。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>參數

*riid*<br/>
所要求介面的介面識別碼。 未使用。

*punk*<br/>
IUnknown 介面的位址。 未使用。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

呼叫以指出資料下載進程的進度。

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
未使用的不帶正負號長整數。

*ulStatusCode*<br/>
不帶正負號的長整數。 未使用。

*szStatusText*<br/>
字串值的位址。 未使用。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="onstartbinding"></a>CBindStatusCallback:: OnStartBinding

將資料成員[m_spBinding](#m_spbinding)設定為`IBinding` *pBinding*中的指標。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>參數

*dwReserved*<br/>
保留供未來使用。

*pBinding*<br/>
在目前系結作業的 IBinding 介面位址。 這不可以是 Null。 用戶端應該在此指標上呼叫 AddRef, 以保留系結物件的參考。

##  <a name="onstopbinding"></a>CBindStatusCallback:: OnStopBinding

釋放資料`IBinding`成員[m_spBinding](#m_spbinding)中的指標。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>參數

*hresult*<br/>
從系結作業傳回的狀態碼。

*szError*<br/>
字串值的位址。 未使用。

### <a name="remarks"></a>備註

由系統提供的非同步標記呼叫, 表示系結作業結束。

##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

開始從指定的 URL 以非同步方式下載資料。

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>參數

*pT*<br/>
在要求非同步資料傳輸之物件的指標。 `CBindStatusCallback`物件是在這個物件的類別上範本化。

*pFunc*<br/>
在函式的指標, 這個函式會接收所讀取的資料。 函式是物件的類型`T`類別的成員。 如需語法和範例, 請參閱**備註**。

*bstrURL*<br/>
在要從中取得資料的 URL。 可以是任何有效的 URL 或檔案名。 不可以是 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
在`IUnknown`容器的。 預設值為 Null。

*bRelative*<br/>
在指出 URL 為相對或絕對的旗標。 預設為 FALSE, 表示 URL 是絕對的。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

每次資料可供使用時, 都會透過`OnDataAvailable`傳送給物件。 `OnDataAvailable`讀取資料, 並呼叫*pFunc*所指向的函式 (例如, 儲存資料或將其列印至螢幕)。

*PFunc*所指向的函式是物件類別的成員, 且具有下列語法:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

在下列範例中 (取自[非同步](../../overview/visual-cpp-samples.md)範例), `OnData`函式會將接收的資料寫入文字方塊中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
