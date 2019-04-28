---
title: CAsyncMonikerFile 類別
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: b86cba0c2e8f7991902a552d404355d6c1474138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237853"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile 類別

提供可在 ActiveX 控制項 (先前稱為 OLE 控制項) 中使用非同步 Moniker 的功能。

## <a name="syntax"></a>語法

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|建構 `CAsyncMonikerFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|關閉並釋放所有資源。|
|[CAsyncMonikerFile::GetBinding](#getbinding)|擷取繫結的非同步傳輸的指標。|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|擷取資料流中的資料的格式。|
|[CAsyncMonikerFile::Open](#open)|以非同步方式開啟檔案。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|建立 COM 物件實作`IBindStatusCallback`。|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|呼叫 OLE 系統程式庫上建立的繫結類型的要求資訊。|
|[CAsyncMonikerFile::GetPriority](#getpriority)|呼叫 OLE 系統程式庫，來取得繫結的優先權。|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|呼叫以提供可用來在用戶端非同步繫結作業期間的資料。|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|當資源過低時呼叫。|
|[CAsyncMonikerFile::OnProgress](#onprogress)|呼叫以表示資料下載程序的進度。|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|當繫結啟動時呼叫。|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|當非同步傳輸已停止時呼叫。|

## <a name="remarks"></a>備註

衍生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，而後者又衍生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`會使用[IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)介面，以存取任何資料流以非同步的方式，包括從 URL 非同步載入檔案。 這些檔案可以 ActiveX 控制項的資料路徑屬性。

非同步 moniker 可啟用網際網路的應用程式和 ActiveX 控制項中的主要檔案傳輸期間提供回應的使用者介面。 主要範例是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)為 ActiveX 控制項提供非同步屬性。 `CDataPathProperty`物件會重複收到的回呼，長時間的屬性交換過程中表示的新資料的可用性。

如需如何在網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列文章：

- [網際網路的第一個步驟：非同步 Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

- [網際網路的第一個步驟：ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

建構 `CAsyncMonikerFile` 物件。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>備註

它不會建立`IBindHost`介面。 `IBindHost` 只有當您在提供時，才會使用`Open`成員函式。

如需描述`IBindHost`介面中，請參閱 Windows SDK。

##  <a name="close"></a>  CAsyncMonikerFile::Close

呼叫此函式來關閉並釋放所有資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以呼叫未開啟或已關閉檔案。

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

建立 COM 物件實作`IBindStatusCallback`。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>參數

*pUnkControlling*<br/>
控制未知的指標 (外部`IUnknown`) 或如果未使用彙總，則為 NULL。

### <a name="return-value"></a>傳回值

如果*pUnkControlling*不是 NULL，函式會傳回內部指標`IUnknown`在新的 COM 物件支援`IBindStatusCallback`。 如果`pUnkControlling`為 NULL，則函數會傳回的指標`IUnknown`在新的 COM 物件支援`IBindStatusCallback`。

### <a name="remarks"></a>備註

`CAsyncMonikerFile` 需要實作的 COM 物件`IBindStatusCallback`。 MFC 實作這類物件，而且彙總。 您可以覆寫`CreateBindStatusCallback`傳回您自己的 COM 物件。 您的 COM 物件可以藉由呼叫項目彙總 MFC 實作`CreateBindStatusCallback`與 COM 物件的控制未知。 使用實作的 COM 物件`CCmdTarget`COM 支援可以擷取控制未知使用`CCmdTarget::GetControllingUnknown`。

或者，您的 COM 物件可以委派給 MFC 實作藉由呼叫`CreateBindStatusCallback( NULL )`。

[CAsyncMonikerFile::Open](#open)呼叫`CreateBindStatusCallback`。

如需有關非同步 moniker 和非同步繫結的詳細資訊，請參閱 < [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))介面並[如何在非同步繫結和儲存體工作](/windows/desktop/Stg/how-asynchronous-binding-and-storage-work)。 如需彙總的討論，請參閱 <<c0> [ 彙總](/windows/desktop/com/aggregation)。 所有的三個主題都在 Windows SDK 中。

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

從用戶端的非同步 moniker，告訴它要繫結的方式的非同步 moniker 呼叫。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>傳回值

擷取的設定`IBindStatusCallBack`。 如需描述`IBindStatusCallback`介面中，請參閱 Windows SDK。

### <a name="remarks"></a>備註

預設實作會設定為非同步，若要使用儲存媒體 （串流），並將資料推送模型繫結。 如果您想要變更繫結的行為，請覆寫這個函式。

執行此動作的其中一個原因是使用資料提取模型，而不資料推送模型繫結。 在資料提取模型，用戶端磁碟機繫結作業，和 moniker 只提供資料給用戶端會在讀取。 在資料推入模型中，moniker 驅動非同步繫結作業，並持續在每當有新資料可用時通知用戶端。

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

呼叫此函式可擷取非同步傳輸繫結的指標。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>傳回值

指標`IBinding`非同步傳輸開始時所提供的介面。 傳回 NULL，如果基於任何原因傳輸無法在以非同步方式進行。

### <a name="remarks"></a>備註

這可讓您控制的資料傳輸程序，透過`IBinding`介面，例如，使用`IBinding::Abort`， `IBinding::Pause`，和`IBinding::Resume`。

如需描述`IBinding`介面中，請參閱 Windows SDK。

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

呼叫此函式可擷取的資料流中的資料格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>傳回值

Windows 結構的指標[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)目前開啟的資料流。 如果 moniker 未繫結，如果不是非同步的或尚未開始執行非同步作業，則傳回 NULL。

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

呼叫從用戶端的非同步 moniker 繫結程序開始時接收到執行緒給繫結作業的優先順序。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>傳回值

優先權處非同步傳輸，就會進行。 其中一個標準的執行緒優先順序旗標：THREAD_PRIORITY_ABOVE_NORMAL、 THREAD_PRIORITY_BELOW_NORMAL、 THREAD_PRIORITY_HIGHEST、 THREAD_PRIORITY_IDLE、 THREAD_PRIORITY_LOWEST、 THREAD_PRIORITY_NORMAL 和 THREAD_PRIORITY_TIME_CRITICAL。 請參閱 Windows 函式[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)如需這些值的描述。

### <a name="remarks"></a>備註

`GetPriority` 應該不會直接呼叫。 預設實作會傳回 THREAD_PRIORITY_NORMAL。

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

非同步 moniker 呼叫`OnDataAvailable`提供資料給用戶端上，可供使用，在非同步繫結作業。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>參數

*dwSize*<br/>
（以位元組為單位） 的繫結開始之後，您可以使用資料的累積數量。 可以是零，表示的資料量不相關的作業，或特定數量變成可用。

*bscfFlag*<br/>
BSCF 列舉值。 可以是下列一或多個下列值：

- BSCF_FIRSTDATANOTIFICATION 識別的第一個呼叫`OnDataAvailable`指定繫結作業。

- BSCF_INTERMEDIATEDATANOTIFICATION 識別的中間呼叫`OnDataAvailable`繫結作業。

- BSCF_LASTDATANOTIFICATION 識別上次呼叫`OnDataAvailable`繫結作業。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 請參閱以下範例的範例實作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

當資源不足時呼叫的 moniker。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>備註

預設實作會呼叫`GetBinding( )-> Abort( )`。

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

呼叫重複，以指出此繫結作業中，通常會在合理的時間間隔，在長時間作業期間的目前進度的 moniker。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>參數

*ulProgress*<br/>
指出目前相對於所示的預期最大值的繫結作業的進度*ulProgressMax*。

*ulProgressMax*<br/>
表示預期的最大值的*ulProgress*的呼叫期間`OnProgress`這項作業。

*ulStatusCode*<br/>
提供繫結作業的進度相關的其他的資訊。 有效的值取自`BINDSTATUS`列舉型別。 如需可能值，請參閱 < 備註 >。

*szStatusText*<br/>
目前的進度，根據的值的相關資訊*ulStatusCode*。 如需可能值，請參閱 < 備註 >。

### <a name="remarks"></a>備註

可能值為*ulStatusCode* (並*szStatusText*每個值) 是：

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |繫結作業尋找保存物件或繫結至的儲存體資源。 *SzStatusText*提供所搜尋之資源的顯示名稱 (例如，"www.microsoft.com")。  |
|BINDSTATUS_CONNECTING  |繫結作業已連線至資源所在的物件或繫結至的儲存體。 *SzStatusText*提供 （例如，IP 位址） 連線至資源的顯示名稱。  |
|BINDSTATUS_SENDINGREQUEST|繫結作業要求的物件或繫結至的儲存體。 *SzStatusText*提供物件 （例如，檔案名稱） 的顯示名稱。|
|BINDSTATUS_REDIRECTING  |繫結作業已重新導向不同的資料位置。 *SzStatusText*提供新的資料位置的顯示名稱。  |
|BINDSTATUS_USINGCACHEDCOPY  |繫結作業會從快取複本擷取要求的物件或儲存體。 *SzStatusText*是 NULL。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |繫結作業已開始接收的物件或繫結至的儲存體。 *SzStatusText*提供的資料位置的顯示名稱。|
|BINDSTATUS_DOWNLOADINGDATA  |繫結作業會繼續接收的物件或繫結至的儲存體。 *SzStatusText*提供的資料位置的顯示名稱。  |
|BINDSTATUS_ENDDOWNLOADDATA  |繫結作業已完成接收的物件或繫結至的儲存體。 *SzStatusText*提供的資料位置的顯示名稱。  |
|BINDSTATUS_CLASSIDAVAILABLE  |繫結至物件的執行個體只是要建立的。 *SzStatusText*提供讓用戶端有機會取消繫結作業中，視字串格式的新物件的 CLSID。  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

覆寫您繫結啟動時執行動作的衍生類別中此函式。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>備註

此函式會呼叫回 moniker。 預設實作不做任何動作。

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

呼叫繫結作業結尾的 moniker。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>參數

*hresult*<br/>
HRESULT 的錯誤或警告值。

*szErrort*<br/>
字元字串，描述錯誤。

### <a name="remarks"></a>備註

覆寫這個函式來執行動作時停止傳輸。 根據預設，函式會釋放`IBinding`。

如需描述`IBinding`介面中，請參閱 Windows SDK。

##  <a name="open"></a>  CAsyncMonikerFile::Open

呼叫此成員函式，以非同步方式開啟檔案。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
若要以非同步方式開啟的檔案指標。 檔案可以是任何有效的 URL 或檔案名稱。

*pError*<br/>
檔案例外狀況指標。 發生錯誤時，它會設定為原因。

*pMoniker*<br/>
非同步 moniker 介面的指標`IMoniker`，文件自己的 moniker 時，您可以使用擷取的組合精確 moniker `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`，並建立從路徑名稱的 moniker。 控制項可以使用這個 moniker 繫結，但這不是控制項應該儲存的 moniker。

*pBindHost*<br/>
指標`IBindHost`將用於從可能的相對路徑名稱建立 moniker 的介面。 如果繫結主機無效或未提供的 moniker，呼叫就會預設為`Open(lpszFileName,pError)`。 如需描述`IBindHost`介面中，請參閱 Windows SDK。

*pServiceProvider*<br/>
指標`IServiceProvider`介面。 如果服務提供者無效或無法提供的服務`IBindHost`，呼叫會預設為`Open(lpszFileName,pError)`。

*pUnknown*<br/>
指標`IUnknown`介面。 如果`IServiceProvider`找到，則此函式中的查詢`IBindHost`。 如果服務提供者無效或無法提供的服務`IBindHost`，呼叫會預設為`Open(lpszFileName,pError)`。

### <a name="return-value"></a>傳回值

如果順利開啟檔案，非零值。否則為 0。

### <a name="remarks"></a>備註

這個呼叫初始化繫結程序。

您可以使用 URL 或檔名*lpszURL*參數。 例如: 

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\-或-

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
