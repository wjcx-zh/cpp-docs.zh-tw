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
ms.openlocfilehash: cd399368e46e4e9a86b4c6260e07aee07b80defb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507506"
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
|[CAsyncMonikerFile::GetBinding](#getbinding)|抓取非同步傳輸系結的指標。|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|抓取資料流程中的資料格式。|
|[CAsyncMonikerFile::Open](#open)|以非同步方式開啟檔案。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|建立可`IBindStatusCallback`執行的 COM 物件。|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|由 OLE 系統程式庫呼叫, 以要求要建立之系結類型的資訊。|
|[CAsyncMonikerFile::GetPriority](#getpriority)|由 OLE 系統程式庫呼叫以取得系結的優先順序。|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|呼叫以提供資料, 使其在非同步系結作業期間可供用戶端使用。|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|當資源不足時呼叫。|
|[CAsyncMonikerFile::OnProgress](#onprogress)|呼叫以指出資料下載進程的進度。|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|在啟動系結時呼叫。|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|停止非同步傳輸時呼叫。|

## <a name="remarks"></a>備註

衍生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md), 而後者又衍生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile`使用[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面以非同步方式存取任何資料流程, 包括以非同步方式從 URL 載入檔案。 這些檔案可以是 ActiveX 控制項的資料路徑屬性。

非同步名字標記主要是用於具備網際網路功能的應用程式和 ActiveX 控制項, 以便在檔案傳輸期間提供回應式的使用者介面。 其主要的範例是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)來提供 ActiveX 控制項的非同步屬性。 `CDataPathProperty`物件會重複取得回呼, 表示在冗長的屬性交換過程中, 新資料的可用性。

如需如何在網際網路應用程式中使用非同步名字和 ActiveX 控制項的詳細資訊, 請參閱下列文章:

- [網際網路的第一個步驟:非同步名字](../../mfc/asynchronous-monikers-on-the-internet.md)

- [網際網路的第一個步驟:ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile:: CAsyncMonikerFile

建構 `CAsyncMonikerFile` 物件。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>備註

它不會建立`IBindHost`介面。 `IBindHost`只有當您在`Open`成員函式中提供它時, 才會使用。

如需`IBindHost`介面的說明, 請參閱 Windows SDK。

##  <a name="close"></a>CAsyncMonikerFile:: Close

呼叫此函式以關閉並釋放所有資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以在未開啟或已關閉的檔案上呼叫。

##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile:: CreateBindStatusCallback

建立可`IBindStatusCallback`執行的 COM 物件。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>參數

*pUnkControlling*<br/>
控制不明 (外部`IUnknown`) 的指標, 如果未使用匯總則為 Null。

### <a name="return-value"></a>傳回值

如果*pUnkControlling*不是 Null, 此函式會將指標傳回至`IUnknown`支援`IBindStatusCallback`的新 COM 物件上的內部。 如果`pUnkControlling`為 Null, 則函式`IUnknown`會將指標傳回至支援`IBindStatusCallback`的新 COM 物件上的。

### <a name="remarks"></a>備註

`CAsyncMonikerFile`需要執行的 COM 物件`IBindStatusCallback`。 MFC 會執行這類物件, 而且它是可匯總的。 您可以覆`CreateBindStatusCallback`寫以傳回您自己的 COM 物件。 您的 com 物件可以藉由呼叫`CreateBindStatusCallback` , 並對您的 com 物件使用控制不明, 來匯總 MFC 的執行。 使用`CCmdTarget` com 支援所實作用的 com 物件可以使用`CCmdTarget::GetControllingUnknown`來抓取的控制不明。

或者, 您的 COM 物件可以藉由呼叫`CreateBindStatusCallback( NULL )`來委派給 MFC 的執行。

[CAsyncMonikerFile:: Open](#open)呼叫`CreateBindStatusCallback`。

如需非同步名字和非同步系結的詳細資訊, 請參閱[IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))介面和非同步系結[和儲存的工作方式](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)。 如需匯總的討論, 請參閱[匯總](/windows/win32/com/aggregation)。 這三個主題都在 Windows SDK 中。

##  <a name="getbindinfo"></a>CAsyncMonikerFile:: GetBindInfo

從非同步標記的用戶端呼叫, 以告知非同步標記其所要系結的方式。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>傳回值

抓取的設定`IBindStatusCallBack`。 如需`IBindStatusCallback`介面的說明, 請參閱 Windows SDK。

### <a name="remarks"></a>備註

預設的執行會將系結設定為非同步, 以使用儲存媒體 (資料流程), 並使用資料推送模型。 如果您想要變更系結的行為, 請覆寫此函式。

執行這項作業的其中一個原因是使用資料提取模型來系結, 而不是資料推送模型。 在資料提取模型中, 用戶端會驅動系結作業, 而該名字標記只會在讀取時提供資料給用戶端。 在資料推送模型中, 標記會驅動非同步系結作業, 並在有可用的新資料時持續通知用戶端。

##  <a name="getbinding"></a>CAsyncMonikerFile:: Getbindingexpression

呼叫此函式可取得非同步傳輸系結的指標。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>傳回值

非同步傳輸開始時`IBinding`所提供之介面的指標。 如果基於任何原因而無法以非同步方式進行傳送, 則會傳回 Null。

### <a name="remarks"></a>備註

這`IBinding`可讓您透過介面控制資料傳輸進程, 例如, 使用`IBinding::Abort`、 `IBinding::Pause`和`IBinding::Resume`。

如需`IBinding`介面的說明, 請參閱 Windows SDK。

##  <a name="getformatetc"></a>CAsyncMonikerFile:: GetFormatEtc

呼叫此函式可取得資料流程中資料的格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>傳回值

目前開啟的資料流程之 Windows 結構[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)的指標。 如果名字尚未系結, 則傳回 Null, 如果不是非同步, 則傳回, 如果非同步作業尚未開始, 則傳回。

##  <a name="getpriority"></a>CAsyncMonikerFile:: GetPriority

從非同步標記的用戶端呼叫, 因為系結程式會開始接收指定給系結作業之執行緒的優先順序。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>傳回值

將進行非同步傳輸的優先順序。 其中一個標準執行緒優先順序旗標:THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL 和 THREAD_PRIORITY_TIME_CRITICAL。 如需這些值的說明, 請參閱 Windows 函數[SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

### <a name="remarks"></a>備註

`GetPriority`不應直接呼叫。 預設的執行會傳回 THREAD_PRIORITY_NORMAL。

##  <a name="ondataavailable"></a>CAsyncMonikerFile:: OnDataAvailable

非同步標記會`OnDataAvailable`呼叫, 在非同步系結作業期間, 將資料提供給用戶端。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>參數

*dwSize*<br/>
自系結開始後可用的資料累計量 (以位元組為單位)。 可以是零, 表示資料量與作業無關, 或沒有可用的特定數量。

*bscfFlag*<br/>
BSCF 列舉值。 可以是下列一個或多個值:

- BSCF_FIRSTDATANOTIFICATION 識別給定系結作業`OnDataAvailable`的第一個呼叫。

- BSCF_INTERMEDIATEDATANOTIFICATION 識別系結作業的`OnDataAvailable`中繼呼叫。

- BSCF_LASTDATANOTIFICATION 識別系結作業的`OnDataAvailable`最後一個呼叫。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 請參閱下列範例以取得範例執行。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>CAsyncMonikerFile:: OnLowResource

當資源較低時, 由標記呼叫。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>備註

預設的執行會`GetBinding( )-> Abort( )`呼叫。

##  <a name="onprogress"></a>CAsyncMonikerFile:: OnProgress

由名字重複呼叫以指出此系結作業的目前進度, 通常是在冗長的作業期間合理的間隔。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>參數

*ulProgress*<br/>
指出系結作業目前的進度, 相對於*ulProgressMax*中所指出的預期最大值。

*ulProgressMax*<br/>
針對這項作業的呼叫 `OnProgress`持續時間, 指出 ulProgress 的預期最大值。

*ulStatusCode*<br/>
提供有關系結作業進度的其他資訊。 有效的值取自`BINDSTATUS`列舉。 如需可能的值, 請參閱備註。

*szStatusText*<br/>
目前進度的相關資訊, 視*ulStatusCode*的值而定。 如需可能的值, 請參閱備註。

### <a name="remarks"></a>備註

*UlStatusCode*的可能值 (以及每個值的*szStatusText* ) 為:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |系結作業會尋找保存要系結之物件或儲存體的資源。 *SzStatusText*會提供所搜尋資源的顯示名稱 (例如 "www.microsoft.com")。  |
|BINDSTATUS_CONNECTING  |系結作業會連接到保存要系結之物件或儲存體的資源。 *SzStatusText*會提供所連線之資源的顯示名稱 (例如, IP 位址)。  |
|BINDSTATUS_SENDINGREQUEST|系結作業要求將物件或儲存體系結至。 *SzStatusText*會提供物件的顯示名稱 (例如, 檔案名)。|
|BINDSTATUS_REDIRECTING  |已將系結作業重新導向至不同的資料位置。 *SzStatusText*會提供新資料位置的顯示名稱。  |
|BINDSTATUS_USINGCACHEDCOPY  |系結作業會從快取的複本抓取要求的物件或儲存體。 *SzStatusText*是 Null。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |系結作業已開始接收要系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。|
|BINDSTATUS_DOWNLOADINGDATA  |系結作業會繼續接收所系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。  |
|BINDSTATUS_ENDDOWNLOADDATA  |系結作業已完成接收要系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。  |
|BINDSTATUS_CLASSIDAVAILABLE  |要系結之物件的實例只會建立。 *SzStatusText*會以字串格式提供新物件的 CLSID, 讓用戶端有機會取消系結作業 (如有需要)。  |

##  <a name="onstartbinding"></a>CAsyncMonikerFile:: OnStartBinding

覆寫衍生類別中的這個函式, 以便在啟動系結時執行動作。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>備註

此函式是由標記傳回。 預設實作不做任何動作。

##  <a name="onstopbinding"></a>CAsyncMonikerFile:: OnStopBinding

由系結作業結尾的標記所呼叫。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>參數

*hresult*<br/>
屬於錯誤或警告值的 HRESULT。

*szErrort*<br/>
描述錯誤的字元字串。

### <a name="remarks"></a>備註

覆寫此函式, 以在傳輸停止時執行動作。 根據預設, 函式會`IBinding`發行。

如需`IBinding`介面的說明, 請參閱 Windows SDK。

##  <a name="open"></a>CAsyncMonikerFile:: Open

呼叫這個成員函式以非同步方式開啟檔案。

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
要以非同步方式開啟之檔案的指標。 檔案可以是任何有效的 URL 或檔案名。

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時, 會將其設定為原因。

*pMoniker*<br/>
非同步「名字」介面`IMoniker`的指標, 這是一種精確的標記, 它是檔本身的名字標記的組合, 您可以用`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`來抓取, 以及從路徑名稱建立的「名字」。 控制項可以使用此標記來進行系結, 但這不是控制項應儲存的標記。

*pBindHost*<br/>
`IBindHost`介面的指標, 將用來從可能的相對路徑名稱建立名字標記。 如果系結主機無效或未提供名字標記, 則呼叫會預設為`Open(lpszFileName,pError)`。 如需`IBindHost`介面的說明, 請參閱 Windows SDK。

*pServiceProvider*<br/>
`IServiceProvider`介面的指標。 如果服務提供者無效或無法提供的服務`IBindHost`, 則呼叫會預設為。 `Open(lpszFileName,pError)`

*pUnknown*<br/>
`IUnknown`介面的指標。 如果`IServiceProvider`找到, 則函數會`IBindHost`查詢。 如果服務提供者無效或無法提供的服務`IBindHost`, 則呼叫會預設為。 `Open(lpszFileName,pError)`

### <a name="return-value"></a>傳回值

如果檔案已順利開啟, 則為非零;否則為0。

### <a name="remarks"></a>備註

此呼叫會起始系結程式。

您可以使用 URL 或 filename 作為*lpszURL*參數。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\-或-

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
