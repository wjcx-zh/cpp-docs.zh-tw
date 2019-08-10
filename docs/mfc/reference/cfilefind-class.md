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
ms.openlocfilehash: f2dfd3421d2154b4894b62b71d7993c483a77c53
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916130"
---
# <a name="cfilefind-class"></a>CFileFind 類別

會執行本機檔案搜尋, 而是[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的基類, 它會執行網際網路檔案搜尋。

## <a name="syntax"></a>語法

```
class CFileFind : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|建構 `CFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFileFind::Close](#close)|關閉搜尋要求。|
|[CFileFind::FindFile](#findfile)|在目錄中搜尋指定的檔案名。|
|[CFileFind::FindNextFile](#findnextfile)|繼續從先前的[FindFile](#findfile)呼叫進行檔案搜尋。|
|[CFileFind::GetCreationTime](#getcreationtime)|取得建立檔案的時間。|
|[CFileFind::GetFileName](#getfilename)|取得所找到檔案的名稱, 包括副檔名|
|[CFileFind::GetFilePath](#getfilepath)|取得找到之檔案的完整路徑。|
|[CFileFind::GetFileTitle](#getfiletitle)|取得所找到檔案的標題。 標題不包含延伸模組。|
|[CFileFind::GetFileURL](#getfileurl)|取得所找到檔案的 URL, 包括檔案路徑。|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|取得上次存取檔案的時間。|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|取得上次變更和儲存檔案的時間。|
|[CFileFind::GetLength](#getlength)|取得找到之檔案的長度 (以位元組為單位)。|
|[CFileFind::GetRoot](#getroot)|取得找到之檔案的根目錄。|
|[CFileFind::IsArchived](#isarchived)|判斷找到的檔案是否已封存。|
|[CFileFind::IsCompressed](#iscompressed)|判斷找到的檔案是否已壓縮。|
|[CFileFind::IsDirectory](#isdirectory)|判斷找到的檔案是否為目錄。|
|[CFileFind::IsDots](#isdots)|判斷找到的檔案名稱是否具有名稱 "." 或 "...", 表示實際上是目錄。|
|[CFileFind::IsHidden](#ishidden)|判斷找到的檔案是否已隱藏。|
|[CFileFind::IsNormal](#isnormal)|判斷找到的檔案是否正常 (換句話說, 沒有其他屬性)。|
|[CFileFind::IsReadOnly](#isreadonly)|判斷找到的檔案是否為唯讀。|
|[CFileFind::IsSystem](#issystem)|判斷找到的檔案是否為系統檔案。|
|[CFileFind::IsTemporary](#istemporary)|判斷找到的檔案是否為暫時性。|
|[CFileFind::MatchesMask](#matchesmask)|表示要尋找之檔案的所需檔案屬性。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|關閉目前搜尋控制碼所指定的檔案。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|說明|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 物件的指標。|

## <a name="remarks"></a>備註

`CFileFind`包含開始搜尋的成員函式、尋找檔案, 以及傳回檔案的標題、名稱或路徑。 針對網際網路搜尋, 成員函式[GetFileURL](#getfileurl)會傳回檔案的 URL。

`CFileFind`是其他兩個 MFC 類別的基類, 設計用來搜尋特定的伺服器`CGopherFileFind`類型: 特別適用于 Gopher 伺服器`CFtpFileFind` , 並且特別適用于 FTP 伺服器。 這三個類別一起提供順暢的機制, 讓用戶端在本機電腦或遠端伺服器上尋找檔案, 不論伺服器通訊協定、檔案類型或位置為何。

下列程式碼會列舉目前目錄中的所有檔案, 並列印每個檔案的名稱:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

為了讓範例保持簡單, 此程式碼會C++使用標準`cout`程式庫類別。 例如, 在具有圖形化使用者介面的程式`CListBox::AddString`中, 可以使用呼叫來取代這一行。`cout`

如需如何使用`CFileFind`和其他 WinInet 類別的詳細資訊, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

在結構化`CFileFind`物件時, 會呼叫這個成員函式。

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>參數

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="close"></a>  CFileFind::Close

呼叫此成員函式以結束搜尋、重設內容, 以及釋放所有資源。

```
void Close();
```

### <a name="remarks"></a>備註

呼叫`Close`之後, 您不需要在呼叫[FindFile](#findfile)開始新的搜尋之前, 先建立新`CFileFind`的實例。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="closecontext"></a>  CFileFind::CloseContext

關閉目前搜尋控制碼所指定的檔案。

```
virtual void CloseContext();
```

### <a name="remarks"></a>備註

關閉搜尋控制碼的目前值所指定的檔案。 覆寫此函數以變更預設行為。

您必須呼叫[FindFile](#findfile)或[FindNextFile](#findnextfile)函式至少一次, 才能取出有效的搜尋控制碼。 `FindFile` 和`FindNextFile`函式會使用搜尋控制碼來尋找名稱符合指定名稱的檔案。

##  <a name="findfile"></a>  CFileFind::FindFile

呼叫此成員函式以開啟檔案搜尋。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>參數

*pstrName*<br/>
字串的指標, 其中包含要尋找的檔案名。 如果您為*pstrName*傳遞 Null, `FindFile`則會執行萬用字元 (*\*.) 搜尋。

*dwUnused*<br/>
保留以使`FindFile`衍生類別成為多型。 必須是 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊, 請呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

呼叫`FindFile`以開始檔案搜尋之後, 請呼叫[FindNextFile](#findnextfile)來取出後續的檔案。 呼叫下列任何`FindNextFile`屬性成員函式之前, 您至少必須呼叫一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>範例

  請參閱[CFileFind:: IsDirectory](#isdirectory)的範例。

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

呼叫這個成員函式, 以從先前的[FindFile](#findfile)呼叫繼續進行檔案搜尋。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果有多個檔案, 則為非零值;如果找到的檔案是目錄中的最後一個檔案, 或如果發生錯誤, 則為零。 若要取得延伸錯誤資訊, 請呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔案是目錄中的最後一個檔案, 或如果找不到相符的檔案, 則`GetLastError`函式會傳回 ERROR_NO_MORE_FILES。

### <a name="remarks"></a>備註

呼叫下列任何`FindNextFile`屬性成員函式之前, 您至少必須呼叫一次:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`包裝 Win32 函數[FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea)。

### <a name="example"></a>範例

  請參閱[CFileFind:: IsDirectory](#isdirectory)的範例。

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

呼叫這個成員函式以取得指定檔案的建立時間。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)結構的指標, 其中包含建立檔案的時間。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;如果失敗, 則為0。 `GetCreationTime`只有在此`CFileFind`物件上從未呼叫過[FindNextFile](#findnextfile)時, 才會傳回0。

### <a name="remarks"></a>備註

呼叫`GetCreationTime`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性, 則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊, 請參閱[Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構。 在某些作業系統上, 所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊, 請參閱 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="getfilename"></a>  CFileFind::GetFileName

呼叫這個成員函式以取得找到的檔案名稱。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>傳回值

最近找到的檔案的名稱。

### <a name="remarks"></a>備註

呼叫 GetFileName 之前, 您至少必須呼叫[FindNextFile](#findnextfile)一次。

`GetFileName`是三個`CFileFind`成員函式的其中一個, 這些函式會傳回某種形式的檔案名。 下列清單說明三種和它們的差異:

- `GetFileName`傳回檔案名, 包括副檔名。 例如, 呼叫`GetFileName`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案名*myfile.txt。*

- [GetFilePath](#getfilepath)會傳回檔案的完整路徑。 例如, 呼叫`GetFilePath`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案路徑*c:\myhtml\myfile.txt*。

- [GetFileTitle](#getfiletitle)會傳回檔案名, 但不包括副檔名。 例如, 呼叫`GetFileTitle`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案標題*myfile.txt*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

呼叫這個成員函式以取得指定檔案的完整路徑。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>傳回值

指定檔案的路徑。

### <a name="remarks"></a>備註

呼叫`GetFilePath`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

`GetFilePath`是三個`CFileFind`成員函式的其中一個, 這些函式會傳回某種形式的檔案名。 下列清單說明三種和它們的差異:

- [GetFileName](#getfilename)會傳回檔案名, 包括副檔名。 例如, 呼叫`GetFileName`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案名*myfile.txt。*

- `GetFilePath`傳回檔案的完整路徑。 例如, 呼叫`GetFilePath`來產生有關`c:\myhtml\myfile.txt`檔案的使用者訊息, 會傳回檔案路徑`c:\myhtml\myfile.txt`。

- [GetFileTitle](#getfiletitle)會傳回檔案名, 但不包括副檔名。 例如, 呼叫`GetFileTitle`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案標題*myfile.txt*。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

呼叫這個成員函式以取得所找到檔案的標題。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>傳回值

檔案的標題。

### <a name="remarks"></a>備註

呼叫`GetFileTitle`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

`GetFileTitle`是三個`CFileFind`成員函式的其中一個, 這些函式會傳回某種形式的檔案名。 下列清單說明三種和它們的差異:

- [GetFileName](#getfilename)會傳回檔案名, 包括副檔名。 例如, 呼叫`GetFileName`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案名*myfile.txt。*

- [GetFilePath](#getfilepath)會傳回檔案的完整路徑。 例如, 呼叫`GetFilePath`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案路徑*c:\myhtml\myfile.txt*。

- `GetFileTitle`傳回檔案名, 不包括副檔名。 例如, 呼叫`GetFileTitle`來產生有關 file *c:\myhtml\myfile.txt*的使用者訊息, 會傳回檔案標題*myfile.txt*。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

呼叫這個成員函式, 以取得指定的 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

完整的 URL。

### <a name="remarks"></a>備註

呼叫`GetFileURL`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

`GetFileURL`類似于成員函式[GetFilePath](#getfilepath), 不同之處在于它會傳回格式`file://path`的 URL。 例如, 呼叫`GetFileURL`以取得*myfile.txt*的完整 url 會傳回 url `file://c:\myhtml\myfile.txt`。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

呼叫這個成員函式以取得上次存取指定檔案的時間。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>參數

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

*pTimeStamp*<br/>
[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)結構的指標, 其中包含上次存取檔案的時間。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;如果失敗, 則為0。 `GetLastAccessTime`只有在此`CFileFind`物件上從未呼叫過[FindNextFile](#findnextfile)時, 才會傳回0。

### <a name="remarks"></a>備註

呼叫`GetLastAccessTime`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性, 則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊, 請參閱[Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構。 在某些作業系統上, 所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊, 請參閱 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

呼叫這個成員函式, 以取得上次變更檔案的時間。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>參數

*pTimeStamp*<br/>
[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)結構的指標, 其中包含檔案上次被寫入的時間。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;如果失敗, 則為0。 `GetLastWriteTime`只有在此`CFileFind`物件上從未呼叫過[FindNextFile](#findnextfile)時, 才會傳回0。

### <a name="remarks"></a>備註

呼叫`GetLastWriteTime`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

> [!NOTE]
>  並非所有檔案系統都使用相同的語義來執行此函式所傳回的時間戳記。 如果基礎檔案系統或伺服器不支援保留時間屬性, 則此函式可能會傳回其他時間戳記函式所傳回的相同值。 如需時間格式的詳細資訊, 請參閱[Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構。 在某些作業系統上, 所傳回的時間會是該檔案所在的本機時區。 如需詳細資訊, 請參閱 Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) API。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="getlength"></a>  CFileFind::GetLength

呼叫這個成員函式可取得找到檔案的長度 (以位元組為單位)。

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

找到的檔案長度 (以位元組為單位)。

### <a name="remarks"></a>備註

呼叫`GetLength`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

`GetLength`使用 Win32 結構[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)來取得並傳回檔案大小的值 (以位元組為單位)。

> [!NOTE]
>  從 MFC 7.0, `GetLength`支援64位整數類型。 先前使用此新版程式庫建立的現有程式碼可能會產生截斷警告。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

呼叫這個成員函式以取得所找到檔案的根目錄。

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>傳回值

現用搜尋的根目錄。

### <a name="remarks"></a>備註

呼叫`GetRoot`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

此成員函式會傳回用來開始搜尋的磁片磁碟機規範和路徑名稱。 例如, 以`*.dat`結果`GetRoot`呼叫[FindFile](#findfile)會傳回空字串。 `c:\windows\system\*.dll`將路徑 (例如) 傳遞至`FindFile`傳回的結果`c:\windows\system\` `GetRoot` 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetFileName](#getfilename)的範例。

##  <a name="isarchived"></a>  CFileFind::IsArchived

呼叫這個成員函式, 以判斷找到的檔案是否已封存。

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

應用程式會使用 FILE_ATTRIBUTE_ARCHIVE (在[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中識別的檔案屬性) 來標示要備份或移除的封存檔案。

呼叫`IsArchived`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

呼叫這個成員函式, 以判斷找到的檔案是否已壓縮。

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

壓縮的檔案會標記為 FILE_ATTRIBUTE_COMPRESSED, 這是[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 若為檔案, 這個屬性會指出檔案中的所有資料都是壓縮檔案。 若為目錄, 此屬性工作表示壓縮是新建立之檔案和子目錄的預設值。

呼叫`IsCompressed`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

呼叫這個成員函式, 以判斷找到的檔案是否為目錄。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

目錄的檔案會以 FILE_ATTRIBUTE_DIRECTORY 標示[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。

呼叫`IsDirectory`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

這個小程式會 recurses C:\ 上的每個目錄磁片磁碟機並列印目錄的名稱。

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

呼叫這個成員函式可在逐一查看檔案時, 測試目前的目錄和上層目錄標記。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>傳回值

如果找到的檔案名稱為 "." 或 "...", 則為非零, 表示找到的檔案實際上是目錄。 否則為0。

### <a name="remarks"></a>備註

呼叫`IsDots`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

### <a name="example"></a>範例

  請參閱[CFileFind:: IsDirectory](#isdirectory)的範例。

##  <a name="ishidden"></a>  CFileFind::IsHidden

呼叫這個成員函式, 以判斷找到的檔案是否已隱藏。

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隱藏的檔案, 以 FILE_ATTRIBUTE_HIDDEN 標示, [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 一般目錄清單中不會包含隱藏的檔案。

呼叫`IsHidden`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="isnormal"></a>  CFileFind::IsNormal

呼叫這個成員函式, 以判斷找到的檔案是否為一般檔案。

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

以 FILE_ATTRIBUTE_NORMAL 標記的檔案, 這是[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 一般檔案未設定其他屬性。 所有其他檔案屬性都會覆寫這個屬性。

呼叫`IsNormal`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

呼叫這個成員函式, 以判斷找到的檔案是否為唯讀。

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

唯讀檔案會標記為 FILE_ATTRIBUTE_READONLY, 這是[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 應用程式可以讀取這類檔案, 但無法寫入或刪除檔案。

呼叫`IsReadOnly`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="issystem"></a>  CFileFind::IsSystem

呼叫這個成員函式, 以判斷找到的檔案是否為系統檔案。

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

系統檔案標記為 FILE_ATTRIBUTE_SYSTEM, 這是[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 系統檔案屬於, 或由作業系統獨佔使用。

呼叫`IsSystem`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="istemporary"></a>  CFileFind::IsTemporary

呼叫這個成員函式, 以判斷找到的檔案是否為暫存檔案。

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

暫存檔案會標記為 FILE_ATTRIBUTE_TEMPORARY, 這是[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的檔案屬性。 暫存檔案用於暫時儲存。 只有在絕對必要時, 應用程式才應該寫入檔案。 大部分檔案的資料會保留在記憶體中, 而不會排清到媒體, 因為檔案很快就會遭到刪除。

呼叫`IsTemporary`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

如需檔案屬性的完整清單, 請參閱成員函式[MatchesMask](#matchesmask) 。

### <a name="example"></a>範例

  請參閱[CFileFind:: GetLength](#getlength)的範例。

##  <a name="m_ptm"></a>  CFileFind::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

呼叫這個成員函式可在找到的檔案上測試檔案屬性。

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>參數

*dwMask*<br/>
針對找到的檔案, 指定[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-win32_find_dataa)結構中所識別的一個或多個檔案屬性。 若要搜尋多個屬性, 請使用位 OR&#124;() 運算子。 下列屬性的任何組合都是可接受的:

- FILE_ATTRIBUTE_ARCHIVE 檔案是封存檔案。 應用程式會使用此屬性來標示要備份或移除的檔案。

- FILE_ATTRIBUTE_COMPRESSED 檔案或目錄已壓縮。 就檔案而言, 這表示檔案中的所有資料都是壓縮檔案。 若是目錄, 這表示壓縮是新建立之檔案和子目錄的預設值。

- FILE_ATTRIBUTE_DIRECTORY 檔案是目錄。

- FILE_ATTRIBUTE_NORMAL 檔案未設定其他屬性。 這個屬性只有在單獨使用時才有效。 所有其他檔案屬性都會覆寫這個屬性。

- FILE_ATTRIBUTE_HIDDEN 檔案已隱藏。 這不會包含在一般目錄清單中。

- FILE_ATTRIBUTE_READONLY 檔案是唯讀的。 應用程式可以讀取檔案, 但無法寫入或刪除檔案。

- FILE_ATTRIBUTE_SYSTEM 檔案是的一部分, 或由作業系統獨佔使用。

- FILE_ATTRIBUTE_TEMPORARY 檔案正用於暫時儲存。 只有在絕對必要時, 應用程式才應該寫入檔案。 大部分檔案的資料會保留在記憶體中, 而不會排清到媒體, 因為檔案很快就會遭到刪除。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊, 請呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

呼叫`MatchesMask`之前, 您必須至少呼叫[FindNextFile](#findnextfile)一次。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind 類別](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
