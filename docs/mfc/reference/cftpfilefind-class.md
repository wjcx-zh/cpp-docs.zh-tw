---
title: CFtpFileFind 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 885005cc04da94ff4339a5f538956b1bfc96b4c3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503685"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 類別

協助 FTP 伺服器的網際網路檔案搜尋。

## <a name="syntax"></a>語法

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|建構 `CFtpFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|尋找 FTP 伺服器上的檔案。|
|[CFtpFileFind::FindNextFile](#findnextfile)|會繼續從先前呼叫檔案搜尋[FindFile](#findfile)。|
|[CFtpFileFind::GetFileURL](#getfileurl)|取得 URL，包括路徑，找到的檔案。|

## <a name="remarks"></a>備註

`CFtpFileFind` 包含開始搜尋，找出檔案，並傳回的 URL 或其他檔案的描述性資訊的成員函式。

設計的網際網路和搜尋的本機檔案包含其他 MFC 類別[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)並[CFileFind](../../mfc/reference/cfilefind-class.md)。 搭配`CFtpFileFind`，這些類別提供無縫式的機制，讓用戶端尋找特定的檔案，不論伺服器 （本機電腦或遠端伺服器） 的通訊協定或檔案類型。 請注意，來搜尋 HTTP 伺服器上，因為 HTTP 不支援直接與檔案操作所需的搜尋沒有任何 MFC 類別。

如需有關如何使用`CFtpFileFind`和其他 WinInet 類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="example"></a>範例

下列程式碼示範如何列舉在 FTP 伺服器的目前目錄中的所有檔案。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

此成員函式呼叫來建構`CFtpFileFind`物件。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pConnection*<br/>
`CFtpConnection` 物件的指標。 您可以藉由呼叫來取得 FTP 連線[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)。

*dwContext*<br/>
內容識別碼`CFtpFileFind`物件。 請參閱**備註**如需有關此參數。

### <a name="remarks"></a>備註

預設值*dwContext* MFC，以便傳送`CFtpFileFind`物件[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CFtpFileFind`物件。 您可以覆寫預設值可設定的內容識別碼以您選擇的值。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供，它識別之物件的狀態。 請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

### <a name="example"></a>範例

  請參閱稍早在本主題中的類別概觀中的範例。

##  <a name="findfile"></a>  CFtpFileFind::FindFile

呼叫此成員函式，來尋找 FTP 檔案。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>參數

*pstrName*<br/>
包含要尋找的檔案名稱的字串指標。 如果是 NULL，則呼叫會執行萬用字元搜尋 （*）。

*dwFlags*<br/>
描述如何處理此工作階段旗標。 可與位元的 OR 運算子結合這些旗標 (&#124;)，如下所示：

- INTERNET_FLAG_RELOAD 從網路取得的資料，即使在本機快取。 這是預設旗標。

- 在本機或在任何閘道，請 INTERNET_FLAG_DONT_CACHE 不要快取的資料。

- INTERNET_FLAG_RAW_DATA 覆寫預設值，傳回的未經處理資料 ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) ftp 結構)。

- INTERNET_FLAG_SECURE 保護與安全通訊端層或 PCT 在網路上的交易 這個旗標適用於僅限 HTTP 要求。

- INTERNET_FLAG_EXISTING_CONNECT 如果可能的話，請重複使用現有的連線到伺服器新`FindFile`要求，而非建立新的工作階段，針對每個要求。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 若要取得延伸錯誤資訊，請呼叫 Win32 函式[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

之後呼叫`FindFile`若要擷取的第一個 FTP 檔案，您可以呼叫[FindNextFile](#findnextfile)來擷取後續的 FTP 檔案。

### <a name="example"></a>範例

  請參閱本主題中先前的範例。

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

呼叫此成員函式，以繼續檔案搜尋，開始藉由呼叫[FindFile](#findfile)成員函式。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

非零值，如果有多個檔案;如果找到該檔案的目錄中的最後一個，或發生錯誤，則為零。 若要取得延伸錯誤資訊，請呼叫 Win32 函式[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到該檔案是在目錄中，最後一個檔案，或如果沒有相符，就可以找到檔案，`GetLastError`函式會傳回 ERROR_NO_MORE_FILES。

### <a name="remarks"></a>備註

您必須呼叫此函式呼叫的任何屬性函式之前，至少一次 (請參閱[CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile))。

`FindNextFile` 包裝 Win32 函式[FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea)。

### <a name="example"></a>範例

  請參閱本主題前面的範例。

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

呼叫此成員函式，以取得指定之檔案的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

檔案和路徑的統一資源定位器 (URL)。

### <a name="remarks"></a>備註

`GetFileURL` 此成員函式類似[CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)，只不過它傳回的 URL 格式`ftp://moose/dir/file.txt`。

## <a name="see-also"></a>另請參閱

[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
