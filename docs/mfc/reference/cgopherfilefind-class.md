---
title: CGopherFileFind 類別
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418577"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 類別

協助網際網路檔案搜尋 Gopher 伺服器。

> [!NOTE]
>  類別 `CGopherConnection`、`CGopherFile`、`CGopherFileFind`、`CGopherLocator` 及其成員已被取代，因為它們無法在 Windows XP 平臺上執行，但它們仍可在舊版平臺上繼續工作。

## <a name="syntax"></a>語法

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGopherFileFind：： CGopherFileFind](#cgopherfilefind)|建構 `CGopherFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGopherFileFind：： FindFile](#findfile)|在 Gopher 伺服器上尋找檔案。|
|[CGopherFileFind：： FindNextFile](#findnextfile)|繼續從先前的[FindFile](#findfile)呼叫進行檔案搜尋。|
|[CGopherFileFind：： GetCreationTime](#getcreationtime)|取得指定檔案的建立時間。|
|[CGopherFileFind：： GetLastAccessTime](#getlastaccesstime)|取得指定檔案上次被存取的時間。|
|[CGopherFileFind：： GetLastWriteTime](#getlastwritetime)|取得指定檔案上次被寫入的時間。|
|[CGopherFileFind：： GetLength](#getlength)|取得找到之檔案的長度（以位元組為單位）。|
|[CGopherFileFind：： GetLocator](#getlocator)|取得 `CGopherLocator` 物件。|
|[CGopherFileFind：： GetScreenName](#getscreenname)|取得 gopher 螢幕的名稱。|
|[CGopherFileFind：： IsDots](#isdots)|測試目前目錄和父目錄標記，同時逐一查看檔案。|

## <a name="remarks"></a>備註

`CGopherFileFind` 包含開始搜尋的成員函式、尋找檔案，並傳回檔案的 URL。

針對網際網路和本機檔案而設計的其他 MFC 類別，會包含[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 除了 `CGopherFileFind`，這些類別也提供順暢的機制，讓使用者尋找特定檔案，而不論伺服器通訊協定、檔案類型或位置（本機電腦或遠端伺服器）。請注意，沒有任何 MFC 類別可用於在 HTTP 伺服器上進行搜尋，因為 HTTP 不支援搜尋所需的直接檔案操作。

> [!NOTE]
> `CGopherFileFind` 不支援其基類[CFileFind](../../mfc/reference/cfilefind-class.md)的下列成員函式：

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

此外，與 `CGopherFileFind`搭配使用時，`CFileFind` 成員函式[IsDots](../../mfc/reference/cfilefind-class.md#isdots)一律為 FALSE。

如需如何使用 `CGopherFileFind` 和其他 WinInet 類別的詳細資訊，請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>需求

**標頭：** afxinet.h。h

##  <a name="cgopherfilefind"></a>CGopherFileFind：： CGopherFileFind

呼叫這個成員函式來建立 `CGopherFileFind` 物件。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pConnection*<br/>
[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件的指標。

*dwCoNtext*<br/>
作業的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱**備註**。

### <a name="remarks"></a>備註

從建立 `CGopherFileFind` 物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件，MFC 會將*dwCoNtext*的預設值傳送至 `CGopherFileFind` 物件。 當您建立 `CGopherFileFind` 物件時，您可以覆寫預設值，將內容識別碼設定為您所選擇的值。 內容識別碼會傳回給[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以在其識別所在的物件上提供狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

##  <a name="findfile"></a>CGopherFileFind：： FindFile

呼叫這個成員函式以尋找 gopher 檔案。

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>參數

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件的參考。

*pstrString*<br/>
包含檔案名之字串的指標。

*dwFlags*<br/>
描述如何處理此會話的旗標。 有效的旗標如下：

- INTERNET_FLAG_RELOAD 從遠端伺服器取得資料，即使它是在本機快取的。

- INTERNET_FLAG_DONT_CACHE 不會在本機或任何閘道上快取資料。

- INTERNET_FLAG_SECURE 以安全通訊端層或 PCT 要求網路上的安全交易。 此旗標僅適用于 HTTP 要求。

- INTERNET_FLAG_USE_EXISTING 可能的話，請針對新的 `FindFile` 要求重複使用伺服器的現有連線，而不是針對每個要求建立新的會話。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊，請呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

呼叫 `FindFile` 來抓取第一個 gopher 物件之後，您可以呼叫[FindNextFile](#findnextfile)來取出後續的 gopher 檔案。

##  <a name="findnextfile"></a>CGopherFileFind：： FindNextFile

呼叫此成員函式，以在呼叫[CGopherFileFind：： FindFile](#findfile)的情況下繼續進行檔案搜尋。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果有多個檔案，則為非零值;如果找到的檔案是目錄中的最後一個檔案，或如果發生錯誤，則為零。 若要取得延伸錯誤資訊，請呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔案是目錄中的最後一個檔案，或如果找不到相符的檔案，則 `GetLastError` 函式會傳回 ERROR_NO_MORE_FILES。

##  <a name="getcreationtime"></a>CGopherFileFind：： GetCreationTime

取得目前檔案的建立時間。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標，其中包含建立檔案的時間。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

### <a name="return-value"></a>傳回值

如果成功，則為非零;如果失敗，則為0。 只有在這個 `CGopherFileFind` 物件上從未呼叫過[FindNextFile](#findnextfile)時，`GetCreationTime` 才會傳回0。

### <a name="remarks"></a>備註

呼叫 `GetCreationTime`之前，您至少必須呼叫一次[FindNextFile](#findnextfile) 。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性，則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊，請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上，所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊，請參閱 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlastaccesstime"></a>CGopherFileFind：： GetLastAccessTime

取得指定檔案上次被存取的時間。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>參數

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

*pTimeStamp*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標，其中包含上次存取檔案的時間。

### <a name="return-value"></a>傳回值

如果成功，則為非零;如果失敗，則為0。 只有在這個 `CGopherFileFind` 物件上從未呼叫過[FindNextFile](#findnextfile)時，`GetLastAccessTime` 才會傳回0。

### <a name="remarks"></a>備註

呼叫 `GetLastAccessTime`之前，您至少必須呼叫一次[FindNextFile](#findnextfile) 。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性，則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊，請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上，所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊，請參閱 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlastwritetime"></a>CGopherFileFind：： GetLastWriteTime

取得上次變更檔案的時間。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標，其中包含檔案上次被寫入的時間。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

### <a name="return-value"></a>傳回值

如果成功，則為非零;如果失敗，則為0。 只有在這個 `CGopherFileFind` 物件上從未呼叫過[FindNextFile](#findnextfile)時，`GetLastWriteTime` 才會傳回0。

### <a name="remarks"></a>備註

呼叫 `GetLastWriteTime`之前，您至少必須呼叫一次[FindNextFile](#findnextfile) 。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性，則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊，請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上，所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊，請參閱 Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

##  <a name="getlength"></a>CGopherFileFind：： GetLength

呼叫這個成員函式可取得找到檔案的長度（以位元組為單位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

找到之檔案的長度（以位元組為單位）。

### <a name="remarks"></a>備註

`GetLength` 使用 Win32 結構[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)取得檔案大小的值（以位元組為單位）。

> [!NOTE]
>  從 MFC 7.0，`GetLength` 支援64位整數類型。 先前的現有程式碼（使用這個較新版本的程式庫所建立）可能會導致截斷警告。

### <a name="example"></a>範例

  請參閱[CFile：： GetLength](../../mfc/reference/cfile-class.md#getlength)的範例（基類實作為）。

##  <a name="getlocator"></a>CGopherFileFind：： GetLocator

呼叫這個成員函式，以取得[FindFile](#findfile)用來尋找 gopher 檔案的[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>傳回值

`CGopherLocator` 物件。

##  <a name="getscreenname"></a>CGopherFileFind：： GetScreenName

呼叫這個成員函式以取得 gopher 螢幕的名稱。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>傳回值

Gopher 螢幕的名稱。

##  <a name="isdots"></a>CGopherFileFind：： IsDots

測試目前目錄和父目錄標記，同時逐一查看檔案。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>傳回值

如果找到的檔案名稱為 "." 或 "..."，則為非零，表示找到的檔案實際上是目錄。 否則為 0。

### <a name="remarks"></a>備註

呼叫 `IsDots`之前，您至少必須呼叫一次[FindNextFile](#findnextfile) 。

## <a name="see-also"></a>另請參閱

[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 類別](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
