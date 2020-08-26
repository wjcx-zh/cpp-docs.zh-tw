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
ms.openlocfilehash: 259d31b9c1e198b326ba616481dbbf5315225546
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845935"
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
|[CAsyncMonikerFile：： CAsyncMonikerFile](#casyncmonikerfile)|建構 `CAsyncMonikerFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMonikerFile：： Close](#close)|關閉並釋放所有資源。|
|[CAsyncMonikerFile：： Getbindingexpression](#getbinding)|捕獲非同步傳送系結的指標。|
|[CAsyncMonikerFile：： GetFormatEtc](#getformatetc)|捕獲資料流程中資料的格式。|
|[CAsyncMonikerFile：： Open](#open)|以非同步方式開啟檔案。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMonikerFile：： CreateBindStatusCallback](#createbindstatuscallback)|建立可執行檔 COM 物件 `IBindStatusCallback` 。|
|[CAsyncMonikerFile：： GetBindInfo](#getbindinfo)|由 OLE 系統程式庫呼叫，以要求要建立之系結類型的資訊。|
|[CAsyncMonikerFile：： GetPriority](#getpriority)|由 OLE 系統程式庫呼叫以取得系結的優先權。|
|[CAsyncMonikerFile：： OnDataAvailable](#ondataavailable)|在非同步系結作業期間，呼叫以提供可供用戶端使用的資料。|
|[CAsyncMonikerFile：： OnLowResource](#onlowresource)|資源不足時呼叫。|
|[CAsyncMonikerFile：： OnProgress](#onprogress)|呼叫以表示資料下載進程的進度。|
|[CAsyncMonikerFile：： OnStartBinding](#onstartbinding)|在啟動系結時呼叫。|
|[CAsyncMonikerFile：： OnStopBinding](#onstopbinding)|在停止非同步傳送時呼叫。|

## <a name="remarks"></a>備註

衍生自 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，後者又衍生自 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)，會 `CAsyncMonikerFile` 使用 [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 介面以非同步方式存取任何資料流程，包括從 URL 以非同步方式載入檔案。 檔案可以是 ActiveX 控制項的資料路徑屬性。

非同步標記主要用於具備網際網路功能的應用程式和 ActiveX 控制項，可在檔案傳輸期間提供回應式的使用者介面。 這是使用 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) 來提供 ActiveX 控制項的非同步屬性的一個主要範例。 `CDataPathProperty`物件會重複取得回呼，以指出在冗長的屬性交換程式期間，新資料的可用性。

如需如何在網際網路應用程式中使用非同步名字和 ActiveX 控制項的詳細資訊，請參閱下列文章：

- [網際網路第一個步驟：非同步名字](../../mfc/asynchronous-monikers-on-the-internet.md)

- [網際網路第一個步驟： ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>規格需求

**標頭：** afxole。h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a> CAsyncMonikerFile：： CAsyncMonikerFile

建構 `CAsyncMonikerFile` 物件。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>備註

它不會建立 `IBindHost` 介面。 `IBindHost` 只有在成員函式中提供時，才會使用 `Open` 。

如需介面的描述 `IBindHost` ，請參閱 Windows SDK。

## <a name="casyncmonikerfileclose"></a><a name="close"></a> CAsyncMonikerFile：： Close

呼叫此函式可關閉並釋放所有資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以在未開啟或已關閉的檔案上呼叫。

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a> CAsyncMonikerFile：： CreateBindStatusCallback

建立可執行檔 COM 物件 `IBindStatusCallback` 。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>參數

*pUnkControlling*<br/>
控制外部) 之未知 (的指標， `IUnknown` 如果未使用匯總，則為 Null。

### <a name="return-value"></a>傳回值

如果 *pUnkControlling* 不是 Null，則函式會 `IUnknown` 在支援的新 COM 物件上傳回內部指標 `IBindStatusCallback` 。 如果 `pUnkControlling` 是 Null，則函式會 `IUnknown` 在支援的新 COM 物件上傳回的指標 `IBindStatusCallback` 。

### <a name="remarks"></a>備註

`CAsyncMonikerFile` 需要執行的 COM 物件 `IBindStatusCallback` 。 MFC 會執行這類物件，而且它是可匯總的。 您可以覆寫 `CreateBindStatusCallback` 以傳回您自己的 COM 物件。 您的 COM 物件可以藉由呼叫來 `CreateBindStatusCallback` 控制 com 物件的未知，來匯總 MFC 的實作為。 使用 com 支援所執行 `CCmdTarget` 的 com 物件，可以使用來取得控制未知 `CCmdTarget::GetControllingUnknown` 。

或者，您的 COM 物件可以藉由呼叫來委派至 MFC 的實作為 `CreateBindStatusCallback( NULL )` 。

[CAsyncMonikerFile：： Open](#open) 呼叫 `CreateBindStatusCallback` 。

如需非同步標記和非同步綁定的詳細資訊，請參閱 [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) 介面，以及非同步系結 [和儲存的運作方式](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)。 如需匯總的討論，請參閱 [匯總](/windows/win32/com/aggregation)。 這三個主題都在 Windows SDK 中。

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a> CAsyncMonikerFile：： GetBindInfo

從非同步標記的用戶端呼叫，以告知非同步名字標記其要系結的方式。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>傳回值

抓取的設定 `IBindStatusCallBack` 。 如需介面的描述 `IBindStatusCallback` ，請參閱 Windows SDK。

### <a name="remarks"></a>備註

預設的執行會將系結設定為非同步、使用儲存媒體 (資料流程) ，以及使用資料推送模型。 如果您想要變更系結的行為，請覆寫此函數。

這樣做的其中一個原因是使用資料提取模型來系結，而不是使用資料推送模型。 在資料提取模型中，用戶端會驅動系結作業，而且標記只會在讀取時提供資料給用戶端。 在資料推送模型中，此標記會驅動非同步系結作業，並在每次有新資料可用時持續通知用戶端。

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a> CAsyncMonikerFile：： Getbindingexpression

呼叫此函式可取得非同步傳送系結的指標。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>傳回值

`IBinding`非同步傳送開始時提供的介面指標。 如果基於任何原因而無法以非同步方式進行傳送，則傳回 Null。

### <a name="remarks"></a>備註

這可讓您透過介面控制資料傳輸 `IBinding` 程式，例如，使用 `IBinding::Abort` 、 `IBinding::Pause` 和 `IBinding::Resume` 。

如需介面的描述 `IBinding` ，請參閱 Windows SDK。

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a> CAsyncMonikerFile：： GetFormatEtc

呼叫此函式可取得資料流程中的資料格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>傳回值

目前開啟之資料流程的 Windows 結構 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 指標。 如果不是已系結的標記（如果它不是非同步）或非同步作業尚未開始，則傳回 Null。

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a> CAsyncMonikerFile：： GetPriority

從非同步標記的用戶端呼叫，因為系結程式會開始接收系結作業之執行緒的優先權。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>傳回值

進行非同步傳送的優先順序。 其中一個標準執行緒優先權旗標： THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL 和 THREAD_PRIORITY_TIME_CRITICAL。 如需這些值的描述，請參閱 Windows 函數 [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

### <a name="remarks"></a>備註

`GetPriority` 不應該直接呼叫。 預設的執行會傳回 THREAD_PRIORITY_NORMAL。

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a> CAsyncMonikerFile：： OnDataAvailable

非同步標記呼叫 `OnDataAvailable` ，可在非同步系結作業期間，將資料提供給用戶端使用。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>參數

*dwSize*<br/>
自系結開始之後可用的資料)  (位元組累計量。 可以是零，表示資料量與作業無關，或沒有任何特定數量可供使用。

*bscfFlag*<br/>
BSCF 列舉值。 可以是下列其中一個或多個值：

- BSCF_FIRSTDATANOTIFICATION 會識別給定系結作業的第一個呼叫 `OnDataAvailable` 。

- BSCF_INTERMEDIATEDATANOTIFICATION 識別系結作業的中繼呼叫 `OnDataAvailable` 。

- BSCF_LASTDATANOTIFICATION 識別系結作業的最後一次呼叫 `OnDataAvailable` 。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 請參閱下列範例以取得範例執行。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a> CAsyncMonikerFile：： OnLowResource

當資源不足時由標記呼叫。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>備註

預設的執行呼叫 `GetBinding( )-> Abort( )` 。

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a> CAsyncMonikerFile：： OnProgress

重複呼叫標記以表示此系結作業目前的進度，通常在冗長的作業期間以合理的間隔進行。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>參數

*ulProgress*<br/>
指出系結作業目前的進度，相對於 *ulProgressMax*中指出的預期最大值。

*ulProgressMax*<br/>
指出此作業的呼叫持續時間內 *ulProgress* 的預期最大值 `OnProgress` 。

*ulStatusCode*<br/>
提供系結作業進度的其他相關資訊。 有效的值取自 `BINDSTATUS` 列舉。 如需可能的值，請參閱備註。

*szStatusText*<br/>
目前進度的相關資訊，視 *ulStatusCode*的值而定。 如需可能的值，請參閱備註。

### <a name="remarks"></a>備註

*UlStatusCode* (的可能值，以及每個值) 的*szStatusText*為：

| 值 | 描述 |
|--|--|
| BINDSTATUS_FINDINGRESOURCE | 系結作業會尋找保存要系結之物件或儲存體的資源。 *SzStatusText*會提供所搜尋之資源的顯示名稱 (例如 "www.microsoft.com" ) 。 |
| BINDSTATUS_CONNECTING | 系結作業正在連接到保存要系結之物件或儲存體的資源。 *SzStatusText*會提供連線到 (之資源的顯示名稱，例如 IP 位址) 。 |
| BINDSTATUS_SENDINGREQUEST | 系結作業正在要求系結至的物件或儲存體。 *SzStatusText*會提供物件的顯示名稱 (例如，) 的檔案名。 |
| BINDSTATUS_REDIRECTING | 系結作業已重新導向至不同的資料位置。 *SzStatusText*會提供新資料位置的顯示名稱。 |
| BINDSTATUS_USINGCACHEDCOPY | 系結作業正在從快取的複本中抓取要求的物件或儲存體。 *SzStatusText*為 Null。 |
| BINDSTATUS_BEGINDOWNLOADDATA | 系結作業已開始接收要系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。 |
| BINDSTATUS_DOWNLOADINGDATA | 系結作業會繼續接收要系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。 |
| BINDSTATUS_ENDDOWNLOADDATA | 系結作業已完成接收要系結的物件或儲存體。 *SzStatusText*會提供資料位置的顯示名稱。 |
| BINDSTATUS_CLASSIDAVAILABLE | 即將系結之物件的實例即將建立。 *SzStatusText*會以字串格式提供新物件的 CLSID，讓用戶端有機會取消系結作業（如有需要）。 |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a> CAsyncMonikerFile：： OnStartBinding

覆寫衍生類別中的這個函式，以在啟動系結時執行動作。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>備註

這個函式會由標記回呼。 預設實作不做任何動作。

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a> CAsyncMonikerFile：： OnStopBinding

在系結作業結束時由標記呼叫。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>參數

*hresult*<br/>
HRESULT，它是錯誤或警告值。

*szErrort*<br/>
描述錯誤的字元字串。

### <a name="remarks"></a>備註

覆寫此函數，以在停止傳輸時執行動作。 根據預設，函式會釋放 `IBinding` 。

如需介面的描述 `IBinding` ，請參閱 Windows SDK。

## <a name="casyncmonikerfileopen"></a><a name="open"></a> CAsyncMonikerFile：： Open

呼叫這個成員函式，以非同步方式開啟檔案。

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
要以非同步方式開啟的檔案指標。 檔案可以是任何有效的 URL 或檔案名。

*pError*<br/>
檔案例外狀況的指標。 如果發生錯誤，則會將它設定為原因。

*pMoniker*<br/>
非同步標記介面指標 `IMoniker` ，這是一個精確的標記，它是檔本身的名字標記的組合，您可以用它來抓取 `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)` ，並從路徑名稱建立一個標記。 控制項可以使用這個標記來系結，但是這不是控制項應該儲存的標記。

*pBindHost*<br/>
`IBindHost`介面的指標，該介面將用來從可能的相對路徑名稱建立標記。 如果系結主機無效或未提供標記，則呼叫會預設為 `Open(lpszFileName,pError)` 。 如需介面的描述 `IBindHost` ，請參閱 Windows SDK。

*pServiceProvider*<br/>
Unmanaged 物件的 `IServiceProvider` 介面，擲回具有特定失敗 HRESULT 的例外狀況。 如果服務提供者無效或無法提供的服務 `IBindHost` ，則呼叫會預設為 `Open(lpszFileName,pError)` 。

*pUnknown*<br/>
Unmanaged 物件的 `IUnknown` 介面，擲回具有特定失敗 HRESULT 的例外狀況。 如果 `IServiceProvider` 找到，則函數會查詢 `IBindHost` 。 如果服務提供者無效或無法提供的服務 `IBindHost` ，則呼叫會預設為 `Open(lpszFileName,pError)` 。

### <a name="return-value"></a>傳回值

如果成功開啟檔案，則為非零;否則為0。

### <a name="remarks"></a>備註

此呼叫會起始系結程式。

您可以使用 URL 或檔案名作為 *lpszURL* 參數。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
