---
title: CFtpConnection 類別
ms.date: 08/29/2019
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
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373768"
---
# <a name="cftpconnection-class"></a>CFtpConnection 類別

管理與 Internet 伺服器的 FTP 連接,並允許直接操作該伺服器上的目錄和檔。

## <a name="syntax"></a>語法

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFtp 連線::CFtp 連接](#cftpconnection)|建構 `CFtpConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFtp 連線::指令](#command)|將命令直接傳送至 FTP 伺服器。|
|[CFtp 連線:建立目錄](#createdirectory)|在伺服器上創建目錄。|
|[CFtp 連線::取得目前的目錄](#getcurrentdirectory)|獲取此連接的當前目錄。|
|[CFtp 連線::取得目前的目錄](#getcurrentdirectoryasurl)|取得此連線的目前目錄作為 URL。|
|[CFtp 連線:抓取檔案](#getfile)|從連線的伺服器抓取檔案|
|[CFtp 連線::開啟檔案](#openfile)|在連接的伺服器上打開檔。|
|[CFtp 連接::PutFile](#putfile)|將檔放在伺服器上。|
|[CFtp 連線::刪除](#remove)|從伺服器中刪除檔。|
|[CFtp 連線::刪除目錄](#removedirectory)|從伺服器中刪除指定的目錄。|
|[CFtp 連線:重新命名](#rename)|重新命名伺服器上的檔案。|
|[CFtp 連線::設定目前的目錄](#setcurrentdirectory)|設置當前 FTP 目錄。|

## <a name="remarks"></a>備註

FTP 是 MFC WinInet 類認可的三大互聯網服務之一。

要與 FTP Internet 伺服器通訊,必須首先建立[CInternetSession](../../mfc/reference/cinternetsession-class.md)的`CFtpConnection`實例,然後創建 物件。 您從不直接創建`CFtpConnection`物件;相反,調用[CInternetSession::GetFtpConnect](../../mfc/reference/cinternetsession-class.md#getftpconnection)`CFtpConnection`,它 創建物件並返回指向它的指標。

要瞭解有關如何`CFtpConnection`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。 有關與其他兩個受支援的服務 HTTP 和 gopher 通信的詳細資訊,請參閱[CHTTPConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)的類。

## <a name="example"></a>範例

  請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)類概述中的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtp 連線::CFtp 連接

呼叫此成員函數以建構物件`CFtpConnection`。

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

*p 工作階段*<br/>
指向相關[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*h 連線*<br/>
當前 Internet 作業階段的 Windows 句柄。

*pstrServer*<br/>
指向包含 FTP 伺服器名稱的字串的指標。

*dwContext*<br/>
操作的上下文標識碼。 *dwContext*識別 CInternetSession 傳回的作業的狀態資訊[::onStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 預設值設定為 1;將預設值設定為 1但是,您可以顯式為操作分配特定的上下文 ID。 物件及其執行的任何工作都將與該上下文 ID 相關聯。

*pstrUser 名稱*<br/>
指向 null 終止字串的指標,該字串指定要登錄的使用者的名稱。 如果為 NULL,則預設值為匿名。

*pstr密碼*<br/>
指向 null 終止字串的指標,用於指定用於登入的密碼。 如果*pstrPassword*和*pstrUserName*均為 NULL,則預設的匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*為 NULL(或空字串),但*pstrUserName*不是 NULL,則使用空白密碼。 下表描述了*pstrUserName*和*pstrPassword*的四種可能設定的行為:

|*pstrUser 名稱*|*pstr密碼*|傳送 FTP 伺服器的使用者名稱|傳送 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|使用者的電子郵件名稱|
|NULL 字串|NULL 或""|*pstrUser 名稱*|" "|
|NULL 非 NULL 字串|ERROR|ERROR||
|NULL 字串|NULL 字串|*pstrUser 名稱*|*pstr密碼*|

*n波特*<br/>
標識要在伺服器上使用的 TCP/IP 連接埠的數位。

*b被動*<br/>
為此 FTP 會話指定被動或主動模式。 如果設置為 TRUE,它將 Win32 API *dwFlag*設置為INTERNET_FLAG_PASSIVE。

### <a name="remarks"></a>備註

您從不直接創建`CFtpConnection`物件。 相反,調用[CInternetSession::GetFtpConnect](../../mfc/reference/cinternetsession-class.md#getftpconnection),`CFptConnection`這將 創建物件。

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtp 連線::指令

將命令直接傳送至 FTP 伺服器。

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pszCommand*<br/>
包含要傳送至命令的字串指標。

*eResponse*<br/>
指定是否預期來自 FTP 伺服器的回應。 可以是下列其中一個值：

- `CmdRespNone`預期不會回應。
- `CmdRespRead`預期會做出回應。
- `CmdRespWrite`未使用。

CmdResponseType 是 CFtpConnection 的成員,在*afxinet.h*中定義。

*dwFlags*<br/>
一個值，包含控制此函式的旗標。 有關完整清單,請參閱[FTP 命令](/windows/win32/api/wininet/nf-wininet-ftpcommandw)。

*dwContext*<br/>
值的指標，包含應用程式定義的值，用以識別回呼中的應用程式內容。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數類比[FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)函數的功能,如 Windows SDK 中所述。

如果發生錯誤,MFC將引發[CInternetException](../../mfc/reference/cinternetexception-class.md)類型的異常。

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtp 連線:建立目錄

呼叫此成員函數在連接的伺服器上創建目錄。

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*普斯特迪爾名稱*<br/>
指向包含要建立的目錄名稱的字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Windows 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

用於`GetCurrentDirectory`確定此連接到伺服器的當前工作目錄。 不要假定遠端系統已將您連接到根目錄。

參數`pstrDirName`可以是相對於當前目錄的部分或完全限定的檔名。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `CreateDirectory`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtp 連線::取得目前的目錄

呼叫此成員函數以獲取當前目錄的名稱。

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>參數

*斯特迪爾名稱*<br/>
對將接收目錄名稱的字串的引用。

*普斯特迪爾名稱*<br/>
指向將接收目錄名稱的字串的指標。

*lpdwLen*<br/>
指向包含以下資訊的 DWORD 的指標:

|||
|-|-|
|入場時|*pstrDirName*引用的緩衝區的大小。|
|返回時|儲存到*pstrDirName*的字元數。 如果成員函數失敗並返回ERROR_INSUFFICIENT_BUFFER,則*lpdwLen*包含應用程式必須分配的位元組數才能接收字串。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

要將目錄名稱作為網址,請呼叫[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。

參數*pstrDirName*或*strDirName*可以是相對於目前的目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `GetCurrentDirectory`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtp 連線::取得目前的目錄

呼叫此成員函數以獲取當前目錄的名稱作為網址。

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>參數

*斯特迪爾名稱*<br/>
對將接收目錄名稱的字串的引用。

*普斯特迪爾名稱*<br/>
指向將接收目錄名稱的字串的指標。

*lpdwLen*<br/>
指向包含以下資訊的 DWORD 的指標:

|||
|-|-|
|入場時|*pstrDirName*引用的緩衝區的大小。|
|返回時|儲存到*pstrDirName*的字元數。 如果成員函數失敗並返回ERROR_INSUFFICIENT_BUFFER,則*lpdwLen*包含應用程式必須分配的位元組數才能接收字串。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

`GetCurrentDirectoryAsURL`產生與[GetCurrentDirectory](#getcurrentdirectory)相同

參數*strDirName*可以是相對於當前目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `GetCurrentDirectoryAsURL`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtp 連線:抓取檔案

呼叫此成員函數從 FTP 伺服器獲取檔案並將其儲存在本地電腦上。

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

*pstrRemoteFile*<br/>
指向從 FTP 伺服器檢索的檔名稱的 null 連接端接字串的指標。

*pstrlocalFile*<br/>
指向在本地系統上建立的檔案名稱的 null 端結束的字串的指標。

*bFailIf 存在*<br/>
指示現有檔是否已經使用檔名。 如果本地檔名已存在,並且此參數為 TRUE,`GetFile`則失敗。 否則,`GetFile`將擦除檔的現有副本。

*dwAttributes*<br/>
指示檔的屬性。 這可以是以下FILE_ATTRIBUTE_* 標誌的任意組合。

- FILE_ATTRIBUTE_ARCHIVE 該檔是存檔檔。 應用程式使用此屬性標記檔以進行備份或刪除。

- FILE_ATTRIBUTE_COMPRESSED檔或目錄被壓縮。 對於檔,壓縮意味著檔中的所有數據被壓縮。 對於目錄,壓縮是新創建的檔和子目錄的預設值。

- FILE_ATTRIBUTE_DIRECTORY 該檔是目錄。

- FILE_ATTRIBUTE_NORMAL 該檔沒有其他屬性集。 此屬性僅在單獨使用時有效。 所有其他檔案屬性將覆寫FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN檔案已隱藏。 它不包含在普通目錄清單中。

- FILE_ATTRIBUTE_READONLY該檔是唯讀的。 應用程式可以讀取檔,但不能寫入或刪除該檔。

- FILE_ATTRIBUTE_SYSTEM 該檔是 操作系統的一部分或由操作系統專門使用。

- FILE_ATTRIBUTE_TEMPORARY 該檔用於臨時存儲。 應用程式僅在絕對必要時才應寫入檔。 檔的大部分數據保留在記憶體中,而不會刷新到介質,因為該檔將很快被刪除。

*dwFlags*<br/>
指定傳輸發生的條件。 此參數可以是 Windows SDK 中[FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew)中描述的任何*dwFlags*值。

*dwContext*<br/>
檔檢索的上下文標識符。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

`GetFile`是一種高級例程,用於處理與從 FTP 伺服器讀取檔並在本地存儲檔案相關的所有開銷。 只取得檔案資料或需要嚴格控制檔案傳輸的應用程式應使用`OpenFile` [CInternetFile::改為讀取](../../mfc/reference/cinternetfile-class.md#read)。

如果*dwFlags* FILE_TRANSFER_TYPE_ASCII,則文件數據的轉換也會將控制項和格式字元轉換為 Windows 等效項。 默認傳輸是二進位模式,其中檔案下載的格式與儲存在伺服器上的格式相同。

*pstrRemoteFile*和*pstrLocalFile*都可以是相對於當前目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `GetFile`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

覆寫*dwContext*預設值,將上下文識別子設定為您選擇的值。 上下文識別碼`CFtpConnection`[與其 CInternetSession](../../mfc/reference/cinternetsession-class.md)對象創建的物件的此特定操作相關聯。 該值將返回到[CInternetSession::onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供標識該值的操作的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtp 連線::開啟檔案

呼叫此成員函數打開位於 FTP 伺服器上的檔以進行讀取或寫入。

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pstrFile 名稱*<br/>
指向包含要打開的檔案名稱的字串的指標。

*dwAccess*<br/>
確定如何訪問該檔。 可以是GENERIC_READ或GENERIC_WRITE,但不能同時使用這兩者。

*dwFlags*<br/>
指定後續傳輸發生的條件。 這可以是以下任何FTP_TRANSFER_* 常量:

- FTP_TRANSFER_TYPE_ASCII使用 FTP ASCII (類型 A) 傳輸方法傳輸檔。 將控制項和格式資訊轉換為本地等效項。

- FTP_TRANSFER_TYPE_BINARY檔使用 FTP 的圖像(類型 I)傳輸方法傳輸數據。 檔案傳輸數據完全與它存在一樣,沒有更改。 這是默認傳輸方法。

*dwContext*<br/>
用於打開檔的上下文標識符。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="return-value"></a>傳回值

指向[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件的指標。

### <a name="remarks"></a>備註

`OpenFile`應在以下情況下使用:

- 應用程式的數據需要作為 FTP 伺服器上的檔發送和創建,但該數據不在本地檔中。 打開`OpenFile`檔案後,應用程式將使用[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)將 FTP 檔案資料發送到伺服器。

- 應用程式必須從伺服器檢索檔並將其放入應用程式控制的記憶體中,而不是將其寫入磁碟。 應用程式使用[CInternetFile:使用後讀取](../../mfc/reference/cinternetfile-class.md#read)`OpenFile`以打開檔。

- 應用程式需要對文件傳輸進行精細級別的控制。 例如,應用程式可能想要顯示進度控制,指示檔案傳輸狀態在下載檔時的進度。

`OpenFile`呼叫後,直到呼叫`CInternetConnection::Close`, 應用程式只能呼叫[CInternetFile::讀取](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::寫入](../../mfc/reference/cinternetfile-class.md#write),`CInternetConnection::Close`或[CFtpFile 尋找::尋找檔案](../../mfc/reference/cftpfilefind-class.md#findfile)。 對同一 FTP 會話的其他 FTP 函數的調用將失敗,並將錯誤代碼設置為FTP_ETRANSFER_IN_PROGRESS。

*pstrFileName*參數可以是相對於當前目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `OpenFile`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

覆寫*dwContext*預設值,將上下文識別子設定為您選擇的值。 上下文識別碼`CFtpConnection`[與其 CInternetSession](../../mfc/reference/cinternetsession-class.md)對象創建的物件的此特定操作相關聯。 該值將返回到[CInternetSession::onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供標識該值的操作的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtp 連接::PutFile

調用此成員函數以在 FTP 伺服器上儲存檔。

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pstrlocalFile*<br/>
指向從本地系統發送的檔案名稱的字串的指標。

*pstrRemoteFile*<br/>
指向在 FTP 伺服器上建立的檔案名稱的字串的指標。

*dwFlags*<br/>
指定檔案傳輸的條件。 可以是[OpenFile](#openfile)中描述的任何FTP_TRANSFER_* 常量。

*dwContext*<br/>
放置檔的上下文標識碼。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

`PutFile`是一種高級例程,用於處理與在 FTP 伺服器上存儲檔關聯的所有操作。 只送出資料或需要更密切地控制檔案傳輸的應用程式應使用[OpenFile](#openfile)和[CInternetFile::write](../../mfc/reference/cinternetfile-class.md#write)。

覆蓋`dwContext`預設值,將上下文識別碼設定為您選擇的值。 上下文識別碼`CFtpConnection`[與其 CInternetSession](../../mfc/reference/cinternetsession-class.md)對象創建的物件的此特定操作相關聯。 該值將返回到[CInternetSession::onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供標識該值的操作的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtp 連線::刪除

呼叫此成員函數從連接的伺服器中刪除指定的檔案。

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>參數

*pstrFile 名稱*<br/>
指向要刪除的檔名的字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

*pstrFileName*參數可以是相對於當前目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 函數`Remove`在使用目錄名稱分隔符之前將其轉換為相應的字元。

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtp 連線::刪除目錄

呼叫此成員函數從連接的伺服器中刪除指定的目錄。

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*普斯特迪爾名稱*<br/>
指向包含要刪除的目錄的字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

使用[GetCurrentDirectory](#getcurrentdirectory)確定伺服器的當前工作目錄。 不要假定遠端系統已將您連接到根目錄。

*pstrDirName*參數可以是相對於當前目錄的部分或完全限定的檔名。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `RemoveDirectory`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtp 連線:重新命名

呼叫此成員函數重新命名連接的伺服器上的指定檔。

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>參數

*普斯特存在*<br/>
指向要重新命名的檔案的目前的名稱的字串的指標。

*普斯特新*<br/>
指向包含檔新名稱的字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

*pstr存在*和*pstrNew*參數可以是相對於當前目錄的部分限定檔名,也可以是完全限定的。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `Rename`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtp 連線::設定目前的目錄

呼叫此成員函數以更改為 FTP 伺服器上的不同目錄。

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*普斯特迪爾名稱*<br/>
指向包含目錄名稱的字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

*pstrDirName*參數可以是相對於當前目錄的部分或完全限定的檔名。 反斜杠\\( ) 或正向斜杠 (/) 可用作任一名稱的目錄分隔符。 `SetCurrentDirectory`在使用目錄名稱分隔符之前,將其轉換為相應的字元。

使用[GetCurrentDirectory](#getcurrentdirectory)確定 FTP 伺服器的當前工作目錄。 不要假定遠端系統已將您連接到根目錄。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
