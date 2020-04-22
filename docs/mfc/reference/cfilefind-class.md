---
title: CFileFind 類別
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: 5bb53a6abf7040bd6ee9f5f2cf56b0feb4d62e66
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755026"
---
# <a name="cfilefind-class"></a>CFileFind 類別

執行本地檔案搜尋,是執行 Internet 檔搜尋的[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的基本類。

## <a name="syntax"></a>語法

```
class CFileFind : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[檔案尋找::檔案尋找](#cfilefind)|建構 `CFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[檔案尋找:關閉](#close)|關閉搜索請求。|
|[檔案尋找:尋找檔案](#findfile)|搜尋目錄以搜尋指定的檔名。|
|[檔案尋找:尋找下一個檔案](#findnextfile)|繼續從上一個調用[FindFile](#findfile)的檔搜索。|
|[檔案尋找:抓取製作時間](#getcreationtime)|獲取創建文件的時間。|
|[檔案尋找::抓取檔案名稱](#getfilename)|取得找到檔案名稱(包括副檔名)|
|[檔案尋找:抓取檔案路徑](#getfilepath)|獲取找到文件的整個路徑。|
|[檔案尋找:抓取檔案標題](#getfiletitle)|獲取找到檔的標題。 標題不包括擴展。|
|[檔案尋找::抓取檔案網址](#getfileurl)|獲取找到檔案的 URL,包括檔路徑。|
|[檔案尋找::抓取最後存取時間](#getlastaccesstime)|獲取上次訪問文件的時間。|
|[檔案尋找::抓取最後寫入時間](#getlastwritetime)|獲取上次更改和保存文件的時間。|
|[檔案尋找:抓取長度](#getlength)|獲取找到檔的長度(以位元組為單位)。|
|[檔案尋找:抓取根](#getroot)|獲取找到檔的根目錄。|
|[檔案尋找:已存檔](#isarchived)|確定是否存檔了找到的檔。|
|[檔案尋找:已壓縮](#iscompressed)|確定是否壓縮找到的檔。|
|[檔案尋找::IsDirectory](#isdirectory)|確定找到的檔是否為目錄。|
|[檔案尋找::是點](#isdots)|確定找到的檔的名稱是否具有名稱"."或"..",指示該檔實際上是一個目錄。|
|[檔案尋找:隱藏](#ishidden)|確定找到的檔案是否隱藏。|
|[檔案尋找::正常](#isnormal)|確定找到的檔是否正常(換句話說,沒有其他屬性)。|
|[檔案尋找:僅閱讀](#isreadonly)|確定找到的檔是否為唯讀檔。|
|[檔案尋找:isSystem](#issystem)|確定找到的檔是否為系統檔。|
|[檔案尋找::暫時](#istemporary)|確定找到的檔是否臨時。|
|[檔案尋找::符合蒙版](#matchesmask)|指示要找到的檔所需的文件屬性。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[檔案尋找::關閉上下文](#closecontext)|關閉目前搜尋句柄指定的檔。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[檔案尋找:m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 物件的指標。|

## <a name="remarks"></a>備註

`CFileFind`包括開始搜尋、尋找檔並返回檔的標題、名稱或路徑的成員函數。 對於 Internet 搜尋,成員函數[GetFileURL](#getfileurl)傳回檔的 URL。

`CFileFind`是另外兩個 MFC 類的基本類,旨在搜索特定的`CGopherFileFind`伺服器類型 :專門使用`CFtpFileFind`gopher 伺服器 ,並特別適用於 FTP 伺服器。 總之,這三個類為用戶端提供了一個無縫機制,以便用戶端查找本地電腦或遠端伺服器上的檔,而不管伺服器協定、檔案類型或位置如何。

以下代碼將枚舉目前的目錄中的所有檔案,列印每個檔的名稱:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

為了保持示例簡單,此代碼使用C++標準庫`cout`類。 線路`cout`可以替換為調`CListBox::AddString`用 ,例如,在具有圖形使用者介面的程式中。

有關如何使用`CFileFind`和其他 WinInet 類別的詳細資訊,請參閱[使用 WinInet 使用 Internet 編程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>檔案尋找::檔案尋找

構造`CFileFind`物件時將調用此成員函數。

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>參數

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindclose"></a><a name="close"></a>檔案尋找:關閉

調用此成員函數以結束搜索、重置上下文並釋放所有資源。

```cpp
void Close();
```

### <a name="remarks"></a>備註

調用`Close`後,您不必在調`CFileFind`用[FindFile](#findfile)開始新搜索之前創建新實例。

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>檔案尋找::關閉上下文

關閉目前搜尋句柄指定的檔。

```
virtual void CloseContext();
```

### <a name="remarks"></a>備註

關閉搜索句柄的當前值指定的檔。 重寫此函數以更改默認行為。

您必須至少調用一次[FindFile](#findfile)或[FindNextFile](#findnextfile)函數才能檢索有效的搜索句柄。 `FindFile`和`FindNextFile`函數使用搜索句柄查找名稱與給定名稱匹配的檔。

## <a name="cfilefindfindfile"></a><a name="findfile"></a>檔案尋找:尋找檔案

調用此成員函數以打開檔搜索。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>參數

*pstrName*<br/>
指向要查找的檔名稱的字串的指標。 如果透過 NULL 進行*pstrName,*`FindFile`則\*執行通配符 (*) 搜尋。

*dwunused*<br/>
保留以使用`FindFile`派生類進行多態性。 必須是 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

調用`FindFile`開始檔搜索后,調用[FindNextFile](#findnextfile)檢索後續檔。 在呼叫以下`FindNextFile`任一屬性成員函數之前,必須至少調用一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [取得檔案標題](#getfiletitle)

- [取得檔案路徑](#getfilepath)

- [取得檔案網址](#getfileurl)

- [取得最後存取時間](#getlastaccesstime)

- [取得上次寫入時間](#getlastwritetime)

- [取得長度](#getlength)

- [GetRoot](#getroot)

- [已封存](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [是點](#isdots)

- [隱藏](#ishidden)

- [正常](#isnormal)

- [只閱讀](#isreadonly)

- [IsSystem](#issystem)

- [臨時性](#istemporary)

- [符合遮罩](#matchesmask)

### <a name="example"></a>範例

  請參考[CFileFind 的範例:isDirectory](#isdirectory)。

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>檔案尋找:尋找下一個檔案

調用此成員函數以繼續從之前調用[FindFile](#findfile)的檔搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果檔更多,則非零;如果找到的檔是目錄中的最後一個檔或發生錯誤,則為零。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔是目錄中的最後一個檔,或者找不到匹配的檔,則`GetLastError`函數將返回ERROR_NO_MORE_FILES。

### <a name="remarks"></a>備註

在呼叫以下`FindNextFile`任一屬性成員函數之前,必須至少調用一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [取得檔案標題](#getfiletitle)

- [取得檔案路徑](#getfilepath)

- [取得檔案網址](#getfileurl)

- [取得最後存取時間](#getlastaccesstime)

- [取得上次寫入時間](#getlastwritetime)

- [取得長度](#getlength)

- [GetRoot](#getroot)

- [已封存](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [是點](#isdots)

- [隱藏](#ishidden)

- [正常](#isnormal)

- [只閱讀](#isreadonly)

- [IsSystem](#issystem)

- [臨時性](#istemporary)

- [符合遮罩](#matchesmask)

`FindNextFile`包裝 Win32 函數[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:isDirectory](#isdirectory)。

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>檔案尋找:抓取製作時間

呼叫此成員函數以獲取創建指定檔案的時間。

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

如果成功,則非零;0,如果不成功。 `GetCreationTime`僅當從未在此`CFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetCreationTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>檔案尋找::抓取檔案名稱

呼叫此成員函數以獲取找到的檔的名稱。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>傳回值

最近找到的文件的名稱。

### <a name="remarks"></a>備註

在調用 GetFileName 之前,您必須至少調用一次[FindNextFile。](#findnextfile)

`GetFileName`是返回某種形式的檔`CFileFind`名的三個成員函數之一。 下面的清單描述了這三者及其變化方式:

- `GetFileName`返回檔名,包括副檔名。 例如,呼叫`GetFileName`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔名*myfile.txt*。

- [GetFilePath](#getfilepath)返回檔的整個路徑。 例如,呼叫`GetFilePath`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔案路徑*c:\myhtml_myfile.txt*。

- [GetFileTitle](#getfiletitle)傳回檔名,不包括文件副檔名。 例如,呼叫`GetFileTitle`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔案標題*myfile*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>檔案尋找:抓取檔案路徑

呼叫此成員函數獲取指定檔的完整路徑。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>傳回值

指定檔的路徑。

### <a name="remarks"></a>備註

在調用`GetFilePath`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

`GetFilePath`是返回某種形式的檔`CFileFind`名的三個成員函數之一。 下面的清單描述了這三者及其變化方式:

- [GetFileName](#getfilename)傳回檔名,包括副檔名。 例如,呼叫`GetFileName`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔名*myfile.txt*。

- `GetFilePath`返回檔的整個路徑。 例如,呼叫`GetFilePath`以產生有關該`c:\myhtml\myfile.txt`檔案的使用者訊息將傳回`c:\myhtml\myfile.txt`檔案路徑 。

- [GetFileTitle](#getfiletitle)傳回檔名,不包括文件副檔名。 例如,呼叫`GetFileTitle`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔案標題*myfile*。

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>檔案尋找:抓取檔案標題

呼叫此成員函數獲取找到的文件的標題。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>傳回值

檔案的標題。

### <a name="remarks"></a>備註

在調用`GetFileTitle`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

`GetFileTitle`是返回某種形式的檔`CFileFind`名的三個成員函數之一。 下面的清單描述了這三者及其變化方式:

- [GetFileName](#getfilename)傳回檔名,包括副檔名。 例如,呼叫`GetFileName`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔名*myfile.txt*。

- [GetFilePath](#getfilepath)返回檔的整個路徑。 例如,呼叫`GetFilePath`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔案路徑*c:\myhtml_myfile.txt*。

- `GetFileTitle`返回檔名,不包括檔副檔名。 例如,呼叫`GetFileTitle`以產生有關檔*c:_myhtml_myfile.txt*的使用者訊息傳回檔案標題*myfile*。

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>檔案尋找::抓取檔案網址

呼叫此成員函數以檢索指定的 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

完整的 URL。

### <a name="remarks"></a>備註

在調用`GetFileURL`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

`GetFileURL`與成員函數[GetFilePath](#getfilepath)類似,只不過它返回`file://path`窗體 中的 URL。 例如,呼叫`GetFileURL`以取得*myfile.txt*的`file://c:\myhtml\myfile.txt`完整 URL 傳回 URL 。

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>檔案尋找::抓取最後存取時間

呼叫此成員函數以獲取上次訪問指定文件的時間。

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

如果成功,則非零;0,如果不成功。 `GetLastAccessTime`僅當從未在此`CFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetLastAccessTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>檔案尋找::抓取最後寫入時間

呼叫此成員函數以獲取上次更改文件的時間。

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

如果成功,則非零;0,如果不成功。 `GetLastWriteTime`僅當從未在此`CFileFind`物件上調用[FindNextFile](#findnextfile)時,才返回 0。

### <a name="remarks"></a>備註

在調用`GetLastWriteTime`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

> [!NOTE]
> 並非所有文件系統都使用相同的語義來實現此函數返回的時間戳。 如果基礎檔系統或伺服器不支援保留時間屬性,則此功能可能會返回其他時間戳函數返回的相同值。 有關時間格式的資訊,請參閱[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構。 在某些作業系統上,返回的時間位於檔所在的計算機本地時區。 有關詳細資訊,請參閱 Win32[檔時間到本地文件時間](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)API。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindgetlength"></a><a name="getlength"></a>檔案尋找:抓取長度

呼叫此成員函數以獲取找到的文件的長度(以位元組為單位)。

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

找到檔的長度(以位元組為單位)。

### <a name="remarks"></a>備註

在調用`GetLength`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

`GetLength`使用 Win32 結構[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)獲取和返回檔大小的值(以位元組為單位)。

> [!NOTE]
> 自 MFC 7.0`GetLength`起,支援 64 位整數類型。 以前使用此較新版本的庫構建的現有代碼可能會導致截斷警告。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>檔案尋找:抓取根

呼叫此成員函數以獲取找到檔的根。

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>傳回值

活動搜索的根。

### <a name="remarks"></a>備註

在調用`GetRoot`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

此成員函數返回用於啟動搜索的驅動器指定器和路徑名稱。 例如,調用[FindFile](#findfile) `*.dat``GetRoot`時會導致返回空字串。 將`c:\windows\system\*.dll`路徑(如 )`FindFile`傳遞`GetRoot``c:\windows\system\`給返回的結果。

### <a name="example"></a>範例

  請參考[CFileFind 範例:抓取檔名](#getfilename)。

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>檔案尋找:已存檔

呼叫此成員函數以確定找到的檔是否存檔。

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

應用程式標記存檔,該檔將備份或刪除[,FILE_ATTRIBUTE_ARCHIVEWIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構中識別的文件屬性。

在調用`IsArchived`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>檔案尋找:已壓縮

呼叫此成員函數以確定找到的檔是否被壓縮。

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

壓縮檔標有FILE_ATTRIBUTE_COMPRESSED,WIN32_FIND_DATA[結構中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)標識的文件屬性。 對於檔,此屬性指示檔中的所有數據都已壓縮。 對於目錄,此屬性指示壓縮是新創建的檔案和子目錄的預設值。

在調用`IsCompressed`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>檔案尋找::IsDirectory

呼叫此成員函數以確定找到的檔是否為目錄。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

作為目錄的檔[FILE_ATTRIBUTE_DIRECTORYWIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構中識別的檔屬性進行標記。

在調用`IsDirectory`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

這個小程式會重詛咒 C 上的每個目錄:*驅動器並列印目錄的名稱。

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>檔案尋找::是點

調用此成員函數以測試當前目錄和父目錄標記,同時遍歷檔。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>傳回值

如果找到的檔的名稱為"."或"..",則為"..",表示找到的文件實際上是一個目錄,則為非零。 否則為 0。

### <a name="remarks"></a>備註

在調用`IsDots`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:isDirectory](#isdirectory)。

## <a name="cfilefindishidden"></a><a name="ishidden"></a>檔案尋找:隱藏

呼叫此成員函數以確定找到的檔案是否隱藏。

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隱藏檔(標有FILE_ATTRIBUTE_HIDDEN,WIN32_FIND_DATA[結構中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)標識的文件屬性。 隱藏檔不包括在普通目錄清單中。

在調用`IsHidden`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>檔案尋找::正常

呼叫此成員函數以確定找到的檔案是否為普通檔。

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

標有FILE_ATTRIBUTE_NORMAL的檔,WIN32_FIND_DATA[結構中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)標識的文件屬性。 普通文件沒有其他屬性集。 所有其他文件屬性都覆蓋此屬性。

在調用`IsNormal`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>檔案尋找:僅閱讀

呼叫此成員函數以確定找到的檔是否為唯讀檔。

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

唯讀檔案標有FILE_ATTRIBUTE_READONLY,WIN32_FIND_DATA[結構中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)識別的文件屬性。 應用程式可以讀取此類檔,但不能寫入或刪除該檔。

在調用`IsReadOnly`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindissystem"></a><a name="issystem"></a>檔案尋找:isSystem

呼叫此成員函數以確定找到的檔是否為系統檔。

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

系統檔標有FILE_ATTRIBUTE_SYSTEM,WIN32_FIND_DATA[結構中](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)標識的文件屬性。 系統檔是作業系統的一部分,或者由操作系統專門使用。

在調用`IsSystem`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>檔案尋找::暫時

呼叫此成員函數以確定找到的檔是否為暫存檔。

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

暫存檔用[FILE_ATTRIBUTE_TEMPORARY(WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構中識別的檔案屬性)標記。 臨時檔用於臨時存儲。 應用程式僅在絕對必要時才應寫入檔。 檔的大部分數據保留在記憶體中,而不會刷新到介質,因為該檔將很快被刪除。

在調用`IsTemporary`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

關於檔案屬性的完整清單,請參閱成員函數[比對遮罩](#matchesmask)。

### <a name="example"></a>範例

  請參考[CFileFind 的範例:取得長度](#getlength)。

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>檔案尋找:m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>檔案尋找::符合蒙版

調用此成員函數以測試找到的檔上的文件屬性。

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>參數

*dwMask*<br/>
為找到的檔指定一個或多個文件屬性,這些屬性在[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構中標識。 要搜索多個屬性,請使用位或(&#124;)運算符。 以下屬性的任意組合是可以接受的:

- FILE_ATTRIBUTE_ARCHIVE 該檔是存檔檔。 應用程式使用此屬性標記檔以進行備份或刪除。

- FILE_ATTRIBUTE_COMPRESSED檔或目錄被壓縮。 對於檔,這意味著檔中的所有數據將被壓縮。 對於目錄,這意味著壓縮是新創建的檔和子目錄的預設值。

- FILE_ATTRIBUTE_DIRECTORY 該檔是目錄。

- FILE_ATTRIBUTE_NORMAL 該檔沒有其他屬性集。 此屬性僅在單獨使用時有效。 所有其他文件屬性都覆蓋此屬性。

- FILE_ATTRIBUTE_HIDDEN檔案已隱藏。 它不包含在普通目錄清單中。

- FILE_ATTRIBUTE_READONLY該檔是唯讀的。 應用程式可以讀取檔,但不能寫入或刪除該檔。

- FILE_ATTRIBUTE_SYSTEM 該檔是 操作系統的一部分或由操作系統專門使用。

- FILE_ATTRIBUTE_TEMPORARY 該檔用於臨時存儲。 應用程式僅在絕對必要時才應寫入檔。 檔的大部分數據保留在記憶體中,而不會刷新到介質,因為該檔將很快被刪除。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

在調用`MatchesMask`之前,您必須至少調用[FindNextFile](#findnextfile)一次。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 類別](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
