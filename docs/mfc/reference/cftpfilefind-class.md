---
title: CFtpFileFind 類別
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: e53e16f738f0436cbd02074c10ca24dbcc9d0fd8
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206228"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 類別

協助 FTP 伺服器的網際網路檔案搜尋。

## <a name="syntax"></a>語法

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CFtpFileFind：： CFtpFileFind](#cftpfilefind)|建構 `CFtpFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[CFtpFileFind：： FindFile](#findfile)|在 FTP 伺服器上尋找檔案。|
|[CFtpFileFind：： FindNextFile](#findnextfile)|繼續從先前的[FindFile](#findfile)呼叫進行檔案搜尋。|
|[CFtpFileFind：： GetFileURL](#getfileurl)|取得找到之檔案的 URL，包括路徑。|

## <a name="remarks"></a>備註

`CFtpFileFind`包含開始搜尋的成員函式、尋找檔案，以及傳回該檔案的 URL 或其他描述性資訊。

針對網際網路和本機檔案而設計的其他 MFC 類別，會包含[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 與搭配使用時 `CFtpFileFind` ，這些類別可提供順暢的機制，讓用戶端尋找特定檔案，而不論伺服器通訊協定或檔案類型（本機電腦或遠端伺服器）。 沒有任何 MFC 類別可用於在 HTTP 伺服器上進行搜尋，因為 HTTP 不支援搜尋所需的直接檔案操作。

如需如何使用 `CFtpFileFind` 和其他 WinInet 類別的詳細資訊，請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="example"></a>範例

下列程式碼示範如何列舉 FTP 伺服器目前目錄中的所有檔案。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>規格需求

**標頭：** afxinet.h。h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind：： CFtpFileFind

呼叫這個成員函式以建立 `CFtpFileFind` 物件。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pConnection*<br/>
`CFtpConnection` 物件的指標。 您可以藉由呼叫[CInternetSession：： GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)來取得 FTP 連接。

*dwCoNtext*<br/>
物件的內容識別碼 `CFtpFileFind` 。 如需詳細資訊，請參閱下列**備註**。

### <a name="remarks"></a>備註

*DwCoNtext*的預設值是由 MFC `CFtpFileFind` 從建立物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件傳送至物件 `CFtpFileFind` 。 您可以覆寫預設值，將內容識別碼設定為您所選擇的值。 內容識別碼會傳回給[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以在其識別的物件上提供狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

### <a name="example"></a>範例

  請參閱本主題稍早的類別總覽中的範例。

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind：： FindFile

呼叫這個成員函式以尋找 FTP 檔案。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>參數

*pstrName*<br/>
字串的指標，其中包含要尋找的檔案名。 如果是 Null，則呼叫會執行萬用字元搜尋（*）。

*dwFlags*<br/>
描述如何處理此會話的旗標。 這些旗標可以與位 OR 運算子（&#124;）結合，如下所示：

- `INTERNET_FLAG_RELOAD`即使是在本機快取，也會從網路取得資料。 這是預設旗標。

- `INTERNET_FLAG_DONT_CACHE`請勿在本機或任何閘道上快取資料。

- `INTERNET_FLAG_RAW_DATA`覆寫預設值，以傳回原始資料（FTP 的[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構）。

- `INTERNET_FLAG_SECURE`使用安全通訊端層或 PCT 來保護網路上的交易。 此旗標僅適用于 HTTP 要求。

- `INTERNET_FLAG_EXISTING_CONNECT`可能的話，請針對新的要求重複使用伺服器的現有連線， `FindFile` 而不是針對每個要求建立新的會話。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊，請呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

呼叫 `FindFile` 來抓取第一個 ftp 檔案之後，您可以呼叫[FindNextFile](#findnextfile)來取出後續的 ftp 檔案。

### <a name="example"></a>範例

  請參閱本主題中的先前範例。

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind：： FindNextFile

呼叫這個成員函式，以使用[FindFile](#findfile)成員函式的呼叫來繼續執行檔案搜尋。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果有多個檔案，則為非零值;如果找到的檔案是目錄中的最後一個檔案，或如果發生錯誤，則為零。 若要取得延伸錯誤資訊，請呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔案是目錄中的最後一個檔案，或如果找不到相符的檔案，則函式會傳回 `GetLastError` ERROR_NO_MORE_FILES。

### <a name="remarks"></a>備註

呼叫任何屬性函數之前，您至少必須呼叫此函式一次（請參閱[CFileFind：： FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)）。

`FindNextFile`包裝 Win32 函數[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>範例

  請參閱本主題稍早的範例。

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind：： GetFileURL

呼叫這個成員函式以取得指定檔案的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

通用資源定位器（URL）的檔案和路徑。

### <a name="remarks"></a>備註

`GetFileURL`類似于成員函式[CFileFind：： GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) ，不同之處在于它會以 URL 格式提供結果。 如同 `CFileFind::GetFilePath` ，結果不包含檔案名。 例如， `file1.txt` 位於中的會傳回 `//moose/dir/file1.txt:` `ftp://moose/dir/` 。

## <a name="see-also"></a>另請參閱

[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
