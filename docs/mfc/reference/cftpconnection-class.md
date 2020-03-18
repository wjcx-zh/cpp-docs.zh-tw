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
ms.openlocfilehash: 94ee4cb938ee061470282eb2f08a94d83c908805
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418570"
---
# <a name="cftpconnection-class"></a>CFtpConnection 類別

管理網際網路伺服器的 FTP 連線，並允許直接操作該伺服器上的目錄和檔案。

## <a name="syntax"></a>語法

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFtpConnection：： CFtpConnection](#cftpconnection)|建構 `CFtpConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFtpConnection：： Command](#command)|將命令直接傳送至 FTP 伺服器。|
|[CFtpConnection：： CreateDirectory](#createdirectory)|在伺服器上建立目錄。|
|[CFtpConnection：： GetCurrentDirectory](#getcurrentdirectory)|取得此連接的目前的目錄。|
|[CFtpConnection：： GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|取得此連接的目前目錄作為 URL。|
|[CFtpConnection：： GetFile](#getfile)|從連接的伺服器取得檔案|
|[CFtpConnection：： OpenFile](#openfile)|在連接的伺服器上開啟檔案。|
|[CFtpConnection：:P utFile](#putfile)|將檔案放在伺服器上。|
|[CFtpConnection：： Remove](#remove)|從伺服器中移除檔案。|
|[CFtpConnection：： RemoveDirectory](#removedirectory)|從伺服器中移除指定的目錄。|
|[CFtpConnection：： Rename](#rename)|重新命名伺服器上的檔案。|
|[CFtpConnection：： SetCurrentDirectory](#setcurrentdirectory)|設定目前的 FTP 目錄。|

## <a name="remarks"></a>備註

FTP 是 MFC WinInet 類別所識別的三種網際網路服務之一。

若要與 FTP 網際網路伺服器通訊，您必須先建立[CInternetSession](../../mfc/reference/cinternetsession-class.md)的實例，然後建立 `CFtpConnection` 物件。 您永遠不會直接建立 `CFtpConnection` 物件;相反地，請呼叫[CInternetSession：： GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，它會建立 `CFtpConnection` 物件，並傳回它的指標。

若要深入瞭解 `CFtpConnection` 如何與其他 MFC 網際網路類別搭配運作，請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。 如需與其他兩個支援的服務（HTTP 和 gopher）進行通訊的詳細資訊，請參閱類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。

## <a name="example"></a>範例

  請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)類別總覽中的範例。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>需求

**標頭：** afxinet.h。h

##  <a name="cftpconnection"></a>CFtpConnection：： CFtpConnection

呼叫這個成員函式來建立 `CFtpConnection` 物件。

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

*pSession*<br/>
相關[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*hConnected*<br/>
目前網際網路會話的 Windows 控制碼。

*pstrServer*<br/>
包含 FTP 伺服器名稱之字串的指標。

*dwCoNtext*<br/>
作業的內容識別碼。 *dwCoNtext*會識別[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)傳回的作業狀態資訊。 預設值設定為 1;不過，您可以明確地指派作業的特定內容識別碼。 物件及其執行的任何工作都會與該內容識別碼相關聯。

*pstrUserName*<br/>
以 null 結束的字串指標，指定要登入之使用者的名稱。 如果是 Null，則預設值為 anonymous。

*pstrPassword*<br/>
以 null 結束的字串指標，指定要用來登入的密碼。 如果*pstrPassword*和*PSTRUSERNAME*都是 Null，則預設的匿名密碼就是使用者的電子郵件名稱。 如果*pstrPassword*為 Null （或空字串），但*PSTRUSERNAME*不是 null，則會使用空白密碼。 下表描述*pstrUserName*和*pstrPassword*的四個可能設定的行為：

|*pstrUserName*|*pstrPassword*|傳送到 FTP 伺服器的使用者名稱|傳送到 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null 或 ""|Null 或 ""|匿名|使用者的電子郵件名稱|
|非 Null 字串|Null 或 ""|*pstrUserName*|" "|
|Null 非 Null 字串|ERROR|ERROR||
|非 Null 字串|非 Null 字串|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
識別要在伺服器上使用之 TCP/IP 通訊埠的數位。

*bPassive*<br/>
指定此 FTP 會話的被動或主動模式。 如果設定為 TRUE，它會將 WIN32 API *dwFlag*設定為 INTERNET_FLAG_PASSIVE。

### <a name="remarks"></a>備註

您永遠不會直接建立 `CFtpConnection` 物件。 相反地，請呼叫[CInternetSession：： GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)，它會建立 `CFptConnection` 物件。

##  <a name="command"></a>CFtpConnection：： Command

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

- `CmdRespNone` 不需要回應。
- `CmdRespRead` 預期的回應。
- 未使用 `CmdRespWrite`。

CmdResponseType 是 CFtpConnection 的成員，定義于*afxinet.h*中。

*dwFlags*<br/>
一個值，包含控制此函式的旗標。 如需完整清單，請參閱[FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)。

*dwCoNtext*<br/>
值的指標，包含應用程式定義的值，用以識別回呼中的應用程式內容。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會模擬[FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)函式的功能，如 Windows SDK 中所述。

如果發生錯誤，MFC 會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)類型的例外狀況。

##  <a name="createdirectory"></a>CFtpConnection：： CreateDirectory

呼叫這個成員函式，在連接的伺服器上建立目錄。

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*pstrDirName*<br/>
字串的指標，其中包含要建立的目錄名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，可能會呼叫 Windows 函式[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以判斷錯誤的原因。

### <a name="remarks"></a>備註

使用 `GetCurrentDirectory` 來判斷此伺服器連接的目前工作目錄。 不要假設遠端系統已將您連接到根目錄。

`pstrDirName` 參數可以是部分或相對於目前的目錄的完整檔案名。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `CreateDirectory` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="getcurrentdirectory"></a>CFtpConnection：： GetCurrentDirectory

呼叫這個成員函式以取得目前目錄的名稱。

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>參數

*strDirName*<br/>
將接收目錄名稱之字串的參考。

*pstrDirName*<br/>
將接收目錄名稱之字串的指標。

*lpdwLen*<br/>
DWORD 的指標，其中包含下列資訊：

|||
|-|-|
|進入時|*PstrDirName*所參考的緩衝區大小。|
|返回時|儲存至*pstrDirName*的字元數。 如果成員函式失敗並傳回 ERROR_INSUFFICIENT_BUFFER，則*lpdwLen*會包含應用程式必須配置才能接收字串的位元組數目。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

若要改為取得目錄名稱作為 URL，請呼叫[GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)。

*PstrDirName*或*strDirName*參數可以是相對於目前的目錄的部分限定檔案名或完整名稱。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `GetCurrentDirectory` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection：： GetCurrentDirectoryAsURL

呼叫這個成員函式以取得目前目錄的名稱做為 URL。

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>參數

*strDirName*<br/>
將接收目錄名稱之字串的參考。

*pstrDirName*<br/>
將接收目錄名稱之字串的指標。

*lpdwLen*<br/>
DWORD 的指標，其中包含下列資訊：

|||
|-|-|
|進入時|*PstrDirName*所參考的緩衝區大小。|
|返回時|儲存至*pstrDirName*的字元數。 如果成員函式失敗並傳回 ERROR_INSUFFICIENT_BUFFER，則*lpdwLen*會包含應用程式必須配置才能接收字串的位元組數目。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

`GetCurrentDirectoryAsURL` 的行為與[GetCurrentDirectory](#getcurrentdirectory)相同

參數*strDirName*可以是相對於目前目錄或完整格式的部分限定檔案名。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `GetCurrentDirectoryAsURL` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="getfile"></a>CFtpConnection：： GetFile

呼叫這個成員函式可從 FTP 伺服器取得檔案，並將它儲存在本機電腦上。

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
以 null 終止的字串指標，其中包含要從 FTP 伺服器取出的檔案名。

*pstrLocalFile*<br/>
以 null 終止的字串指標，其中包含要在本機系統上建立的檔案名。

*bFailIfExists*<br/>
指出現有檔案是否可能已經使用此檔案名。 如果本機檔案名已經存在，且此參數為 TRUE，`GetFile` 會失敗。 否則，`GetFile` 將會清除檔案的現有複本。

*dwAttributes*<br/>
表示檔案的屬性。 這可以是下列 FILE_ATTRIBUTE_ * 旗標的任意組合。

- FILE_ATTRIBUTE_ARCHIVE 檔案是封存檔案。 應用程式會使用此屬性來標示要備份或移除的檔案。

- FILE_ATTRIBUTE_COMPRESSED 檔案或目錄已壓縮。 針對檔案，壓縮表示檔案中的所有資料都是壓縮檔案。 針對目錄，新建立的檔案和子目錄的預設值為壓縮。

- FILE_ATTRIBUTE_DIRECTORY 檔案是目錄。

- FILE_ATTRIBUTE_NORMAL 檔案未設定其他屬性。 這個屬性只有在單獨使用時才有效。 所有其他的檔案屬性都會覆寫 FILE_ATTRIBUTE_NORMAL：

- FILE_ATTRIBUTE_HIDDEN 檔案已隱藏。 這不會包含在一般目錄清單中。

- FILE_ATTRIBUTE_READONLY 檔案是唯讀的。 應用程式可以讀取檔案，但無法寫入或刪除檔案。

- FILE_ATTRIBUTE_SYSTEM 檔案是的一部分，或僅供作業系統使用。

- FILE_ATTRIBUTE_TEMPORARY 檔案正用於暫存儲存體。 只有在絕對必要時，應用程式才應該寫入檔案。 大部分檔案的資料會保留在記憶體中，而不會排清到媒體，因為檔案很快就會遭到刪除。

*dwFlags*<br/>
指定發生傳輸的條件。 這個參數可以是 Windows SDK 的[FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew)中所述的任何*dwFlags*值。

*dwCoNtext*<br/>
檔案抓取的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

`GetFile` 是高階常式，它會處理與從 FTP 伺服器讀取檔案並將檔案儲存在本機的相關聯的所有額外負荷。 只抓取檔案資料或需要對檔案傳輸進行關閉控制的應用程式，應該改用 `OpenFile` 和[CInternetFile：： Read](../../mfc/reference/cinternetfile-class.md#read) 。

如果 FILE_TRANSFER_TYPE_ASCII *dwFlags* ，則檔案資料的轉譯也會將控制和格式化字元轉換成 Windows 對等專案。 預設傳輸是二進位模式，其下載檔案的格式與儲存在伺服器上的相同。

*PstrRemoteFile*和*pstrLocalFile*都可以是相對於目前的目錄的部分限定檔案名或完整名稱。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `GetFile` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

覆寫*dwCoNtext*預設值，將內容識別碼設定為您選擇的值。 內容識別碼會與[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件所建立之 `CFtpConnection` 物件的這個特定作業相關聯。 此值會傳回[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供所識別之作業的狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

##  <a name="openfile"></a>CFtpConnection：： OpenFile

呼叫這個成員函式可開啟位於 FTP 伺服器上的檔案，以供讀取或寫入。

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pstrFileName*<br/>
字串的指標，其中包含要開啟的檔案名。

*dwAccess*<br/>
決定如何存取檔案。 可以是 GENERIC_READ 或 GENERIC_WRITE，但不能同時是兩者。

*dwFlags*<br/>
指定後續傳輸發生的條件。 這可以是下列其中一個 FTP_TRANSFER_ * 常數：

- FTP_TRANSFER_TYPE_ASCII 使用 FTP ASCII （類型 A）傳輸方法的檔案傳輸。 將控制項和格式設定資訊轉換為本機對等專案。

- FTP_TRANSFER_TYPE_BINARY 檔案會使用 FTP 的 Image （類型 I）傳輸方法來傳輸資料。 檔案會以完全相同的方式傳輸資料，而不會有任何變更。 這是預設的傳輸方法。

*dwCoNtext*<br/>
用來開啟檔案的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱**備註**。

### <a name="return-value"></a>傳回值

[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件的指標。

### <a name="remarks"></a>備註

`OpenFile` 應該用於下列情況：

- 應用程式的資料必須以 FTP 伺服器上的檔案的形式傳送和建立，但該資料不在本機檔案中。 一旦 `OpenFile` 開啟檔案，應用程式就會使用[CInternetFile：： Write](../../mfc/reference/cinternetfile-class.md#write)將 FTP 檔案資料傳送至伺服器。

- 應用程式必須從伺服器抓取檔案，並將它放入應用程式控制的記憶體中，而不是將它寫入磁片。 應用程式會在使用 `OpenFile` 開啟檔案之後，使用[CInternetFile：： Read](../../mfc/reference/cinternetfile-class.md#read) 。

- 應用程式需要對檔案傳輸進行精細的控制層級。 例如，應用程式可能會想要顯示進度控制項，指出下載檔案時檔案傳輸狀態的進度。

呼叫 `OpenFile` 並直到呼叫 `CInternetConnection::Close`之後，應用程式只能呼叫[CInternetFile：： Read](../../mfc/reference/cinternetfile-class.md#read)、 [CInternetFile：： Write](../../mfc/reference/cinternetfile-class.md#write)、`CInternetConnection::Close`或[CFtpFileFind：： FindFile](../../mfc/reference/cftpfilefind-class.md#findfile)。 相同 FTP 會話的其他 FTP 函數呼叫將會失敗，並將錯誤碼設定為 FTP_ETRANSFER_IN_PROGRESS。

*PstrFileName*參數可以是相對於目前的目錄的部分限定檔案名，或是完整的。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `OpenFile` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

覆寫*dwCoNtext*預設值，將內容識別碼設定為您選擇的值。 內容識別碼會與[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件所建立之 `CFtpConnection` 物件的這個特定作業相關聯。 此值會傳回[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供所識別之作業的狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

##  <a name="putfile"></a>CFtpConnection：:P utFile

呼叫這個成員函式，將檔案儲存在 FTP 伺服器上。

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pstrLocalFile*<br/>
字串的指標，包含要從本機系統傳送的檔案名。

*pstrRemoteFile*<br/>
字串的指標，其中包含要在 FTP 伺服器上建立的檔案名。

*dwFlags*<br/>
指定發生檔案傳輸的條件。 可以是[OpenFile](#openfile)中所述的任何 FTP_TRANSFER_ * 常數。

*dwCoNtext*<br/>
用於放置檔案的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

`PutFile` 是高階常式，它會處理與在 FTP 伺服器上儲存檔案相關聯的所有作業。 只傳送資料或需要更進一步控制檔案傳輸的應用程式，應該使用[OpenFile](#openfile)和[CInternetFile：： Write](../../mfc/reference/cinternetfile-class.md#write)。

覆寫 `dwContext` 預設值，將內容識別碼設定為您所選擇的值。 內容識別碼會與[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件所建立之 `CFtpConnection` 物件的這個特定作業相關聯。 此值會傳回[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供所識別之作業的狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

##  <a name="remove"></a>CFtpConnection：： Remove

呼叫這個成員函式，從連接的伺服器刪除指定的檔案。

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>參數

*pstrFileName*<br/>
包含要移除之檔案名的字串指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

*PstrFileName*參數可以是相對於目前的目錄的部分限定檔案名，或是完整的。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `Remove` 函式會在使用之前，將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="removedirectory"></a>CFtpConnection：： RemoveDirectory

呼叫這個成員函式，從連接的伺服器中移除指定的目錄。

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*pstrDirName*<br/>
包含要移除之目錄的字串指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

使用[GetCurrentDirectory](#getcurrentdirectory)來判斷伺服器目前的工作目錄。 不要假設遠端系統已將您連接到根目錄。

*PstrDirName*參數可以是相對於目前的目錄的部分或完整檔案名。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `RemoveDirectory` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="rename"></a>CFtpConnection：： Rename

呼叫這個成員函式，在連接的伺服器上重新命名指定的檔案。

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>參數

*pstrExisting*<br/>
字串的指標，其中包含要重新命名之檔案的目前名稱。

*pstrNew*<br/>
包含檔案新名稱之字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

*PstrExisting*和*pstrNew*參數可以是相對於目前目錄或完整格式的部分限定檔案名。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `Rename` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

##  <a name="setcurrentdirectory"></a>CFtpConnection：： SetCurrentDirectory

呼叫這個成員函式，以變更至 FTP 伺服器上的不同目錄。

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>參數

*pstrDirName*<br/>
包含目錄名稱之字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

*PstrDirName*參數可以是相對於目前的目錄的部分或完整檔案名。 您可以使用反斜線（\\）或斜線（/）做為任一名稱的目錄分隔符號。 `SetCurrentDirectory` 在使用之前，會將目錄名稱分隔符號轉譯為適當的字元。

使用[GetCurrentDirectory](#getcurrentdirectory)來判斷 FTP 伺服器目前的工作目錄。 不要假設遠端系統已將您連接到根目錄。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
