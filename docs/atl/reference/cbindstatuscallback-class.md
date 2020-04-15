---
title: CBind 狀態回檔類別
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
ms.openlocfilehash: 6cdac444836574dd4d398571b71bb25363af5d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321227"
---
# <a name="cbindstatuscallback-class"></a>CBind 狀態回檔類別

此類別會實作 `IBindStatusCallback` 介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
包含將在接收數據時調用的函數的類。

*N 繫結旗*<br/>
指定[GetBindInfo](#getbindinfo)傳回的綁定標誌。 默認實現將綁定設置為非同步,檢索資料/物件的最新版本,並且不將檢索到的數據儲存在磁碟緩存中。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C綁定狀態回調::C綁定狀態回調](#cbindstatuscallback)|建構函式。|
|[C綁定狀態回調::*C綁定狀態回調](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBind狀態回撥::D自己的負載](#download)|啟動下載過程、創建`CBindStatusCallback`對象和`StartAsyncDownload`調用的靜態方法。|
|[CBind 狀態回撥::取得綁定資訊](#getbindinfo)|由非同步名字物件調用,以請求有關要建立的綁定類型的資訊。|
|[CBind 狀態回撥::取得優先順序](#getpriority)|由非同步名字物件調用,以獲得綁定操作的優先順序。 ATL 執行`E_NOTIMPL`到傳回 。|
|[CBind 狀態回撥::OnData 可用](#ondataavailable)|呼叫以在應用程式可用時向應用程式提供資料。 讀取數據,然後調用傳遞給它的函數以使用數據。|
|[CBind狀態回調::在低資源](#onlowresource)|在資源不足時調用。 ATL 實現返回S_OK。|
|[CBind 狀態回檔:開啟物件可用](#onobjectavailable)|由非同步名字物件調用,將對象介面指標傳遞給應用程式。 ATL 實現返回S_OK。|
|[CBind 狀態回撥::在進度上](#onprogress)|調用 以指示數據下載過程的進度。 ATL 實現返回S_OK。|
|[CBind 狀態回檔:打開繫結](#onstartbinding)|啟動綁定時調用。|
|[CBind 狀態回檔:打開繫結](#onstopbinding)|在異步數據傳輸停止時調用。|
|[CBind 狀態回撥::開始同步下載](#startasyncdownload)|初始化可用位元組和讀取到零的位元組,從網址來建立推送類型的流物件,並在每次資料`OnDataAvailable`可用時呼叫 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CBind狀態回撥::m_dwAvailableToRead](#m_dwavailabletoread)|可供讀取的位元組數。|
|[CBind狀態回撥::m_dwTotalRead](#m_dwtotalread)|讀取的位元組總數。|
|[CBind狀態回撥::m_pFunc](#m_pfunc)|指向數據可用時調用的函數的指標。|
|[CBind狀態回撥::m_pT](#m_pt)|指向請求非同步數據傳輸的物件的指標。|
|[CBind狀態回撥::m_spBindCtx](#m_spbindctx)|指向當前綁定操作的[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)介面。|
|[CBind狀態回撥::m_spBinding](#m_spbinding)|指向當前綁定`IBinding`操作的介面的指標。|
|[CBind狀態回撥::m_spMoniker](#m_spmoniker)|指向[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面的 URL。|
|[CBind狀態回撥::m_spStream](#m_spstream)|指向數據傳輸的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面。|

## <a name="remarks"></a>備註

`CBindStatusCallback` 類別會實作 `IBindStatusCallback` 介面。 `IBindStatusCallback`必須由應用程式實現,以便它可以從非同步資料傳輸接收通知。 系統提供的非同步名字項使用`IBindStatusCallback`方法發送和接收有關物件和物件中的非同步資料傳輸的資訊。

通常,該`CBindStatusCallback`物件與特定的綁定操作相關聯。 例如,在[ASYNC](../../overview/visual-cpp-samples.md)範例中,當您設定 URL 屬性`CBindStatusCallback`時,它會在調`Download`用 中創建一個物件,

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

非同步名字物件使用回檔函`OnData`數 在應用程式具有資料時調用應用程式。 非同步名字由系統提供。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>C綁定狀態回調::C綁定狀態回調

建構函式。

```
CBindStatusCallback();
```

### <a name="remarks"></a>備註

創建一個物件來接收有關非同步資料傳輸的通知。 通常,為每個綁定操作創建一個物件。

建構函數還會初始化[m_pT,](#m_pt)並將[m_pFunc](#m_pfunc)到 NULL。

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>C綁定狀態回調::*C綁定狀態回調

解構函式。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBind狀態回撥::D自己的負載

建立物件`CBindStatusCallback`和調用`StartAsyncDownload`以從指定的 URL 以非同步方式下載資料。

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>參數

*鉑*<br/>
[在]指向請求非同步數據傳輸的物件的指標。 物件`CBindStatusCallback`在此物件的類上被範本化。

*普豐克*<br/>
[在]指向接收讀取數據的函數的指標。 該函數是對象`T`類型 類的成員。 有關語法和範例,請參閱[StartAsync 下載](#startasyncdownload)。

*bstrURL*<br/>
[在]要從中獲取數據的 URL。 可以是任何有效的 URL 或檔名。 不能是 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnk 容器*<br/>
[在]容器`IUnknown`的 。 預設情況下為 NULL。

*b 相對*<br/>
[在]指示 URL 是相對的還是絕對的標記。 默認情況下,FALSE 表示 URL 是絕對的。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

每次數據可用時,它都會通過`OnDataAvailable`發送到物件。 `OnDataAvailable`讀取資料並調用*pFunc*指向的功能(例如,儲存數據或將其列印到螢幕)。

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBind 狀態回撥::取得綁定資訊

被叫來告訴名字物件如何綁定。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>參數

*pgrfBSCF*<br/>
[出]指向 BINDF 枚舉值的指標,指示綁定操作應如何發生。 預設情況下,使用以下枚舉值進行設定:

BINDF_ASYNCHRONOUS異步下載。

當`OnDataAvailable`數據尚未可用時BINDF_ASYNCSTORAGE返回E_PENDING,而不是在數據可用之前進行阻塞。

BINDF_GETNEWESTVERSION 綁定操作應檢索數據的最新版本。

BINDF_NOWRITECACHE 綁定操作不應將檢索到的數據存儲在磁碟緩存中。

*普賓德福*<br/>
[進出]指向結構的指標`BINDINFO`,提供有關物件希望如何進行綁定的詳細資訊。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

默認實現將綁定設置為非同步並使用資料推送模型。 在數據推送模型中,名字物件驅動非同步綁定操作,並在有新資料可用時持續通知用戶端。

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBind 狀態回撥::取得優先順序

由非同步名字物件調用,以獲得綁定操作的優先順序。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>參數

*pn優先權*<br/>
[出]**LONG**變數的位址,在成功時,接收優先順序。

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBind狀態回撥::m_dwAvailableToRead

可用於存儲可供讀取的位元組數。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>備註

初始化為零。 `StartAsyncDownload`

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBind狀態回撥::m_dwTotalRead

非同步數據傳輸中讀取的位元組的累計總數。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>備註

每次`OnDataAvailable`按實際讀取的位元組數調用增量。 初始化為零。 `StartAsyncDownload`

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBind狀態回撥::m_pFunc

讀取可用資料(`m_pFunc`例如,儲存`OnDataAvailable`資料或將其列印到螢幕上)後,將呼叫指向的函數。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>備註

指向的`m_pFunc`函數是物件類的成員,具有以下語法:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBind狀態回撥::m_pT

指向請求非同步數據傳輸的物件的指標。

```
T* m_pT;
```

### <a name="remarks"></a>備註

物件`CBindStatusCallback`在此物件的類上被範本化。

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBind狀態回撥::m_spBindCtx

指向[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)介面的指標,該介面提供對綁定上下文的訪問(存儲有關特定名字綁定操作的資訊物件)。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>備註

在`StartAsyncDownload`中 初始化。

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBind狀態回撥::m_spBinding

指向當前綁定操作`IBinding`的介面的指標。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>備註

在`OnStartBinding`中 初始`OnStopBinding`化並在 中釋放。

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBind狀態回撥::m_spMoniker

指向[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面的指標,用於 URL。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>備註

在`StartAsyncDownload`中 初始化。

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBind狀態回撥::m_spStream

指向當前綁定操作的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>備註

當 BCSF`STGMEDIUM`標誌BCSF_FIRSTDATANOTIFICATION在 BCSF 標誌BCSF_LASTDATANOTIFICATION時從`OnDataAvailable`結構中初始化 。

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBind 狀態回撥::OnData 可用

系統提供的非同步名字物件調用`OnDataAvailable`在物件可用時向物件提供資料。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>參數

*grfBSCF*<br/>
[在]BSCF 枚舉值。 以下一項或多項:BSCF_FIRSTDATANOTIFICATION、BSCF_INTERMEDIARYDATANOTIFICATION或BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
[在]自綁定開始以來可用的數據的累積量(以位元組為單位)。 可以是零,指示數據量不相關或沒有可用的特定數量。

*波波裡奇*<br/>
[在]指向包含可用資料的格式的[FORMATETC](/windows/win32/com/the-formatetc-structure)結構的指標。 如果沒有格式,可以CF_NULL。

*psgmed*<br/>
[在]指向保存當前可用實際數據的[STGMEDIUM](/windows/win32/com/the-stgmedium-structure)結構的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

`OnDataAvailable`讀取資料,然後調用物件的類的方法(例如,存儲數據或將其列印到螢幕)。 有關詳細資訊[,請參閱 CBind 狀態回撥::啟動同步下載](#startasyncdownload)。

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBind狀態回調::在低資源

在資源不足時調用。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>參數

*dw 保留*<br/>
已保留。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBind 狀態回檔:開啟物件可用

由非同步名字物件調用,將對象介面指標傳遞給應用程式。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>參數

*riid*<br/>
請求介面的介面標識碼。 未使用的。

*龐克*<br/>
I未知介面的位址。 未使用的。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBind 狀態回撥::在進度上

調用 以指示數據下載過程的進度。

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>參數

*烏爾進步*<br/>
未簽名的長整數。 未使用的。

*ulProgressMax*<br/>
未簽名的長整數未使用。

*ulStatus代碼*<br/>
未簽名的長整數。 未使用的。

*szStatusText*<br/>
字串值的位址。 未使用的。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBind 狀態回檔:打開繫結

將數據成員[m_spBinding](#m_spbinding)m_spBinding`IBinding`到*pBinding*中的指標。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>參數

*dw 保留*<br/>
保留供未來使用。

*p 繫結*<br/>
[在]當前綁定操作的 IBinding 介面的位址。 這不能為 NULL。 用戶端應在此指標上調用 AddRef,以保持對綁定物件的引用。

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBind 狀態回檔:打開繫結

釋放數據`IBinding`成員[m_spBinding](#m_spbinding)中的指標。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>參數

*h結果*<br/>
從綁定操作返回的狀態代碼。

*szError*<br/>
字串值的位址。 未使用的。

### <a name="remarks"></a>備註

由系統提供的異步名字物件調用,以指示綁定操作的結束。

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBind 狀態回撥::開始同步下載

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

*鉑*<br/>
[在]指向請求非同步數據傳輸的物件的指標。 物件`CBindStatusCallback`在此物件的類上被範本化。

*普豐克*<br/>
[在]指向接收正在讀取的數據的函數的指標。 該函數是對象`T`類型 類的成員。 有關語法和範例,請參閱**備註**。

*bstrURL*<br/>
[在]要從中獲取數據的 URL。 可以是任何有效的 URL 或檔名。 不能是 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnk 容器*<br/>
[在]容器`IUnknown`的 。 預設情況下為 NULL。

*b 相對*<br/>
[在]指示 URL 是相對的還是絕對的標記。 默認情況下,FALSE 表示 URL 是絕對的。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

每次數據可用時,它都會通過`OnDataAvailable`發送到物件。 `OnDataAvailable`讀取資料並調用*pFunc*指向的功能(例如,儲存數據或將其列印到螢幕)。

*pFunc*指向的函數是物件類的成員,具有以下語法:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

在下面的範例中(取自[ASYNC](../../overview/visual-cpp-samples.md)範例),`OnData`函數將接收到的數據寫入文本框中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
