---
title: "CFtpConnection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
dev_langs:
- C++
helpviewer_keywords:
- CFtpConnection class
- FTP (File Transfer Protocol), establishing connections
- Internet connections, FTP
- Internet services, FTP
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ebfe4078bf70d0afc2d36a222b61c11dbaf7c64d
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cftpconnection-class"></a>CFtpConnection 類別
管理您與網際網路伺服器的 FTP 連接，並允許直接操作該伺服器上目錄和檔案。  
  
## <a name="syntax"></a>語法  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFtpConnection::CFtpConnection](#cftpconnection)|建構 `CFtpConnection` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFtpConnection::Command](#command)|將命令直接傳送至 FTP 伺服器。|  
|[CFtpConnection::CreateDirectory](#createdirectory)|在伺服器上建立目錄。|  
|[Cftpconnection:: Getcurrentdirectory](#getcurrentdirectory)|取得此連接目前的目錄。|  
|[Cftpconnection:: Getcurrentdirectoryasurl](#getcurrentdirectoryasurl)|取得這個連線的 URL 為目前的目錄。|  
|[CFtpConnection::GetFile](#getfile)|從連接的伺服器取得檔案|  
|[CFtpConnection::OpenFile](#openfile)|開啟連接的伺服器上的檔案。|  
|[CFtpConnection::PutFile](#putfile)|將放在伺服器上的檔案。|  
|[Findfile](#remove)|從伺服器移除檔案。|  
|[CFtpConnection::RemoveDirectory](#removedirectory)|從伺服器中移除指定的目錄。|  
|[CFtpConnection::Rename](#rename)|重新命名的伺服器上的檔案。|  
|[Cftpconnection:: Setcurrentdirectory](#setcurrentdirectory)|設定目前的 FTP 目錄。|  
  
## <a name="remarks"></a>備註  
 FTP 是其中一個 MFC WinInet 類別可辨識的三種網際網路服務。  
  
 若要與網際網路 FTP 伺服器通訊，您必須先建立的執行個體[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然後再建立`CFtpConnection`物件。 絕對不要建立`CFtpConnection`直接物件; 而是呼叫[Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，這樣就可以建立`CFtpConnection`物件，並傳回的指標。  
  
 若要深入了解如何`CFtpConnection`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 如需有關支援與其他兩個與通訊服務，HTTP 和 gopher，請參閱類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。  
  
## <a name="example"></a>範例  
  請參閱範例[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)類別概觀。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
  
##  <a name="cftpconnection"></a>CFtpConnection::CFtpConnection  
 此成員函式呼叫來建構`CFtpConnection`物件。  
  
```  
CFtpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CFtpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `pSession`  
 相關的指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。  
  
 `hConnected`  
 目前的網際網路工作階段的視窗控制代碼。  
  
 `pstrServer`  
 包含 FTP 伺服器名稱的字串指標。  
  
 `dwContext`  
 作業的內容識別碼。 `dwContext`識別所傳回的作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 預設值是設定為 1。不過，您可以明確指派作業的特定內容識別碼。 物件，它沒有任何工作將會與該內容識別碼建立關聯  
  
 `pstrUserName`  
 以 null 終止的字串，指定使用者登入名稱的指標。 如果**NULL**，預設值是匿名的。  
  
 `pstrPassword`  
 以 null 終止的字串，指定要用來登入密碼指標。 如果兩個`pstrPassword`和`pstrUserName`是**NULL**，預設匿名密碼是使用者的電子郵件名稱。 如果`pstrPassword`是**NULL** （或空字串），但`pstrUserName`不**NULL**，使用空白密碼。 下表說明的四個可能的設定行為`pstrUserName`和`pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|傳送至 FTP 伺服器的使用者名稱|傳送至 FTP 伺服器的密碼|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或 「 」|**NULL**或 「 」|「 匿名 」|使用者的電子郵件名稱|  
|非- **NULL**字串|**NULL**或 「 」|`pstrUserName`|" "|  
|**NULL**非**NULL**字串|**錯誤**|**錯誤**||  
|非- **NULL**字串|非- **NULL**字串|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 識別在伺服器上使用的 TCP/IP 通訊埠的數字。  
  
 `bPassive`  
 指定此 FTP 工作階段被動還是主動模式。 如果設定為**TRUE**，它會設定 Win32 API`dwFlag`至**INTERNET_FLAG_PASSIVE**。  
  
### <a name="remarks"></a>備註  
 絕對不要建立`CFtpConnection`直接物件。 請改為呼叫[Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，這樣就可以建立**CFptConnection**物件。  
  
##  <a name="command"></a>CFtpConnection::Command  
 將命令直接傳送至 FTP 伺服器。  
  
```  
CInternetFile* Command(
    LPCTSTR pszCommand,  
    CmdResponseType eResponse = CmdRespNone,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pszCommand`  
 包含要傳送至命令的字串指標。  
  
 *eResponse*  
 決定是否會有來自於 FTP 伺服器的回應。 可為下列其中一個值：  
  
- **CmdRespNone**不需要回應。  
  
- **CmdRespRead**預期回應。  
  
 `dwFlags`  
 一個值，包含控制此函式的旗標。 如需完整清單，請參閱[FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133)。  
  
 `dwContext`  
 值的指標，包含應用程式定義的值，用以識別回呼中的應用程式內容。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133)函式，如下所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果發生錯誤時，MFC 會擲回例外狀況型別[CInternetException](../../mfc/reference/cinternetexception-class.md)。  
  
##  <a name="createdirectory"></a>CFtpConnection::CreateDirectory  
 呼叫此成員函式在已連線的伺服器上建立目錄。  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>參數  
 `pstrDirName`  
 包含要建立的目錄名稱的字串指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Windows 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 使用`GetCurrentDirectory`來判斷目前的工作目錄的伺服器連接。 請勿假設遠端系統已連接您的根目錄。  
  
 `pstrDirName`參數可以是部分或完整的檔案名稱與目前的目錄。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `CreateDirectory`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="getcurrentdirectory"></a>Cftpconnection:: Getcurrentdirectory  
 呼叫此成員函式，以取得目前目錄的名稱。  
  
```  
BOOL GetCurrentDirectory(CString& strDirName) const;  
  
BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>參數  
 `strDirName`  
 將會收到的目錄名稱字串的參考。  
  
 `pstrDirName`  
 將會收到的目錄名稱的字串指標。  
  
 `lpdwLen`  
 指標 DWORD，其中包含下列資訊︰  
  
|||  
|-|-|  
|項目|所參考的緩衝區大小`pstrDirName`。|  
|在傳回|若要儲存的字元數`pstrDirName`。 如果成員函式會失敗，而且會傳回 ERROR_INSUFFICIENT_BUFFER，然後`lpdwLen`包含應用程式必須以接收字串配置的位元組數目。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 若要改為取得做為 URL 的目錄名稱，請呼叫[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。  
  
 參數`pstrDirName`或`strDirName`可以是相對於目前目錄是不完整檔案名稱或完整限定。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `GetCurrentDirectory`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="getcurrentdirectoryasurl"></a>Cftpconnection:: Getcurrentdirectoryasurl  
 呼叫此成員函式，取得目前的目錄名稱做為 URL。  
  
```  
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;  
  
BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>參數  
 `strDirName`  
 將會收到的目錄名稱字串的參考。  
  
 `pstrDirName`  
 將會收到的目錄名稱的字串指標。  
  
 `lpdwLen`  
 指標 DWORD，其中包含下列資訊︰  
  
|||  
|-|-|  
|項目|所參考的緩衝區大小`pstrDirName`。|  
|在傳回|若要儲存的字元數`pstrDirName`。 如果成員函式會失敗，而且會傳回 ERROR_INSUFFICIENT_BUFFER，然後`lpdwLen`包含應用程式必須以接收字串配置的位元組數目。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `GetCurrentDirectoryAsURL`行為與相同[GetCurrentDirectory](#getcurrentdirectory)  
  
 參數`strDirName`可以是相對於目前目錄是不完整檔案名稱或完整限定。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `GetCurrentDirectoryAsURL`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="getfile"></a>CFtpConnection::GetFile  
 呼叫此成員函式，取得從 FTP 伺服器的檔案，並將它儲存在本機電腦上。  
  
```  
BOOL GetFile(
    LPCTSTR pstrRemoteFile,  
    LPCTSTR pstrLocalFile,  
    BOOL bFailIfExists = TRUE,  
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pstrRemoteFile`  
 以 null 終止的字串，其中包含從 FTP 伺服器擷取檔案名稱的指標。  
  
 `pstrLocalFile`  
 以 null 終止的字串，其中包含要建立本機系統上的檔案名稱的指標。  
  
 *bFailIfExists*  
 指出是否可能已為現有檔案所使用的檔案名稱。 如果本機檔案名稱已經存在，且這個參數是**TRUE**，`GetFile`失敗。 否則，`GetFile`會清除檔案的現有副本。  
  
 `dwAttributes`  
 指出檔案的屬性。 這可以是下列 FILE_ATTRIBUTE_ * 旗標的任意組合。  
  
-   FILE_ATTRIBUTE_ARCHIVE 檔案是保存檔案。 應用程式會使用這個屬性，將檔案備份或移除標記。  
  
-   壓縮 FILE_ATTRIBUTE_COMPRESSED 檔案或目錄。 壓縮檔案，表示會壓縮所有檔案中的資料。 對於目錄，壓縮會為新建立的檔案和子目錄的預設值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 檔案是目錄。  
  
-   FILE_ATTRIBUTE_NORMAL 檔案具有未設定其他屬性。 這個屬性是單獨使用時才有效。 所有其他檔案屬性覆寫 FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN 隱藏的檔案。 它並不包含在一般的目錄清單。  
  
-   FILE_ATTRIBUTE_READONLY 檔案是唯讀的。 應用程式可以讀取檔案，但無法寫入或刪除它。  
  
-   FILE_ATTRIBUTE_SYSTEM 檔案的一部分或作業系統所獨佔使用。  
  
-   FILE_ATTRIBUTE_TEMPORARY 檔案用於暫存儲存體。 只有在絕對必要時，應用程式應該寫入檔案。 大部分的檔案的資料會保存在記憶體中，而不會排清到媒體中，因為很快就會刪除檔案。  
  
 `dwFlags`  
 指定的條件下，進行轉送。 這個參數可以是任何一個`dwFlags`值中所述[FtpGetFile](http://msdn.microsoft.com/library/windows/desktop/aa384157)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwContext`  
 擷取檔案的內容識別碼。 請參閱**備註**如需詳細資訊`dwContext`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `GetFile`是高階的常式來處理所有從 FTP 伺服器讀取檔案，並將其儲存到本機相關聯的額外負荷。 應用程式，只擷取檔案資料，或需要關閉控制的檔案傳輸，應使用`OpenFile`和[CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read)改。  
  
 如果`dwFlags`FILE_TRANSFER_TYPE_ASCII，轉譯的檔案資料也將控制項並格式化成 Windows 對等字元。 預設傳輸是二進位模式中，其中會下載檔案，在相同的格式儲存在伺服器上。  
  
 同時`pstrRemoteFile`和`pstrLocalFile`可以是相對於目前目錄是不完整檔案名稱或完整限定。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `GetFile`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
 覆寫`dwContext`預設將內容識別碼設定為您選擇的值。 內容識別碼是與這個特定作業的相關聯`CFtpConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路第一個步驟︰ WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="openfile"></a>CFtpConnection::OpenFile  
 呼叫此成員函式，來開啟檔案進行讀取或寫入 FTP 伺服器上。  
  
```  
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,  
    DWORD dwAccess = GENERIC_READ,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pstrFileName`  
 包含要開啟的檔案名稱的字串指標。  
  
 *dwAccess*  
 決定如何存取檔案。 可以是 GENERIC_READ 或 GENERIC_WRITE，但非兩者。  
  
 `dwFlags`  
 指定的條件下進行後續的傳輸。 這可以是任何下列 FTP_TRANSFER_ * 常數︰  
  
-   FTP_TRANSFER_TYPE_ASCII 檔案傳輸使用 FTP ASCII （型別 A） 傳輸方法。 將控制項和格式設定資訊給本機對等項目。  
  
-   FTP_TRANSFER_TYPE_BINARY 檔案傳輸使用 FTP's 映像 (類型 I) 傳輸方法。 完全相同的檔案傳輸資料存在，而不需變更。 這是預設的傳輸方法。  
  
 `dwContext`  
 開啟檔案的內容識別碼。 請參閱**備註**如需詳細資訊`dwContext`。  
  
### <a name="return-value"></a>傳回值  
 指標[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件。  
  
### <a name="remarks"></a>備註  
 `OpenFile`應在下列情況︰  
  
-   應用程式有需要傳送和建立成檔案的 FTP 伺服器上，但是該資料不是本機檔案中的資料。 一次`OpenFile`會開啟檔案時，應用程式會使用[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) FTP 檔案資料傳送到伺服器。  
  
-   應用程式必須從伺服器擷取檔案，並將它放入應用程式所控制的記憶體，而不是寫入至磁碟。 應用程式使用[CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read)之後使用`OpenFile`來開啟檔案。  
  
-   應用程式所需檔案傳輸的控制層的級。 例如，應用程式可能會想要顯示進度控制項下載檔案時指出進度的檔案傳輸狀態。  
  
 在呼叫`OpenFile`，直到呼叫**CInternetConnection::Close**，應用程式可以只呼叫[CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read)， [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)， **CInternetConnection::Close**，或[cftpfilefind:: Findfile](../../mfc/reference/cftpfilefind-class.md#findfile)。 相同的 FTP 工作階段的其他 FTP 函式的呼叫會失敗，且設 FTP_ETRANSFER_IN_PROGRESS 錯誤碼。  
  
 `pstrFileName`參數可以是任一個不完整檔名為目前的目錄的相對或完整。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `OpenFile`然後再將它轉譯為適當的字元的目錄名稱分隔符號。  
  
 覆寫`dwContext`預設將內容識別碼設定為您選擇的值。 內容識別碼是與這個特定作業的相關聯`CFtpConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路第一個步驟︰ WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="putfile"></a>CFtpConnection::PutFile  
 呼叫此成員函式，來儲存 FTP 伺服器上的檔案。  
  
```  
BOOL PutFile(
    LPCTSTR pstrLocalFile,  
    LPCTSTR pstrRemoteFile,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pstrLocalFile`  
 包含要從本機系統傳送的檔案名稱的字串指標。  
  
 `pstrRemoteFile`  
 包含要在 FTP 伺服器上建立的檔案名稱的字串指標。  
  
 `dwFlags`  
 指定在其下的檔案傳輸就會發生的條件。 可以是任何 FTP_TRANSFER_ * 常數中所述[OpenFile](#openfile)。  
  
 `dwContext`  
 放置檔案的內容識別碼。 請參閱**備註**如需詳細資訊`dwContext`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `PutFile`是高階的常式來處理所有儲存在 FTP 伺服器上的檔案相關聯的作業。 應用程式，只會傳送資料，或需要仔細控制的檔案傳輸，應使用[OpenFile](#openfile)和[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)。  
  
 覆寫`dwContext`預設將內容識別碼設定為您選擇的值。 內容識別碼是與這個特定作業的相關聯`CFtpConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路第一個步驟︰ WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="remove"></a>Findfile  
 呼叫此成員函式，從連接的伺服器中刪除指定的檔案。  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>參數  
 `pstrFileName`  
 包含要移除的檔案名稱的字串指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `pstrFileName`參數可以是任一個不完整檔名為目前的目錄的相對或完整。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 **移除**函式在使用前會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="removedirectory"></a>CFtpConnection::RemoveDirectory  
 呼叫此成員函式，從連接的伺服器中移除指定的目錄。  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>參數  
 `pstrDirName`  
 指向的字串，包含要移除的目錄。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 使用[GetCurrentDirectory](#getcurrentdirectory)來判斷伺服器的目前工作目錄。 請勿假設遠端系統已連接您的根目錄。  
  
 `pstrDirName`參數可以是任一部分或完整完整的檔案名稱與目前的目錄。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `RemoveDirectory`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="rename"></a>CFtpConnection::Rename  
 呼叫此成員函式，若要重新命名連線的伺服器上指定的檔案。  
  
```  
BOOL Rename(
    LPCTSTR pstrExisting,  
    LPCTSTR pstrNew);
```  
  
### <a name="parameters"></a>參數  
 `pstrExisting`  
 包含要重新命名檔案的目前名稱的字串指標。  
  
 `pstrNew`  
 包含檔案的新名稱的字串指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `pstrExisting`和`pstrNew`參數可以是任一個不完整檔名為目前的目錄的相對或完整。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 **重新命名**在使用前會轉譯為適當的字元的目錄名稱分隔符號。  
  
##  <a name="setcurrentdirectory"></a>Cftpconnection:: Setcurrentdirectory  
 呼叫此成員函式來變更到 FTP 伺服器上的不同目錄。  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>參數  
 `pstrDirName`  
 包含的目錄名稱的字串指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `pstrDirName`參數可以是任一部分或完整完整的檔案名稱與目前的目錄。 反斜線 (\\) 或正斜線 （/） 可以當做是名稱的目錄分隔符號。 `SetCurrentDirectory`在使用前，會轉譯為適當的字元的目錄名稱分隔符號。  
  
 使用[GetCurrentDirectory](#getcurrentdirectory)判斷 FTP 伺服器的目前工作目錄。 請勿假設遠端系統已連接您的根目錄。  
  
## <a name="see-also"></a>另請參閱  
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)

