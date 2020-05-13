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
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373746"
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
|[CFtp檔案查找::CFtpFile查找](#cftpfilefind)|建構 `CFtpFileFind` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFtp 檔案尋找:尋找檔案](#findfile)|在 FTP 伺服器上查找檔。|
|[CFtp檔案查找:::尋找下一個檔案](#findnextfile)|繼續從上一個調用[FindFile](#findfile)的檔搜索。|
|[CFtpFile 查找::取得檔案網址](#getfileurl)|取得找到檔案的 URL,包括路徑。|

## <a name="remarks"></a>備註

`CFtpFileFind`包括開始搜尋、查找檔並返回有關該檔的 URL 或其他描述性資訊的成員函數。

其他MFC類專為互聯網和本地檔搜索包括[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind。](../../mfc/reference/cfilefind-class.md) 與`CFtpFileFind`結合這些類為用戶端提供了一個無縫機制來查找特定檔,而不管伺服器協定或檔案類型(本地電腦或遠端伺服器)。 請注意,沒有用於在 HTTP 伺服器上搜索的 MFC 類,因為 HTTP 不支援搜尋所需的直接檔操作。

有關如何使用`CFtpFileFind`和其他 WinInet 類別的詳細資訊,請參閱[使用 WinInet 使用 Internet 編程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="example"></a>範例

以下代碼演示如何枚舉 FTP 伺服器目前目錄中的所有檔。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtp檔案查找::CFtpFile查找

呼叫此成員函數以建構物件`CFtpFileFind`。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pConnection*<br/>
`CFtpConnection` 物件的指標。 您可以透過呼叫 CInternetSession 取得 FTP 連線[::取得 Ftp 連線](../../mfc/reference/cinternetsession-class.md#getftpconnection)。

*dwContext*<br/>
`CFtpFileFind`物件的上下文標識碼。 有關此參數的詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

mFC`CFtpFileFind`從 創建物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)`CFtpFileFind`物件向物件發送*dwContext*的預設值。 您可以重寫預設值,將上下文識別碼設定為您選擇的值。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

### <a name="example"></a>範例

  請參閱本主題前面的類概述中的示例。

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtp 檔案尋找:尋找檔案

調用此成員函數以查找 FTP 檔。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>參數

*pstrName*<br/>
指向要查找的檔名稱的字串的指標。 如果 NULL,則呼叫將執行通配符搜索 (*)。

*dwFlags*<br/>
描述如何處理此會話的標誌。 這些標誌可以與位或運算符 (&#124;) 組合,如下所示:

- INTERNET_FLAG_RELOAD從導線中獲取數據,即使它是本地快取的。 這是默認標誌。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何閘道中快取資料。

- INTERNET_FLAG_RAW_DATA覆蓋預設值以返回原始資料[(FTP WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)結構)。

- INTERNET_FLAG_SECURE使用安全套接字層或 PCT 保護線上的交易。 此標誌僅適用於 HTTP 請求。

- INTERNET_FLAG_EXISTING_CONNECT 如果可能,請重用與伺服器的現有連接以`FindFile`訪問 新請求,而不是為每個請求創建新會話。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>備註

調用`FindFile`以檢索第一個 FTP 檔後,可以調用[FindNextFile](#findnextfile)檢索後續 FTP 檔。

### <a name="example"></a>範例

  請參閱本主題中的較早示例。

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtp檔案查找:::尋找下一個檔案

呼叫此成員函數以繼續從調用[FindFile](#findfile)成員函數開始的檔搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>傳回值

如果檔更多,則非零;如果找到的檔是目錄中的最後一個檔或發生錯誤,則為零。 要取得延伸錯誤資訊,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的檔是目錄中的最後一個檔,或者找不到匹配的檔,則`GetLastError`函數將返回ERROR_NO_MORE_FILES。

### <a name="remarks"></a>備註

在調用任何屬性函數之前,必須至少調用此函數一次(請參閱[CFileFind:FindNextFile)。](../../mfc/reference/cfilefind-class.md#findnextfile)

`FindNextFile`包裝 Win32 函數[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>範例

  請參閱本主題前面的示例。

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFile 查找::取得檔案網址

呼叫此成員函數獲取指定檔的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

通用資源定位器 (URL) 的檔案和路徑。

### <a name="remarks"></a>備註

`GetFileURL`類似於成員函數[CFileFind::getFilePath,](../../mfc/reference/cfilefind-class.md#getfilepath)只不過它返回`ftp://moose/dir/file.txt`窗體 中的 URL。

## <a name="see-also"></a>另請參閱

[CFileFind 類別](../../mfc/reference/cfilefind-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
