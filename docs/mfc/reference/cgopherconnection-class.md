---
title: CGopherConnection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49fe725c700a46e59625289de7ca5edf4b4d25b2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955683"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 類別
管理您與 Gopher 網際網路伺服器的連接。  
  
> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`及它們的成員已被取代，因為它們無法在 Windows XP 平台運作，但他們仍會繼續在舊版平台上運作。  
  
## <a name="syntax"></a>語法  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](#cgopherconnection)|建構 `CGopherConnection` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CGopherConnection::CreateLocator](#createlocator)|建立[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) gopher 伺服器上尋找檔案的物件。|  
|[CGopherConnection::GetAttribute](#getattribute)|擷取 gopher 物件的屬性資訊。|  
|[CGopherConnection::OpenFile](#openfile)|開啟 gopher 檔案。|  
  
## <a name="remarks"></a>備註  
 Gopher 服務是其中一個 MFC WinInet 類別所辨識的三個網際網路服務。  
  
 類別`CGopherConnection`包含建構函式和管理 gopher 服務的三個額外的成員函式： [OpenFile](#openfile)， [CreateLocator](#createlocator)，和[Xmlelement](#getattribute).  
  
 若要與 gopher 網際網路伺服器通訊，您必須先建立的執行個體[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然後呼叫[CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，這樣就可以建立`CGopherConnection`物件，並傳回的指標。 您絕對不要建立`CGopherConnection`直接物件。  
  
 若要深入了解如何`CGopherConnection`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 如需有關使用其他兩個支援的網際網路服務，FTP 和 HTTP 查看類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection  
 呼叫此成員函式會建構`CGopherConnection`物件。  
  
```  
CGopherConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CGopherConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>參數  
 *pSession*  
 相關的指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。  
  
 *hConnected*  
 目前的網際網路工作階段的 Windows 控制代碼。  
  
 *pstrServer*  
 包含 FTP 伺服器名稱的字串指標。  
  
 *dwContext*  
 作業的內容識別碼。 *dwContext*識別作業的狀態資訊傳回[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 預設是設為 1。不過，您可以明確指派作業的特定內容識別碼。 物件，且任何工作，它會將相關聯的內容識別碼。  
  
 *pstrUserName*  
 以 null 終止的字串，指定使用者登入名稱的指標。 如果**NULL**，預設值是匿名的。  
  
 *pstrPassword*  
 指向以 null 結束的字串，指定要用來登入密碼。 如果兩個*pstrPassword*和*pstrUserName*是**NULL**，預設匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*是**NULL** （或空字串），但*pstrUserName*不**NULL**，則使用空白密碼。 下表描述四個可能設定的行為*pstrUserName*和*pstrPassword*:  
  
|*pstrUserName*|*pstrPassword*|傳送至 FTP 伺服器的使用者名稱|傳送至 FTP 伺服器的密碼|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|「 匿名 」|使用者的電子郵件名稱|  
|非- **NULL**字串|**NULL**或""|*pstrUserName*|" "|  
|**NULL**非**NULL**字串|**錯誤**|**錯誤**||  
|非- **NULL**字串|非- **NULL**字串|*pstrUserName*|*pstrPassword*|  
  
 *nPort*  
 識別要在伺服器上使用的 TCP/IP 連接埠的數字。  
  
### <a name="remarks"></a>備註  
 您絕對不要建立`CGopherConnection`直接。 相反地，呼叫[CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，它會建立`CGopherConnection`物件，並傳回的指標。  
  
##  <a name="createlocator"></a>  CGopherConnection::CreateLocator  
 呼叫此成員函式建立 gopher 定位器尋找或識別在 gopher 伺服器上的檔案。  
  
```  
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType);  
  
static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

 
static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,  
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>參數  
 *pstrDisplayString*  
 包含 gopher 文件或要擷取的目錄名稱的字串指標。 如果*pstrDisplayString*參數是**NULL**，就會傳回 gopher 伺服器的預設目錄。  
  
 *pstrSelectorString*  
 若要擷取項目傳送至 gopher 伺服器的選取器字串指標。 *pstrSelectorString*可以**NULL**。  
  
 *dwGopherType*  
 這會指定是否*pstrSelectorString*指的是目錄或文件，且該要求是否是 gopher +。 請參閱結構屬性[GOPHER_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa384215) Windows SDK 中。  
  
 *pstrLocator*  
 識別要開啟的檔案的字串指標。 一般而言，這個字串會傳回呼叫[CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。  
  
 *pstrServerName*  
 包含 gopher 伺服器名稱的字串指標。  
  
 *nPort*  
 數字，識別此連線的網際網路連接埠。  
  
### <a name="return-value"></a>傳回值  
 A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。  
  
### <a name="remarks"></a>備註  
 靜態成員函式版本會要求您指定伺服器，而非靜態版本使用的連接物件的伺服器名稱。  
  
 若要從 gopher 伺服器擷取資訊，應用程式必須先取得 gopher 定位器。 應用程式然後必須將視為不透明的語彙基元的定位器 （也就是應用程式可以使用定位程式，但不是直接操作或比較）。 一般來說，應用程式的呼叫中使用定位器[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成員函式來擷取特定資訊。  
  
##  <a name="getattribute"></a>  CGopherConnection::GetAttribute  
 呼叫此成員函式可擷取特定的屬性資訊項目從 gopher 伺服器。  
  
```  
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,  
    CString& strResult,);
```  
  
### <a name="parameters"></a>參數  
 *refLocator*  
 若要參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。  
  
 *strRequestedAttributes*  
 以空格分隔的字串，指定要求的屬性名稱。  
  
 *strResult*  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收定位器類型。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
##  <a name="openfile"></a>  CGopherConnection::OpenFile  
 呼叫此成員函式，以開啟 gopher 伺服器上的檔案。  
  
```  
CGopherFile* OpenFile(
    CGopherLocator& refLocator,  
    DWORD dwFlags = 0,  
    LPCTSTR pstrView = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 *refLocator*  
 若要參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。  
  
 *dwFlags*  
 INTERNET_FLAG_ * 旗標的任意組合。 請參閱[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)更多有關 INTERNET_FLAG_\*旗標。  
  
 *pstrView*  
 檔案檢視字串指標。 如果檔案的幾種檢視存在於伺服器時，此參數會指定要開啟的檔案檢視。 如果*pstrView*是**NULL**，會使用預設檔案檢視。  
  
 *dwContext*  
 正在開啟的檔案內容識別碼。 請參閱**備註**如需有關*dwContext*。  
  
### <a name="return-value"></a>傳回值  
 指標[CGopherFile](../../mfc/reference/cgopherfile-class.md)来開啟物件。  
  
### <a name="remarks"></a>備註  
 覆寫*dwContext*預設可設定的內容識別碼以您選擇的值。 內容識別碼是與這個特定作業的相關聯`CGopherConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
