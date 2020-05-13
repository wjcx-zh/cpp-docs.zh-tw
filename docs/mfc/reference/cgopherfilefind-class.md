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
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373685"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 類別

協助網際網路檔案搜尋 Gopher 伺服器。

> [!NOTE]
> 類`CGopherConnection``CGopherFile` `CGopherFileFind`、`CGopherLocator`、 及其成員已被棄用,因為它們在 Windows XP 平臺上不工作,但它們將繼續在較早的平臺上工作。

## <a name="syntax"></a>語法

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGopher檔案查找::CGopher檔查找](#cgopherfilefind)|建構 `CGopherFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGopher 檔案尋找:尋找檔案](#findfile)|在 gopher 伺服器上查找檔。|
|[CGopher檔案查找::尋找下一個檔案](#findnextfile)|繼續從上一個調用[FindFile](#findfile)的檔搜索。|
|[CGopher 檔案尋找:取得創造時間](#getcreationtime)|獲取創建指定檔案的時間。|
|[CGopher 檔案尋找:抓取最後存取時間](#getlastaccesstime)|獲取上次訪問指定文件的時間。|
|[CGopher 檔案尋找:抓取最後寫入時間](#getlastwritetime)|獲取上次寫入指定文件的時間。|
|[CGopher 檔案尋找:取得長度](#getlength)|獲取找到檔的長度(以位元組為單位)。|
|[CGopher 檔案尋找:取得定位器](#getlocator)|獲取`CGopherLocator`物件。|
|[CGopher 檔案尋找:抓取螢幕名稱](#getscreenname)|獲取高時螢幕的名稱。|
|[CGopher檔查找::是點](#isdots)|測試目前目錄和父目錄標記,同時遍歷檔。|

## <a name="remarks"></a>備註

`CGopherFileFind`包括開始搜尋、查找檔並返回文件 URL 的成員函數。

其他為互聯網和本地檔搜索設計的MFC類包括[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)和[CFileFind。](../../mfc/reference/cfilefind-class.md) 與`CGopherFileFind`配合這些類為使用者提供了一個無縫機制,以便使用者查找特定檔,而不管伺服器協定、檔案類型或位置(本地電腦或遠端伺服器)。請注意,沒有用於在 HTTP 伺服器上搜索的 MFC 類,因為 HTTP 不支援搜尋所需的直接檔操作。

> [!NOTE]
> `CGopherFileFind`不支援其基類別[CFileFind](../../mfc/reference/cfilefind-class.md)的以下成員函數:

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [取得檔案路徑](../../mfc/reference/cfilefind-class.md#getfilepath)

- [取得檔案標題](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [取得檔案網址](../../mfc/reference/cfilefind-class.md#getfileurl)

此外,當與`CGopherFileFind`使用時`CFileFind`,成員函數[IsDots](../../mfc/reference/cfilefind-class.md#isdots)始終為 FALSE。

有關如何使用`CGopherFileFind`和其他 WinInet 類別的詳細資訊,請參閱[使用 WinInet 使用 Internet 編程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopher檔案查找::CGopher檔查找

呼叫此成員函數以建構物件`CGopherFileFind`。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pConnection*<br/>
指向[Gopher 連接](../../mfc/reference/cgopherconnection-class.md)物件的指標。

*dwContext*<br/>
操作的上下文標識碼。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

mFC`CGopherFileFind`從 創建物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)`CGopherFileFind`物件向物件發送*dwContext*的預設值。 建構`CGopherFileFind`物件時,可以重寫預設值,將上下文標識符設置為您選擇的值。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopher 檔案尋找:尋找檔案

調用此成員函數以查找 gopher 檔。

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

*參考定位器*<br/>
對[CGopher 定位器物件的參考](../../mfc/reference/cgopherlocator-class.md)。

*普斯特林*<br/>
指向包含檔名的字串的指標。

*dwFlags*<br/>
描述如何處理此會話的標誌。 有效標誌包括:

- INTERNET_FLAG_RELOAD 從遠端伺服器獲取數據,即使它是本地快取的。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何閘道中快取資料。

- INTERNET_FLAG_SECURE使用安全套接字層或PCT請求線上的安全交易。 此標誌僅適用於 HTTP 請求。

- INTERNET_FLAG_USE_EXISTING 如果可能,請重用與伺服器的現有連接以`FindFile`訪問 新請求,而不是為每個請求創建新會話。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

調用`FindFile`以檢索第一個 gopher 物件後,可以調用[FindNextFile](#findnextfile)來檢索後續的 gopher 檔。

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopher檔案查找::尋找下一個檔案

調用此成員函數以繼續以調用[CGopherFileFind::FindFile](#findfile)開始的檔搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果檔更多,則非零;如果找到的檔是目錄中的最後一個檔或發生錯誤,則為零。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔是目錄中的最後一個檔,或者找不到匹配的檔,則`GetLastError`函數將返回ERROR_NO_MORE_FILES。

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopher 檔案尋找:取得創造時間

獲取目前檔的創建時間。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標,其中包含創建文件的時間。

*參考時間*<br/>
對[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

### <a name="return-value"></a>傳回值

如果成功,則非零;0,如果不成功。 `GetCreationTime`僅當從未在此`CGopherFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetCreationTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopher 檔案尋找:抓取最後存取時間

獲取上次訪問指定文件的時間。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>參數

*參考時間*<br/>
對[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標,其中包含上次訪問文件的時間。

### <a name="return-value"></a>傳回值

如果成功,則非零;0,如果不成功。 `GetLastAccessTime`僅當從未在此`CGopherFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetLastAccessTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopher 檔案尋找:抓取最後寫入時間

獲取上次更改文件的時間。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
指向[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構的指標,其中包含檔上次寫入的時間。

*參考時間*<br/>
對[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

### <a name="return-value"></a>傳回值

如果成功,則非零;0,如果不成功。 `GetLastWriteTime`僅當從未在此`CGopherFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetLastWriteTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopher 檔案尋找:取得長度

呼叫此成員函數以獲取找到檔的長度(以位元組為單位)。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

找到檔的長度(以位元組為單位)。

### <a name="remarks"></a>備註

`GetLength`使用 Win32 結構[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)獲取以位元組為單位的檔大小的值。

> [!NOTE]
> 自 MFC 7.0`GetLength`起,支援 64 位整數類型。 以前使用此較新版本的庫構建的代碼可能會導致截斷警告。

### <a name="example"></a>範例

  請參閱[CFile::getLength(](../../mfc/reference/cfile-class.md#getlength)基數可實現)的範例。

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopher 檔案尋找:取得定位器

呼叫此成員函數獲取[FindFile](#findfile)用於查找 gopher 檔的[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>傳回值

`CGopherLocator` 物件。

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopher 檔案尋找:抓取螢幕名稱

調用此成員函數獲取高時螢幕的名稱。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>傳回值

高舍屏幕的名稱。

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopher檔查找::是點

測試目前目錄和父目錄標記,同時遍歷檔。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>傳回值

如果找到的檔的名稱為"."或"..",則為"..",表示找到的文件實際上是一個目錄,則為非零。 否則為 0。

### <a name="remarks"></a>備註

在調用`IsDots`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

## <a name="see-also"></a>另請參閱

[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 類別](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
