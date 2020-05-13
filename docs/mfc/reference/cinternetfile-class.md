---
title: C 網際網路檔案類別
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372394"
---
# <a name="cinternetfile-class"></a>C 網際網路檔案類別

允許存取使用 Internet 協定的遠端系統上的檔案。

## <a name="syntax"></a>語法

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[C 網際網路檔案:C網際網路檔案](#cinternetfile)|建構 `CInternetFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 網際網路檔::中止](#abort)|關閉檔案,忽略所有警告和錯誤。|
|[C 網際網路檔案:關閉](#close)|關閉和`CInternetFile`釋放其資源。|
|[C網際網路檔:Flush](#flush)|刷新寫入緩衝區的內容,並確保記憶體中的數據寫入目標計算機。|
|[C 網際網路檔案:取得長度](#getlength)|返回檔的大小。|
|[C 網際網路檔案:閱讀](#read)|讀取指定的位元組數。|
|[C互聯網檔::閱讀字串](#readstring)|讀取字元流。|
|[C 網際網路檔:尋找](#seek)|將指標重新置放到打開的檔案中。|
|[C 網際網路檔::設定讀取緩衝區大小](#setreadbuffersize)|設置將讀取數據的緩衝區的大小。|
|[C 網際網路檔::設定寫入緩衝區大小](#setwritebuffersize)|設置將寫入數據的緩衝區的大小。|
|[C網際網路檔:寫入](#write)|寫入指定的位元組數。|
|[C網際網路檔::寫入字串](#writestring)|將 null 終止的字串寫入檔案。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C互聯網檔::管理員 HINTERNET](#operator_hinternet)|互聯網句柄的鑄造運算符。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[C互聯網檔::m_hFile](#m_hfile)|檔的句柄。|

## <a name="remarks"></a>備註

為[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile 檔案](../../mfc/reference/cgopherfile-class.md)類提供基類。 您從不直接創建`CInternetFile`物件。 相反,通過調用[CGopherConnection::打開檔](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHTTPConnection::打開請求](../../mfc/reference/chttpconnection-class.md#openrequest),創建其派生類之一的物件。 您還可以透過除錯`CInternetFile`[CFtpConnection::打開檔案](../../mfc/reference/cftpconnection-class.md#openfile)來建立物件。

成員`CInternetFile``Open`函`LockRange``UnlockRange`數,`Duplicate`與`CInternetFile`未為實現 。 如果在`CInternetFile`物件上調用這些函數,您將取得[CNot 支援異常](../../mfc/reference/cnotsupportedexception-class.md)。

要瞭解有關如何`CInternetFile`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>C 網際網路檔::中止

關閉與此物件關聯的檔,並使該文件無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果在銷毀物件之前尚未關閉該檔,析構函數將為您關閉該檔。

在處理異常時,`Abort`從兩個重要方面與[Close](#close)不同。 首先,函數`Abort`不會在失敗時引發異常,因為它會忽略故障。 其次,`Abort`如果檔案尚未開啟或以前已關閉,則不**斷言**。

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>C 網際網路檔案:C網際網路檔案

創建`CInternetFile`物件時將調用此成員函數。

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>參數

*hFile*<br/>
互聯網檔的句柄。

*pstrFile 名稱*<br/>
指向包含檔名的字串的指標。

*pConnection*<br/>
指向[CInternetConnect](../../mfc/reference/cinternetconnection-class.md)物件的指標。

*bReadMode*<br/>
指示檔是否為唯讀檔。

*h 工作階段*<br/>
互聯網會話的句柄。

*pstrServer*<br/>
指向包含伺服器名稱的字串的指標。

*dwContext*<br/>
`CInternetFile`物件的上下文標識碼。 有關上下文識別碼的詳細資訊,請參閱[WinInet 基礎知識](../../mfc/wininet-basics.md)。

### <a name="remarks"></a>備註

您從不直接創建`CInternetFile`物件。 相反,通過調用[CGopherConnection::打開檔](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHTTPConnection::打開請求](../../mfc/reference/chttpconnection-class.md#openrequest),創建其派生類之一的物件。 您還可以透過除錯`CInternetFile`[CFtpConnection::打開檔案](../../mfc/reference/cftpconnection-class.md#openfile)來建立物件。

## <a name="cinternetfileclose"></a><a name="close"></a>C 網際網路檔案:關閉

關閉和`CInternetFile`釋放其任何資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果檔已打開以進行寫入,則存在對[Flush](#flush)的隱式調用,以確保將所有緩衝數據寫入主機。 使用完檔`Close`後,應調用。

## <a name="cinternetfileflush"></a><a name="flush"></a>C網際網路檔:Flush

調用此成員函數以刷新寫入緩衝區的內容。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

用於`Flush`確保記憶體中的所有數據實際上已寫入目標計算機,並確保與主機的事務已完成。 `Flush`僅在打開用於寫入`CInternetFile`的物件上有效。

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>C 網際網路檔案:取得長度

返回檔的大小。

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>C互聯網檔::m_hFile

與此物件關聯的檔的句柄。

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>C互聯網檔::管理員 HINTERNET

使用此運算元獲取當前 Internet 工作階段的 Windows 句柄。

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>C 網際網路檔案:閱讀

呼叫此成員函數讀取到給定的記憶體中,從*lpvBuf*開始,指定位元組數*nCount*。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
將檔案資料讀取到的記憶體位址指標。

*n( N) Count*<br/>
要寫入的位元組數目。

### <a name="return-value"></a>傳回值

傳輸至緩衝區的位元組數目。 如果達到檔結尾,則返回值可能小於*nCount。*

### <a name="remarks"></a>備註

函數傳回實際讀取的位元組數 - 如果檔案結束時,該數位可能小於*nCount。* 如果在讀取檔時發生錯誤,該函數將引發描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。 請注意，讀取超過檔案結尾不被視為錯誤，而且會擲回任何例外狀況。

為了確保檢索所有資料,應用程式必須繼續調用 方法`CInternetFile::Read`, 直到該方法返回零。

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>C互聯網檔::閱讀字串

呼叫此成員函數以讀取字元流,直到它找到換行元。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>參數

*普斯特*<br/>
指向將接收正在讀取的行的字串的指標。

*nMax*<br/>
要讀取的最大字元數。

*rString*<br/>
對接收讀取行的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用。

### <a name="return-value"></a>傳回值

指向從[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件檢索的普通數據的緩衝區的指標。 無論傳遞給此方法的緩衝區數據類型如何,它都會對數據執行任何操作(例如,轉換為 Unicode),因此必須將返回的數據映射到預期的結構,就像返回**void**<strong>\*</strong>類型一樣。

如果未讀取任何數據就到達了文件結尾;或者,如果布爾,如果到達檔結尾而不讀取任何資料。"

### <a name="remarks"></a>備註

函數將生成的行放入*pstr*參數引用的記憶體中。 當它達到*nMax*指定的字元的最大數量時,它將停止讀取字元。 緩衝區始終接收終止空字元。

如果不首先呼叫`ReadString` [SetReadBufferSize,](#setreadbuffersize)則呼叫時將獲得 4096 位元組的緩衝區。

## <a name="cinternetfileseek"></a><a name="seek"></a>C 網際網路檔:尋找

呼叫此成員函數以重新置放以前打開的檔中的指標。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>參數

*L 位移*<br/>
偏移以位元組為單位,以移動檔中的讀/寫指標。

*n 從*<br/>
偏移的相對參照。 必須為下列其中一個值：

- `CFile::begin`從文件的開頭向前移動檔指標*lOff*位元組。

- `CFile::current`從檔案中的當前位置移動檔指標*lOff*位元組。

- `CFile::end`從檔末尾移動檔指標*lOff*位元組。 *lOff*必須是負的才能查找到現有檔中;正值將查找檔末尾。

### <a name="return-value"></a>傳回值

如果請求的位置是合法的,則從文件開頭的新位元組偏移量;否則,該值將未定義,並引發[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

該`Seek`函數允許通過絕對或相對地將指標移動指定數量來隨機存取檔的內容。 在查找過程中實際上不會讀取任何數據。

此時,僅支援與`CHttpFile`對象關聯的數據調用此成員函數。 FTP 或 gopher 請求不支援它。 如果您呼叫`Seek`這些不支援的服務之一,它將將您傳回 Win32 錯誤代碼ERROR_INTERNET_INVALID_OPERATION。

打開檔時,檔指標位於檔開頭的偏移 0。

> [!NOTE]
> 使用`Seek`可能會導致隱式呼叫[Flush](#flush)。

### <a name="example"></a>範例

  請參閱基類實現的範例[(CFile::seek)。](../../mfc/reference/cfile-class.md#seek)

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>C 網際網路檔::設定讀取緩衝區大小

調用此成員函數以設置`CInternetFile`派生物件使用的臨時讀取緩衝區的大小。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>參數

*nReadSize*<br/>
需要的緩衝區大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

基礎 WinInet API 不執行緩衝,因此請選擇允許應用程式高效讀取數據的緩衝區大小,而不考慮要讀取的數據量。 如果每次對[Read](#read)的調用通常涉及大量數據(例如,四個或更多 KB),則不應需要緩衝區。 但是,如果您調用`Read`以獲取小塊數據,或者使用[ReadString](#readstring)一次讀取單個行,則讀取緩衝區可提高應用程式性能。

默認情況下,`CInternetFile`物件不提供任何用於讀取的緩衝。 如果調用此成員函數,則必須確保該檔已打開以進行讀取訪問。

您可以隨時增加緩衝區大小,但收縮緩衝區將不起作用。 如果調用[ReadString](#readstring)`SetReadBufferSize`而不進行 第一次調用,您將獲得 4096 位元組的緩衝區。

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>C 網際網路檔::設定寫入緩衝區大小

調用此成員函數以設置`CInternetFile`派生物件使用的臨時寫入緩衝區的大小。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>參數

*nWriteSize*<br/>
以位元組為單位的緩衝區大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

基礎 WinInet API 不執行緩衝,因此請選擇允許應用程式高效寫入數據的緩衝區大小,而不考慮要寫入的數據量。 如果每次對[Write](#write)的調用通常涉及大量數據(例如,一次四個或更多千位元組),則不應需要緩衝區。 但是,如果調用[Write](#write)來寫入小塊數據,則寫入緩衝區會提高應用程式的性能。

默認情況下,`CInternetFile`物件不提供任何用於寫入的緩衝。 如果調用此成員函數,則必須確保該檔已打開以進行寫入訪問。 您可以隨時更改寫入緩衝區的大小,但這樣做會導致隱式呼叫[Flush](#flush)。

## <a name="cinternetfilewrite"></a><a name="write"></a>C網際網路檔:寫入

呼叫此成員函數寫入給定的記憶體 *,lpvBuf,* 指定數量的位*元組 ,nCount*。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
指向要寫入的第一個字節的指標。

*n( N) Count*<br/>
指定要寫入的位元組數。

### <a name="remarks"></a>備註

如果在寫入數據時發生任何錯誤,該函數將引發描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>C網際網路檔::寫入字串

此函數將一個 null 終止的字串寫入關聯的檔。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>參數

*普斯特*<br/>
指向包含要寫入內容的字串的指標。

### <a name="remarks"></a>備註

如果在寫入數據時發生任何錯誤,該函數將引發描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

## <a name="see-also"></a>另請參閱

[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)
