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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377000"
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
|[CAsyncMoniker 檔案:CAsyncMoniker 檔案](#casyncmonikerfile)|建構 `CAsyncMonikerFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMoniker 檔案:關閉](#close)|關閉並釋放所有資源。|
|[CAsyncMoniker 檔案:取得繫結](#getbinding)|檢索指向異步傳輸綁定的指標。|
|[CAsyncMonker 檔::取得格式](#getformatetc)|檢索流中資料的格式。|
|[CAsyncMoniker 檔::開啟](#open)|非同步打開檔。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncMoniker 檔案::建立繫結狀態回檔](#createbindstatuscallback)|創建實現`IBindStatusCallback`的 COM 物件。|
|[CAsyncMoniker 檔::取得賓德資訊](#getbindinfo)|由 OLE 系統庫調用,以請求有關要創建的綁定類型的資訊。|
|[CAsyncMoniker 檔案:取得優先權](#getpriority)|由 OLE 系統庫調用,以獲得綁定的優先順序。|
|[CAsyncMoniker 檔案::OnData可用](#ondataavailable)|調用以在非同步綁定操作期間向用戶端提供數據。|
|[CAsyncMonker 檔::在洛資源](#onlowresource)|在資源不足時調用。|
|[CAsyncMoniker 檔案::在進度上](#onprogress)|已調用以指示數據下載過程的進度。|
|[CAsyncMonker 檔案::開始繫結](#onstartbinding)|啟動綁定時調用。|
|[CAsyncMonker 檔案::開啟繫結](#onstopbinding)|在異步傳輸停止時調用。|

## <a name="remarks"></a>備註

從[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)派生,而[COleStreamFile](../../mfc/reference/colestreamfile-class.md)則`CAsyncMonikerFile`使用[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)介面非同步存取任何資料串流,包括從網址 以非同步方式載入檔。 這些檔可以是 ActiveX 控制件的資料路徑屬性。

非同步名稱器主要用於支援 Internet 的應用程式和 ActiveX 控制件,以在檔案傳輸期間提供回應式使用者介面。 這方面的一個主要範例是使用[CDataPath 屬性](../../mfc/reference/cdatapathproperty-class.md)為 ActiveX 控制項提供非同步屬性。 對`CDataPathProperty`象 將反覆收到回調,以指示在冗長的屬換過程中新數據的可用性。

有關如何在 Internet 應用程式中使用非同步名字器和 ActiveX 控制件的詳細資訊,請參閱以下文章:

- [互聯網第一步:異步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

- [互聯網第一步:主動X控制](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream 檔案](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMoniker 檔案:CAsyncMoniker 檔案

建構 `CAsyncMonikerFile` 物件。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>備註

它不創建`IBindHost`介面。 `IBindHost`僅當在`Open`成員函數中提供時才使用。

有關介面的說明,`IBindHost`請參閱 Windows SDK。

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMoniker 檔案:關閉

調用此函數以關閉和釋放所有資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以呼叫未打開或已關閉的檔案。

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMoniker 檔案::建立繫結狀態回檔

創建實現`IBindStatusCallback`的 COM 物件。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>參數

*pUnk 控制*<br/>
如果不使用聚合,則指向控制未知`IUnknown`(外部 ) 或 NULL 的指標。

### <a name="return-value"></a>傳回值

如果*pUnk 控制*不是 NULL,則函數`IUnknown``IBindStatusCallback`將傳回指向支援的新 COM 物件上的內部的指標。 如果`pUnkControlling`為 NULL,則函數傳回`IUnknown``IBindStatusCallback`指向支援的新 COM 物件上的指標。

### <a name="remarks"></a>備註

`CAsyncMonikerFile`需要實現`IBindStatusCallback`的 COM 物件。 MFC 實現這樣的物件,它是可聚合的。 您可以重寫`CreateBindStatusCallback`以返回自己的 COM 物件。 您的 COM 物件可以`CreateBindStatusCallback`通過呼叫控制未知 COM 物件的 MFC 實現來聚合 MFC 的實現。 使用`CCmdTarget`COM 支援實現的 COM 物件`CCmdTarget::GetControllingUnknown`可以使用 檢索 未知控制。

或者,您的 COM 物件可以`CreateBindStatusCallback( NULL )`通過調用 來委派到 MFC 的實現。

[CAsyncMoniker 檔案:開啟](#open)呼`CreateBindStatusCallback`叫 。

有關非同步名字器和非同步的詳細資訊,請參閱[IBindStatus 回檔](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))介面以及[非同步的結合與儲存的工作原理](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)。 有關聚合的討論,請參閱[聚合](/windows/win32/com/aggregation)。 所有三個主題都在 Windows SDK 中。

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMoniker 檔::取得賓德資訊

從非同步名字的用戶端調用,告訴非同步名字物件如何綁定。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>傳回值

檢索 設定`IBindStatusCallBack`。 有關介面的說明,`IBindStatusCallback`請參閱 Windows SDK。

### <a name="remarks"></a>備註

默認實現將綁定設置為非同步、使用儲存媒體(流)並使用資料推送模型。 如果要更改綁定的行為,將重寫此函數。

這樣做的一個原因是使用數據拉模型而不是數據推送模型進行綁定。 在數據提取模型中,用戶端驅動綁定操作,而名字物件僅在讀取用戶端時向用戶端提供數據。 在數據推送模型中,名字物件驅動非同步綁定操作,並在有新資料可用時持續通知用戶端。

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMoniker 檔案:取得繫結

調用此函數以檢索指向非同步傳輸綁定的指標。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>傳回值

指向非同步傳輸`IBinding`開始時提供的介面的指標。 如果由於任何原因無法非同步進行傳輸,則傳回 NULL。

### <a name="remarks"></a>備註

`IBinding`這允許您透過介面控制資料傳輸過程,例如,`IBinding::Abort`使用`IBinding::Pause`與`IBinding::Resume`。

有關介面的說明,`IBinding`請參閱 Windows SDK。

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonker 檔::取得格式

呼叫此函數以檢索流中資料的格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>傳回值

指向當前打開的流的 Windows 結構[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)的指標。 如果名字物件尚未綁定,則返回 NULL,如果它不是非同步的,或者非同步操作尚未開始。

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMoniker 檔案:取得優先權

當綁定進程開始接收綁定操作的線程的優先順序時,從異步名字項的用戶端調用。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>傳回值

非同步傳輸的優先順序。 標準線程優先順序標誌之一:THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL 和THREAD_PRIORITY_TIME_CRITICAL。 有關這些值的說明,請參閱 Windows 函數[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="remarks"></a>備註

`GetPriority`不應直接調用。 THREAD_PRIORITY_NORMAL由預設實現返回。

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMoniker 檔案::OnData可用

非同步名字物件調用`OnDataAvailable`在非同步綁定操作期間向用戶端提供資料。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>參數

*dwSize*<br/>
自綁定開始以來可用的數據的累積量(以位元組為單位)。 可以是零,指示數據量與操作無關,或者沒有可用的特定量。

*bscfFlag*<br/>
BSCF 枚舉值。 可以是以下一個或多個值:

- BSCF_FIRSTDATANOTIFICATION 標識給定綁定操作`OnDataAvailable`的第 一個調用。

- BSCF_INTERMEDIATEDATANOTIFICATION 標識綁定操作的`OnDataAvailable`中間 調用。

- BSCF_LASTDATANOTIFICATION 標識綁定操作的最後`OnDataAvailable`一 個調用。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 有關示例實現,請參閱以下範例。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonker 檔::在洛資源

當資源不足時,由名字物件調用。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>備註

預設執行呼叫`GetBinding( )-> Abort( )`。

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMoniker 檔案::在進度上

名字物件反覆調用以指示此綁定操作的當前進度,通常在長時間操作期間以合理的間隔進行。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>參數

*烏爾進步*<br/>
指示綁定操作相對於*ulProgressMax*中指示的預期最大值的當前進度。

*ulProgressMax*<br/>
指示此操作調用`OnProgress`期間*ulProgress*的預期最大值。

*ulStatus代碼*<br/>
提供有關綁定操作進度的其他資訊。 有效值取自`BINDSTATUS`枚舉。 有關可能的值,請參閱備註。

*szStatusText*<br/>
有關當前進度的信息,具體取決於*ulStatusCode*的值。 有關可能的值,請參閱備註。

### <a name="remarks"></a>備註

*ulStatusCode(* 以及每個值的*szStatusText)* 的可能值為:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |綁定操作是查找保存物件或存儲綁定到的資源。 *szStatusText*提供要搜索的資源的顯示名稱(例如,"www.microsoft.com")。  |
|BINDSTATUS_CONNECTING  |綁定操作連接到保存物件或存儲綁定到的資源。 *szStatusText*提供所連接的資源(例如,IP 位址)的顯示名稱。  |
|BINDSTATUS_SENDINGREQUEST|綁定操作請求綁定的物件或存儲。 *szStatusText*提供物件的顯示名稱(例如,檔名)。|
|BINDSTATUS_REDIRECTING  |綁定操作已重定向到其他數據位置。 *szStatusText*提供新資料位置的顯示名稱。  |
|BINDSTATUS_USINGCACHEDCOPY  |綁定操作是從緩存的副本檢索請求的物件或存儲。 *szStatusText*為 NULL。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |綁定操作已開始接收綁定的物件或存儲。 *szStatusText*提供資料位置的顯示名稱。|
|BINDSTATUS_DOWNLOADINGDATA  |綁定操作繼續接收綁定的物件或存儲。 *szStatusText*提供資料位置的顯示名稱。  |
|BINDSTATUS_ENDDOWNLOADDATA  |綁定操作已完成接收要綁定的物件或存儲。 *szStatusText*提供資料位置的顯示名稱。  |
|BINDSTATUS_CLASSIDAVAILABLE  |綁定到的物件的實例即將創建。 *szStatusText*以字串格式提供新物件的 CLSID,允許客戶端根據需要取消綁定操作。  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonker 檔案::開始繫結

覆蓋派生類中的此函數,在啟動綁定時執行操作。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>備註

此函數由名字物件調用回。 預設實作不做任何動作。

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonker 檔案::開啟繫結

由綁定操作結束時的綽號調用。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>參數

*h結果*<br/>
錯誤或警告值的 HRESULT。

*什洛特*<br/>
描述錯誤的字串。

### <a name="remarks"></a>備註

重寫此函數以在停止傳輸時執行操作。 預設情況下,函數將釋放`IBinding`。

有關介面的說明,`IBinding`請參閱 Windows SDK。

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMoniker 檔::開啟

調用此成員函數以非同步打開檔。

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
要非同步打開的檔指標。 該檔可以是任何有效的 URL 或檔名。

*pError*<br/>
指向文件異常的指標。 如果出現錯誤,它將設置為原因。

*普莫尼克爾*<br/>
指向非同步名字器介面`IMoniker`的指標,一個精確的名字物件,它是文檔自己的名字物件的組合,您可以使用檢索`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`,以及從路徑名稱創建的名字物件。 控件可以使用此名字綁定,但這不是控件應保存的名字。

*pBindHost*<br/>
指向介面的`IBindHost`指標,用於從潛在相對路徑名稱創建名字物件。 如果結合主機不合法或未提供名字物件,則呼叫預設為`Open(lpszFileName,pError)`。 有關介面的說明,`IBindHost`請參閱 Windows SDK。

*p 服務提供者*<br/>
Unmanaged 物件的 `IServiceProvider` 介面，擲回具有特定失敗 HRESULT 的例外狀況。 如果服務提供者無效或無法為`IBindHost`提供服務,則呼叫預設`Open(lpszFileName,pError)`為 。

*p 未知*<br/>
Unmanaged 物件的 `IUnknown` 介面，擲回具有特定失敗 HRESULT 的例外狀況。 找不到`IServiceProvider`,則函數會查詢`IBindHost`。 如果服務提供者無效或無法為`IBindHost`提供服務,則呼叫預設`Open(lpszFileName,pError)`為 。

### <a name="return-value"></a>傳回值

如果檔成功打開,則非零;否則 0。

### <a name="remarks"></a>備註

此調用啟動綁定進程。

可以使用 URL 或檔名進行*lpszURL*參數。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
