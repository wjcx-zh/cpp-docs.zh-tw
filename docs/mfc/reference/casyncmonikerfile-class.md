---
title: "CAsyncMonikerFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAsyncMonikerFile
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: eb8727e6fe884c98fe010beab072fb7268f2e2c4
ms.lasthandoff: 02/24/2017

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
  
|名稱|描述|  
|----------|-----------------|  
|[CAsyncMonikerFile::Close](#close)|關閉並釋放所有資源。|  
|[CAsyncMonikerFile::GetBinding](#getbinding)|擷取非同步傳輸繫結的指標。|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|擷取資料流中的資料的格式。|  
|[CAsyncMonikerFile::Open](#open)|以非同步方式開啟檔案。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|建立 COM 物件實作`IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|呼叫 OLE 系統程式庫中建立的繫結的型別要求資訊。|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|呼叫 OLE 系統程式庫，以取得繫結的優先順序。|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|呼叫以提供資料變成非同步繫結作業期間用戶端可用的。|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|當資源不足時呼叫。|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|呼叫以表示資料下載程序的進度。|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|正在啟動繫結時呼叫。|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|停止非同步傳輸時呼叫。|  
  
## <a name="remarks"></a>備註  
 衍生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，而後者又衍生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`使用[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)介面以非同步方式存取任何資料流包括從 URL 非同步載入檔案。 檔案可以是 ActiveX 控制項的資料路徑屬性。  
  
 非同步 moniker 主要在網際網路的應用程式和 ActiveX 控制項用於檔案傳輸期間提供反應靈敏的使用者介面。 這個範例是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)為 ActiveX 控制項提供非同步屬性。 `CDataPathProperty`物件會重複得到回呼長時間的屬性交換過程中表示新資料的可用性。  
  
 如需如何在 網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列文章︰  
  
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
  
##  <a name="a-namecasyncmonikerfilea--casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 建構 `CAsyncMonikerFile` 物件。  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>備註  
 它不會建立`IBindHost`介面。 `IBindHost`只有在您提供在使用**開啟**成員函式。  
  
 如需說明`IBindHost`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclosea--casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Close  
 呼叫此函式來關閉並釋放所有資源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 可以在未開啟或已關閉的檔案上呼叫。  
  
##  <a name="a-namecreatebindstatuscallbacka--casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 建立 COM 物件實作`IBindStatusCallback`。  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>參數  
 `pUnkControlling`  
 控制未知的指標 (外部**IUnknown**) 或**NULL**若未使用彙總。  
  
### <a name="return-value"></a>傳回值  
 如果`pUnkControlling`不**NULL**，函式會傳回內部指標**IUnknown**在新的 COM 物件支援`IBindStatusCallback`。 如果`pUnkControlling`是**NULL**，此函數會傳回指標**IUnknown**在新的 COM 物件支援`IBindStatusCallback`。  
  
### <a name="remarks"></a>備註  
 `CAsyncMonikerFile`需要實作的 COM 物件`IBindStatusCallback`。 MFC 實作這類物件，而且可彙總。 您可以覆寫`CreateBindStatusCallback`傳回您自己的 COM 物件。 您的 COM 物件可以藉由呼叫彙 MFC 實作`CreateBindStatusCallback`且您的 COM 物件的控制。 使用實作的 COM 物件`CCmdTarget`擷取 COM 支援控制無法辨識 using **CCmdTarget::GetControllingUnknown**。  
  
 或者，您的 COM 物件可以委派至 MFC 的實作呼叫**CreateBindStatusCallback (NULL)**。  
  
 [CAsyncMonikerFile::Open](#open)呼叫`CreateBindStatusCallback`。  
  
 如需非同步 moniker 和非同步繫結的詳細資訊，請參閱[IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060)介面和[如何非同步繫結和儲存體工作](http://msdn.microsoft.com/library/windows/desktop/aa379152)。 如需彙總的討論，請參閱[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 所有的三個主題位於[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbindinfoa--casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 從告訴它要繫結的方式的非同步 moniker，非同步 moniker 的用戶端呼叫。  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>傳回值  
 擷取的設定**IBindStatusCallBack**。 如需說明`IBindStatusCallback`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 預設實作會設定的繫結是非同步的若要使用的儲存媒體 (stream)，並將資料推入模式。 如果您想要變更繫結的行為，請覆寫這個函式。  
  
 執行此動作的其中一個原因是使用資料提取模型，而不資料發送模型繫結。 在資料提取模型中，用戶端繫結作業，和 moniker 只提供資料給用戶端會在讀取。 在資料推入模型中，moniker 非同步繫結作業的磁碟機，並持續在每當有新的資料可用時通知用戶端。  
  
##  <a name="a-namegetbindinga--casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 呼叫此函式可擷取非同步傳輸繫結的指標。  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IBinding`時開始執行非同步傳送所提供的介面。 傳回**NULL**如果基於任何理由傳輸無法以非同步方式進行。  
  
### <a name="remarks"></a>備註  
 這可讓您控制的資料傳輸程序，透過`IBinding`介面，例如，使用**IBinding::Abort**， **IBinding::Pause**，和**IBinding::Resume**。  
  
 如需說明`IBinding`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetformatetca--casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 呼叫此函式可擷取的資料流中的資料格式。  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows 結構的指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)目前開啟的資料流。 傳回**NULL** moniker 未繫結，如果不是非同步的或者尚未開始非同步作業。  
  
##  <a name="a-namegetprioritya--casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 呼叫非同步 moniker 的用戶端從繫結程序開始時接收到執行緒給繫結作業的優先順序。  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>傳回值  
 優先順序的非同步傳輸不會發生。 其中一個標準的執行緒優先順序旗標︰ **THREAD_PRIORITY_ABOVE_NORMAL**， **THREAD_PRIORITY_BELOW_NORMAL**， **THREAD_PRIORITY_HIGHEST**， **THREAD_PRIORITY_IDLE**， **THREAD_PRIORITY_LOWEST**， **THREAD_PRIORITY_NORMAL**，和**THREAD_PRIORITY_TIME_CRITICAL**。 請參閱 Windows 函式[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)取得這些值的描述。  
  
### <a name="remarks"></a>備註  
 `GetPriority`應該不會直接呼叫。 **THREAD_PRIORITY_NORMAL**預設實作會傳回。  
  
##  <a name="a-nameondataavailablea--casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 非同步 moniker 呼叫`OnDataAvailable`可用時，請提供資料給用戶端，在非同步繫結作業。  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>參數  
 `dwSize`  
 （以位元組為單位） 的資料繫結的開頭開始提供的累計數量。 可以是零，表示的資料量不相關的作業，或沒有特定的數量變成可用。  
  
 *bscfFlag*  
 A **BSCF**列舉值。 可以是一或多個下列值︰  
  
- **BSCF_FIRSTDATANOTIFICATION**識別第一個呼叫`OnDataAvailable`指定繫結作業。  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION**識別中繼呼叫`OnDataAvailable`繫結作業。  
  
- **BSCF_LASTDATANOTIFICATION**識別上次呼叫`OnDataAvailable`繫結作業。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 請參閱以下的範例實作的範例。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWinInet #&5;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="a-nameonlowresourcea--casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 時資源不足，而呼叫 moniker。  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`GetBinding( )-> Abort( )`。  
  
##  <a name="a-nameonprogressa--casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 呼叫重複，表示這個繫結作業，通常在合理的時間間隔長時間作業期間的目前進度的 moniker。  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>參數  
 `ulProgress`  
 指出目前的繫結作業中指出的預期最大值的相對進度`ulProgressMax`。  
  
 `ulProgressMax`  
 表示預期的最大值的`ulProgress`呼叫期間`OnProgress`這項作業。  
  
 `ulStatusCode`  
 提供繫結作業的進度相關的其他的資訊。 有效的值取自`BINDSTATUS`列舉型別。 可能的值，請參閱 < 備註 >。  
  
 `szStatusText`  
 目前的進度，根據的值的相關資訊`ulStatusCode`。 可能的值，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 可能值`ulStatusCode`(和`szStatusText`每個值) 是︰  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 繫結作業尋找用來保存物件或繫結至儲存體資源。 `szStatusText`提供要搜尋資源的顯示名稱 (例如，「 www.microsoft.com 」)。  
  
 **BINDSTATUS_CONNECTING**  
 繫結作業連線到用來保存物件或繫結至儲存體資源。 `szStatusText`提供連接到 （例如，IP 位址） 資源的顯示名稱。  
  
 **BINDSTATUS_SENDINGREQUEST**  
 繫結作業要求的物件或繫結至儲存體。 `szStatusText`提供物件 （例如，檔案名稱） 的顯示名稱。  
  
 **BINDSTATUS_REDIRECTING**  
 繫結作業已重新導向至不同的資料位置。 `szStatusText`提供新的資料位置的顯示名稱。  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 繫結作業會從快取複本擷取要求的物件或儲存體。 The `szStatusText` is **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 繫結操作已開始接收物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 繫結作業會繼續接收物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 在繫結作業完成後接收的物件或繫結至儲存體。 `szStatusText`提供的資料位置的顯示名稱。  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 繫結至物件的執行個體只是要建立的。 `szStatusText`提供可讓用戶端有機會取消繫結作業中，視字串格式的新物件的 CLSID。  
  
##  <a name="a-nameonstartbindinga--casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 覆寫這個函式，在您啟動繫結時執行動作的衍生類別中。  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>備註  
 此函式被回呼 moniker。 預設實作不做任何動作。  
  
##  <a name="a-nameonstopbindinga--casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 呼叫的繫結作業結尾的 moniker。  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>參數  
 `hresult`  
 `HRESULT`也就是錯誤或警告的值。  
  
 *szErrort*  
 描述錯誤的字串。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來執行動作時停止傳輸。 根據預設，函式會釋放`IBinding`。  
  
 如需說明`IBinding`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameopena--casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Open  
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
 檔案例外狀況指標。 發生錯誤時，它將設定的原因。  
  
 `pMoniker`  
 非同步 moniker 介面的指標`IMoniker`，結合的文件自己的 moniker 時，您可以使用擷取其中的精確 moniker **IOleClientSite::GetMoniker (** *OLEWHICHMK_CONTAINER* **)**，和路徑名稱，建立的 moniker。 控制項可以使用這個 moniker 繫結，但這不是控制項應該將儲存的 moniker。  
  
 *pBindHost*  
 指標`IBindHost`將用於建立 moniker 從可能的相對路徑名稱的介面。 如果繫結主機無效或未提供 moniker，呼叫會預設為**開啟 (** `lpszFileName` **，**`pError`**)**。 如需說明`IBindHost`介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pServiceProvider`  
 指標`IServiceProvider`介面。 如果服務提供者無效或無法提供服務給`IBindHost`，呼叫會預設為**開啟 (** `lpszFileName` **，**`pError`**)**。  
  
 *pUnknown*  
 指標**IUnknown**介面。 如果`IServiceProvider`找到，則函式的查詢`IBindHost`。 如果服務提供者無效或無法提供服務給`IBindHost`，呼叫會預設為**開啟 (** `lpszFileName` **，**`pError`**)**。  
  
### <a name="return-value"></a>傳回值  
 如果成功，開啟檔案，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個呼叫初始化繫結程序。  
  
 您可以使用 URL 或檔案名稱`lpszURL`參數。 例如：  
  
 [!code-cpp[NVC_MFCWinInet #&6;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 -或-  
  
 [!code-cpp[NVC_MFCWinInet #&7;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMonikerFile 類別](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)

