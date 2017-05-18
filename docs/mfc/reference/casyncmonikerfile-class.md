---
title: "CAsyncMonikerFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- monikers [C++], MFC
- asynchronous controls [C++]
- CAsyncMonikerFile class
- IMoniker interface, binding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 47ba3137b5d0d38aa59e9d627101de8350eebd50
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile 類別
提供可在 ActiveX 控制項 (先前稱為 OLE 控制項) 中使用非同步 Moniker 的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CAsyncMonikerFile : public CMonikerFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|建構 `CAsyncMonikerFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAsyncMonikerFile::Close](#close)|關閉並釋放所有資源。|  
|[CAsyncMonikerFile::GetBinding](#getbinding)|擷取非同步傳輸繫結的指標。|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|擷取資料流中的資料的格式。|  
|[CAsyncMonikerFile::Open](#open)|以非同步方式開啟檔案。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|建立 COM 物件實作`IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|呼叫由 OLE 系統程式庫上要建立的繫結類型的要求資訊。|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|呼叫 OLE 系統程式庫，取得繫結的優先順序。|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|呼叫以提供可用來在用戶端非同步繫結作業期間的資料。|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|當資源不足時呼叫。|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|呼叫以表示資料下載程序的進度。|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|當繫結啟動時呼叫。|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|停止非同步傳輸時呼叫。|  
  
## <a name="remarks"></a>備註  
 衍生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，而後者又衍生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`使用[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)介面來以非同步方式存取任何資料流包括從 URL 非同步載入的檔案。 檔案可以是 ActiveX 控制項的資料路徑屬性。  
  
 非同步 moniker 主要在啟用網際網路的應用程式和 ActiveX 控制項用於檔案傳輸期間提供回應的使用者介面。 基本的使用範例，就是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)為 ActiveX 控制項提供非同步屬性。 `CDataPathProperty`物件將會重複取得回呼冗長的屬性交換過程中表示的新資料的可用性。  
  
 如需如何在網際網路應用程式中使用非同步 moniker 以及 ActiveX 控制項的詳細資訊，請參閱下列文章︰  
  
- [非同步 Moniker 的網際網路第一個步驟︰](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [網際網路的第一個步驟︰ ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 建構 `CAsyncMonikerFile` 物件。  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>備註  
 它不會建立`IBindHost`介面。 `IBindHost`您提供時，才會使用**開啟**成員函式。  
  
 如需說明的`IBindHost`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="close"></a>CAsyncMonikerFile::Close  
 呼叫此函式可關閉並釋放所有資源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 可以呼叫未開啟或已關閉檔案。  
  
##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 建立 COM 物件實作`IBindStatusCallback`。  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>參數  
 `pUnkControlling`  
 控制未知的指標 (外部**IUnknown**) 或**NULL**如果不使用彙總。  
  
### <a name="return-value"></a>傳回值  
 如果`pUnkControlling`不**NULL**，函式會傳回內部指標**IUnknown**上新的 COM 物件支援`IBindStatusCallback`。 如果`pUnkControlling`是**NULL**，此函數會傳回指標**IUnknown**上新的 COM 物件支援`IBindStatusCallback`。  
  
### <a name="remarks"></a>備註  
 `CAsyncMonikerFile`需要實作的 COM 物件`IBindStatusCallback`。 MFC 實作這類物件，而且彙總。 您可以覆寫`CreateBindStatusCallback`回到您自己的 COM 物件。 您的 COM 物件可以藉由呼叫項目彙總 MFC 實作`CreateBindStatusCallback`與 COM 物件的控制未知。 使用實作的 COM 物件`CCmdTarget`COM 支援可以擷取控制未知使用**CCmdTarget::GetControllingUnknown**。  
  
 或者，您的 COM 物件可以委派給 MFC 實作藉由呼叫**CreateBindStatusCallback (NULL)**。  
  
 [CAsyncMonikerFile::Open](#open)呼叫`CreateBindStatusCallback`。  
  
 如需有關非同步 moniker 和非同步繫結的詳細資訊，請參閱[IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060)介面和[如何非同步繫結和儲存體工作](http://msdn.microsoft.com/library/windows/desktop/aa379152)。 如需彙總的討論，請參閱[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 所有的三個主題位於[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 從用戶端的非同步 moniker，告訴它要繫結的方式非同步 moniker 呼叫。  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 擷取的設定**IBindStatusCallBack**。 如需說明的`IBindStatusCallback`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 預設實作會設定為非同步，使用儲存媒體 （串流），並且將資料推送模型繫結。 如果您想要變更繫結的行為，請覆寫這個函式。  
  
 執行此作業的一個原因就是使用資料提取模型，而不資料發送模型繫結。 在資料提取模型中，用戶端磁碟機繫結作業，和 moniker 只提供資料給用戶端會在讀取。 在資料推入模型中，moniker 可促進非同步繫結作業以及持續在新的資料可用時通知用戶端。  
  
##  <a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 呼叫此函式可擷取非同步傳輸繫結的指標。  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IBinding`提供非同步傳輸開始時的介面。 傳回**NULL**如果基於任何理由傳輸無法以非同步方式進行。  
  
### <a name="remarks"></a>備註  
 這可讓您控制的資料傳輸程序，透過`IBinding`介面，例如，與**IBinding::Abort**， **IBinding::Pause**，和**IBinding::Resume**。  
  
 如需說明的`IBinding`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 呼叫此函式可擷取的資料流中的資料格式。  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows 結構的指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)目前開啟的資料流。 傳回**NULL**如果 moniker 不已繫結，如果不是非同步的或者尚未開始執行非同步作業。  
  
##  <a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 已從呼叫非同步 moniker 的用戶端繫結程序啟動接收執行緒給繫結作業的優先順序。  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在非同步傳輸，就會進行優先順序。 其中一個標準的執行緒優先順序旗標︰ **THREAD_PRIORITY_ABOVE_NORMAL**， **THREAD_PRIORITY_BELOW_NORMAL**， **THREAD_PRIORITY_HIGHEST**， **THREAD_PRIORITY_IDLE**， **THREAD_PRIORITY_LOWEST**， **THREAD_PRIORITY_NORMAL**，和**THREAD_PRIORITY_TIME_CRITICAL**。 請參閱 Windows 函式[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)如需這些值的說明。  
  
### <a name="remarks"></a>備註  
 `GetPriority`應該不會直接呼叫。 **THREAD_PRIORITY_NORMAL**傳回的預設實作。  
  
##  <a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 非同步 moniker 呼叫`OnDataAvailable`變成可用，請提供資料給用戶端，在非同步繫結作業。  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>參數  
 `dwSize`  
 累積數量 （以位元組為單位） 的繫結起可用的資料。 可以是零，表示的資料量不相關的作業，或沒有特定的數量變得可用。  
  
 *bscfFlag*  
 A **BSCF**列舉值。 可以是一或多個下列值︰  
  
- **BSCF_FIRSTDATANOTIFICATION**識別第一個呼叫`OnDataAvailable`指定的繫結作業。  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION**識別的中間呼叫`OnDataAvailable`繫結作業。  
  
- **BSCF_LASTDATANOTIFICATION**識別在上次呼叫`OnDataAvailable`繫結作業。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 如需範例實作下列的範例，請參閱。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWinInet # 5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 當資源不足時，moniker 所呼叫。  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`GetBinding( )-> Abort( )`。  
  
##  <a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 呼叫重複，表示目前的這項繫結作業，通常在合理的時間間隔期間長時間作業進度的 moniker。  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>參數  
 `ulProgress`  
 指出目前的繫結作業中所示的預期最大值的相對進度`ulProgressMax`。  
  
 `ulProgressMax`  
 表示預期的最大值的`ulProgress`呼叫期間`OnProgress`這項作業。  
  
 `ulStatusCode`  
 提供繫結作業的進度相關的其他的資訊。 有效的值取自`BINDSTATUS`列舉型別。 可能的值，請參閱 < 備註 >。  
  
 `szStatusText`  
 目前的進度，根據的值的相關資訊`ulStatusCode`。 可能的值，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 可能值`ulStatusCode`(和`szStatusText`每個值) 是︰  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 繫結作業正在尋找用來保存物件或繫結至儲存體資源。 `szStatusText`提供要搜尋的資源的顯示名稱 (例如"www.microsoft.com")。  
  
 **BINDSTATUS_CONNECTING**  
 繫結作業正在連接到用來保存物件或繫結至儲存體資源。 `szStatusText`提供資源 （例如，IP 位址） 連接到的顯示名稱。  
  
 **BINDSTATUS_SENDINGREQUEST**  
 繫結作業要求的物件或繫結到的存放裝置。 `szStatusText`提供物件 （例如，檔案名稱） 的顯示名稱。  
  
 **BINDSTATUS_REDIRECTING**  
 繫結作業已經重新導向至不同的資料位置。 `szStatusText`提供新的資料位置的顯示名稱。  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 繫結作業正在擷取快取副本的要求的物件或存放裝置。 The `szStatusText` is **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 繫結作業已經開始接收物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 繫結作業會繼續接收物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 繫結作業已完成接收物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 正繫結至物件的執行個體是只建立。 `szStatusText`提供可讓用戶端有機會取消繫結作業中，視字串格式中的新物件的 CLSID。  
  
##  <a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 覆寫您繫結啟動時執行動作的衍生類別中的這個函式。  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>備註  
 此函式會呼叫回 moniker。 預設實作不做任何動作。  
  
##  <a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 由繫結作業結尾處 moniker 來呼叫。  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>參數  
 `hresult`  
 `HRESULT`也就是錯誤或警告的值。  
  
 *szErrort*  
 描述錯誤的字元字串。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來停止傳輸時執行的動作。 根據預設，函式會釋放`IBinding`。  
  
 如需說明的`IBinding`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="open"></a>CAsyncMonikerFile::Open  
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
 `lpszURL`  
 若要以非同步方式開啟檔案的指標。 檔案可以是任何有效的 URL 或檔案名稱。  
  
 `pError`  
 檔案例外狀況指標。 發生錯誤時，它就會設定為可能的原因。  
  
 `pMoniker`  
 非同步 moniker 介面的指標`IMoniker`，是文件本身的 moniker 時，您可以使用擷取的組合中的精確 moniker **IOleClientSite::GetMoniker (** *OLEWHICHMK_CONTAINER* **)**，和建立路徑名稱的 moniker。 控制項要繫結，就可以使用這個 moniker，但這不是控制項應該儲存的 moniker。  
  
 *pBindHost*  
 指標`IBindHost`將用於建立 moniker 從可能的相對路徑名稱的介面。 如果繫結主機無效或未提供 moniker，呼叫就會預設為**開啟 (** `lpszFileName` **，**`pError`**)**。 如需說明的`IBindHost`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pServiceProvider`  
 指標`IServiceProvider`介面。 如果服務提供者無效或無法提供的服務`IBindHost`，呼叫預設值為**開啟 (** `lpszFileName` **，**`pError`**)**。  
  
 *pUnknown*  
 指標**IUnknown**介面。 如果`IServiceProvider`找到時，此公式會查詢如`IBindHost`。 如果服務提供者無效或無法提供的服務`IBindHost`，呼叫預設值為**開啟 (** `lpszFileName` **，**`pError`**)**。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 開啟檔案，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此呼叫會起始繫結程序。  
  
 您可以使用 URL 或檔案名稱`lpszURL`參數。 例如:   
  
 [!code-cpp[NVC_MFCWinInet # 6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet # 7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)

