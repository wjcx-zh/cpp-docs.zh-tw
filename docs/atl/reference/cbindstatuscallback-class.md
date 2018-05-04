---
title: CBindStatusCallback 類別 |Microsoft 文件
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
ms.openlocfilehash: 43a51b98710ea92f153581945007f21864dca6f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 類別
這個類別會實作 `IBindStatusCallback` 介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS |   BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx
 <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別包含會在收到資料時呼叫的函式。  
  
 *nBindFlags*  
 指定所傳回的繫結旗標[GetBindInfo](#getbindinfo)。 預設實作設定非同步繫結、 擷取資料/物件的最新版本並不會儲存在磁碟快取中擷取的資料。  
  
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
|[CBindStatusCallback::GetPriority](#getpriority)|取得繫結作業的優先順序非同步 moniker 所呼叫。 ATL 實作會傳回`E_NOTIMPL`。|  
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|呼叫資料提供給您的應用程式成為可用。 讀取資料，然後呼叫函式傳遞給它使用的資料。|  
|[CBindStatusCallback::OnLowResource](#onlowresource)|當資源不足時呼叫。 ATL 實作會傳回`S_OK`。|  
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|若要將物件的介面指標傳遞至您的應用程式的非同步 moniker 所呼叫。 ATL 實作會傳回`S_OK`。|  
|[CBindStatusCallback::OnProgress](#onprogress)|呼叫以表示資料下載程序的進度。 ATL 實作會傳回`S_OK`。|  
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|當您啟動繫結時呼叫。|  
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|停止非同步資料傳輸時呼叫。|  
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|初始化可用位元組，並為零，讀取的位元組從 URL，並呼叫建立推入型別資料流物件`OnDataAvailable`每次資料可供使用。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|可讀取的位元組數目。|  
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|讀取的位元組總數。|  
|[CBindStatusCallback::m_pFunc](#m_pfunc)|當資料可供使用時，就會呼叫函式的指標。|  
|[CBindStatusCallback::m_pT](#m_pt)|要求非同步資料傳輸物件的指標。|  
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|指標[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)介面目前的繫結作業。|  
|[CBindStatusCallback::m_spBinding](#m_spbinding)|指標`IBinding`介面目前的繫結作業。|  
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|指標[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)介面要使用的 URL。|  
|[CBindStatusCallback::m_spStream](#m_spstream)|指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)資料傳輸的介面。|  
  
## <a name="remarks"></a>備註  
 `CBindStatusCallback` 類別會實作 `IBindStatusCallback` 介面。 `IBindStatusCallback` 必須實作您的應用程式讓它可以從非同步資料傳輸接收通知。 使用系統提供的非同步 moniker`IBindStatusCallback`方法來傳送和接收資訊的非同步資料傳輸，與您的物件。  
  
 一般而言，`CBindStatusCallback`物件都與特定的繫結作業。 例如，在[非同步](../../visual-cpp-samples.md)範例中，當您設定的 URL 屬性，它會建立`CBindStatusCallback`物件在呼叫`Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]  
  
 非同步 moniker 會使用回呼函式`OnData`資料時，呼叫您的應用程式。 非同步 moniker 是由系統提供的。  
  
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
 建立要接收通知有關非同步資料傳輸的物件。 一般而言，每個繫結作業會建立一個物件。  
  
 建構函式也會初始化[m_pT](#m_pt)和[m_pFunc](#m_pfunc)至**NULL**。  
  
##  <a name="dtor"></a>  CBindStatusCallback:: ~ CBindStatusCallback  
 解構函式。  
  
```
~CBindStatusCallback();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="download"></a>  CBindStatusCallback::Download  
 建立`CBindStatusCallback`物件並呼叫`StartAsyncDownload`開始以非同步方式從指定的 URL 下載資料。  
  
```
static HRESULT Download(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 [in]要求非同步資料傳輸物件的指標。 `CBindStatusCallback`物件根據此物件的類別。  
  
 *pFunc*  
 [in]接收資料所讀取的函式的指標。 此函式所屬物件的類別類型的`T`。 請參閱[StartAsyncDownload](#startasyncdownload)的語法和範例。  
  
 `bstrURL`  
 [in]資料取得 URL。 可以是任何有效的 URL 或檔案名稱。 不能**NULL**。 例如:   
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in]**IUnknown**的容器。 **NULL**預設。  
  
 `bRelative`  
 [in]表示 URL 相對的還是絕對的旗標。 **FALSE**根據預設，這表示 URL 為絕對。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 每次資料可傳送至物件，可透過`OnDataAvailable`。 `OnDataAvailable` 讀取資料，並呼叫函式所指*pFunc* （例如，若要將資料儲存或列印至螢幕）。  
  
##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo  
 呼叫以告知如何將繫結 moniker。  
  
```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```  
  
### <a name="parameters"></a>參數  
 *pgrfBSCF*  
 [out]指標**BINDF**列舉值，指出如何繫結作業應該發生。 根據預設，設定下列的列舉值：  
  
 **BINDF_ASYNCHRONOUS**非同步下載。  
  
 **BINDF_ASYNCSTORAGE** `OnDataAvailable`傳回**E_PENDING**當資料尚未可用，而不是封鎖，直到資料可供使用。  
  
 **BINDF_GETNEWESTVERSION**繫結作業應該擷取資料的最新版本。  
  
 **BINDF_NOWRITECACHE**繫結作業不應該將擷取的資料存放在磁碟快取。  
  
 *pbindinfo*  
 [in、 out]指標**BINDINFO**結構中，提供物件如何想進行的繫結的詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 預設實作會設定繫結是非同步的並且將資料推入模式。 在資料推入模型中，moniker 可促進非同步繫結作業以及持續在新的資料可用時通知用戶端。  
  
##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority  
 取得繫結作業的優先順序非同步 moniker 所呼叫。  
  
```
STDMETHOD(GetPriority)(LONG* pnPriority);
```  
  
### <a name="parameters"></a>參數  
 *pnPriority*  
 [out]位址**長**的成功時，會收到優先順序的變數。  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
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
 每次遞增`OnDataAvailable`稱為實際讀取的位元組數目。 初始化為零`StartAsyncDownload`。  
  
##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc  
 函式所指`m_pFunc`稱為`OnDataAvailable`讀取可用的資料 （例如，若要將資料儲存或列印至螢幕） 之後。  
  
```
ATL_PDATAAVAILABLE m_pFunc;
```  
  
### <a name="remarks"></a>備註  
 此函式所指`m_pFunc`是您的物件類別的成員，而且具有下列語法：  
  
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
 `CBindStatusCallback`物件根據此物件的類別。  
  
##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx  
 指標[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)介面，提供的繫結內容 （儲存在特定的 moniker 繫結作業的相關資訊的物件） 的存取。  
  
```
CComPtr<IBindCtx> m_spBindCtx;
```  
  
### <a name="remarks"></a>備註  
 在初始化`StartAsyncDownload`。  
  
##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding  
 指標`IBinding`介面目前的繫結作業。  
  
```
CComPtr<IBinding> m_spBinding;
```  
  
### <a name="remarks"></a>備註  
 在初始化`OnStartBinding`和發行的`OnStopBinding`。  
  
##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker  
 指標[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)介面要使用的 URL。  
  
```
CComPtr<IMoniker> m_spMoniker;
```  
  
### <a name="remarks"></a>備註  
 在初始化`StartAsyncDownload`。  
  
##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream  
 指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)介面目前的繫結作業。  
  
```
CComPtr<IStream> m_spStream;
```  
  
### <a name="remarks"></a>備註  
 在初始化`OnDataAvailable`從**STGMEDIUM**結構時**BCSF**旗標是**BCSF_FIRSTDATANOTIFICATION**和時釋放**BCSF**旗標是**BCSF_LASTDATANOTIFICATION**。  
  
##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable  
 系統提供的非同步 moniker 呼叫`OnDataAvailable`可用時，提供資料給物件。  
  
```
STDMETHOD(  
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```  
  
### <a name="parameters"></a>參數  
 *grfBSCF*  
 [in]A **BSCF**列舉值。 一或多個項目： **BSCF_FIRSTDATANOTIFICATION**， **BSCF_INTERMEDIARYDATANOTIFICATION**，或**BSCF_LASTDATANOTIFICATION**。  
  
 `dwSize`  
 [in]累積數量 （以位元組為單位） 的繫結起可用的資料。 可以是零，表示不相關的資料量，或沒有特定的數量變得可用。  
  
 *pformatetc*  
 [in]指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682242)結構，其中包含可用的資料格式。 如果沒有任何格式，可以是**CF_NULL**。  
  
 *pstgmed*  
 [in]指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms695269)結構，可保存目前可用的實際資料。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 `OnDataAvailable` 讀取資料，則會呼叫物件的類別 （例如，若要將資料儲存或列印至螢幕） 的方法。 請參閱[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)如需詳細資訊。  
  
##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource  
 當資源不足時呼叫。  
  
```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```  
  
### <a name="parameters"></a>參數  
 `dwReserved`  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable  
 若要將物件的介面指標傳遞至您的應用程式的非同步 moniker 所呼叫。  
  
```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```  
  
### <a name="parameters"></a>參數  
 `riid`  
 所要求介面的介面識別項。 未使用。  
  
 `punk`  
 IUnknown 介面位址。 未使用。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
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
 `ulProgress`  
 不帶正負號的長整數。 未使用。  
  
 `ulProgressMax`  
 不帶正負號的長整數未使用。  
  
 `ulStatusCode`  
 不帶正負號的長整數。 未使用。  
  
 `szStatusText`  
 字串值的位址。 未使用。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding  
 設定資料成員[m_spBinding](#m_spbinding)至`IBinding`中的指標`pBinding`。  
  
```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```  
  
### <a name="parameters"></a>參數  
 `dwReserved`  
 保留供未來使用。  
  
 `pBinding`  
 [in]目前的 IBinding 介面位址繫結作業。 這不能是 NULL。 用戶端應該將繫結物件的參考保留此指標上呼叫 AddRef。  
  
##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding  
 版本`IBinding`中的資料成員的指標[m_spBinding](#m_spbinding)。  
  
```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```  
  
### <a name="parameters"></a>參數  
 `hresult`  
 從繫結作業傳回狀態碼。  
  
 szStatusText  
 字串值未使用的位址。  
  
### <a name="remarks"></a>備註  
 表示繫結作業結束，系統提供的非同步 moniker 呼叫。  
  
##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload  
 從指定的 URL 以非同步方式下載資料開始。  
  
```
HRESULT StartAsyncDownload(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 [in]要求非同步資料傳輸物件的指標。 `CBindStatusCallback`物件根據此物件的類別。  
  
 *pFunc*  
 [in]接收資料被讀取函式的指標。 此函式所屬物件的類別類型的`T`。 請參閱**備註**的語法和範例。  
  
 `bstrURL`  
 [in]資料取得 URL。 可以是任何有效的 URL 或檔案名稱。 不能**NULL**。 例如:   
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in]**IUnknown**的容器。 **NULL**預設。  
  
 `bRelative`  
 [in]表示 URL 相對的還是絕對的旗標。 **FALSE**根據預設，這表示 URL 為絕對。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 每次資料可傳送至物件，可透過`OnDataAvailable`。 `OnDataAvailable` 讀取資料，並呼叫函式所指*pFunc* （例如，若要將資料儲存或列印至螢幕）。  
  
 此函式所指*pFunc*是您的物件類別的成員，而且具有下列語法：  
  
 `void Function_Name(`  
  
 `CBindStatusCallback<T>*` `pbsc` `,`  
  
 `BYTE*` `pBytes` `,`  
  
 `DWORD` `dwSize`  
  
 `);`  
  
 在下列範例 (取自[非同步](../../visual-cpp-samples.md)範例)，函式`OnData`將接收的資料寫入至文字方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
