---
title: CInternetFile 類別
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
ms.openlocfilehash: 68a0a0f35d1a1f4519401080f9f207bf76c87079
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418549"
---
# <a name="cinternetfile-class"></a>CInternetFile 類別

允許存取使用網際網路通訊協定的遠端系統上的檔案。

## <a name="syntax"></a>語法

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CInternetFile：： CInternetFile](#cinternetfile)|建構 `CInternetFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInternetFile：： Abort](#abort)|關閉檔案，忽略所有警告和錯誤。|
|[CInternetFile：： Close](#close)|關閉 `CInternetFile` 並釋放其資源。|
|[CInternetFile：： Flush](#flush)|排清寫入緩衝區的內容，並確定記憶體中的資料已寫入目的電腦。|
|[CInternetFile：： GetLength](#getlength)|傳回檔案的大小。|
|[CInternetFile：： Read](#read)|讀取指定的位元組數。|
|[CInternetFile：： ReadString](#readstring)|讀取字元的資料流程。|
|[CInternetFile：： Seek](#seek)|重新置放已開啟檔案中的指標。|
|[CInternetFile：： SetReadBufferSize](#setreadbuffersize)|設定將讀取資料的緩衝區大小。|
|[CInternetFile：： SetWriteBufferSize](#setwritebuffersize)|設定將寫入資料的緩衝區大小。|
|[CInternetFile：： Write](#write)|寫入指定的位元組數目。|
|[CInternetFile：： WriteString](#writestring)|將以 null 結束的字串寫入至檔案。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CInternetFile：： operator HINTERNET](#operator_hinternet)|網際網路控制碼的轉換運算子。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CInternetFile：： m_hFile](#m_hfile)|檔案的控制碼。|

## <a name="remarks"></a>備註

提供[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile](../../mfc/reference/cgopherfile-class.md)檔案類別的基類。 您永遠不會直接建立 `CInternetFile` 物件。 相反地，請呼叫[CGopherConnection：： OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：： OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)，以建立其衍生類別之一的物件。 您也可以藉由呼叫[CFtpConnection：： OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)來建立 `CInternetFile` 物件。

`CInternetFile` 成員函式 `Open`、`LockRange`、`UnlockRange`和 `Duplicate` 不會針對 `CInternetFile`執行。 如果您在 `CInternetFile` 物件上呼叫這些函式，將會取得[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

若要深入瞭解 `CInternetFile` 如何與其他 MFC 網際網路類別搭配運作，請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>需求

**標頭：** afxinet.h。h

##  <a name="abort"></a>CInternetFile：： Abort

關閉與此物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果您在終結物件之前尚未關閉檔案，則此析構函式會為您關閉該檔案。

在處理例外狀況時，`Abort` 兩個重要的方式不同于[關閉](#close)。 首先，`Abort` 函數不會在失敗時擲回例外狀況，因為它會忽略失敗。 第二，如果檔案尚未開啟或先前已關閉， **`Abort` 不會**判斷提示。

##  <a name="cinternetfile"></a>CInternetFile：： CInternetFile

建立 `CInternetFile` 物件時，會呼叫這個成員函式。

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
網際網路檔案的控制碼。

*pstrFileName*<br/>
包含檔案名之字串的指標。

*pConnection*<br/>
[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件的指標。

*bReadMode*<br/>
指出檔案是否為唯讀。

*hSession*<br/>
網際網路會話的控制碼。

*pstrServer*<br/>
包含伺服器名稱之字串的指標。

*dwCoNtext*<br/>
`CInternetFile` 物件的內容識別碼。 如需內容識別碼的詳細資訊，請參閱[WinInet 基本概念](../../mfc/wininet-basics.md)。

### <a name="remarks"></a>備註

您永遠不會直接建立 `CInternetFile` 物件。 相反地，請呼叫[CGopherConnection：： OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：： OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)，以建立其衍生類別之一的物件。 您也可以藉由呼叫[CFtpConnection：： OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)來建立 `CInternetFile` 物件。

##  <a name="close"></a>CInternetFile：： Close

關閉 `CInternetFile` 並釋放其任何資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果檔案已開啟以供寫入，則會隱含地呼叫來進行排清[，以確保](#flush)所有緩衝的資料都會寫入主機。 當您完成使用檔案時，應該呼叫 `Close`。

##  <a name="flush"></a>CInternetFile：： Flush

呼叫這個成員函式，以排清寫入緩衝區的內容。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

使用 `Flush`，確保記憶體中的所有資料都已確實寫入目的電腦，並確保您的主機電腦交易已完成。 `Flush` 只有在開啟以供寫入的 `CInternetFile` 物件上才有效。

##  <a name="getlength"></a>CInternetFile：： GetLength

傳回檔案的大小。

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>CInternetFile：： m_hFile

與這個物件相關聯之檔案的控制碼。

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>CInternetFile：： operator HINTERNET

使用此運算子來取得目前網際網路會話的 Windows 控制碼。

```
operator HINTERNET() const;
```

##  <a name="read"></a>CInternetFile：： Read

呼叫這個成員函式以讀入給定的記憶體，從*lpvBuf*開始，指定的位元組數目， *nCount*。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
將檔案資料讀取到的記憶體位址指標。

*nCount*<br/>
要寫入的位元組數目。

### <a name="return-value"></a>傳回值

傳輸至緩衝區的位元組數目。 如果已到達檔案結尾，則傳回值可能小於*nCount* 。

### <a name="remarks"></a>備註

函式會傳回實際讀取的位元組數目，如果檔案結束，則為可能小於*nCount*的數位。 如果在讀取檔案時發生錯誤，函式會擲回描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。 請注意，讀取超過檔案結尾不被視為錯誤，而且會擲回任何例外狀況。

為了確保所有資料都已取得，應用程式必須繼續呼叫 `CInternetFile::Read` 方法，直到該方法傳回零為止。

##  <a name="readstring"></a>CInternetFile：： ReadString

呼叫這個成員函式可讀取字元的資料流程，直到找到分行符號為止。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>參數

*pstr*<br/>
字串的指標，會接收讀取的行。

*N 上限*<br/>
要讀取的最大字元數。

*rString*<br/>
可接收讀取行之[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考。

### <a name="return-value"></a>傳回值

緩衝區的指標，其中包含從[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件抓取的純資料。 不論傳遞給這個方法的緩衝區資料類型為何，它都不會對資料執行任何操作（例如，轉換成 Unicode），因此您必須將傳回的資料對應至您預期的結構，如同傳回**void** <strong>\*</strong>類型一樣。

如果已到達檔案結尾，但未讀取任何資料，則為 Null。或者，如果布林值為 FALSE，則為，如果已到達檔案結尾，則不讀取任何資料。

### <a name="remarks"></a>備註

函式會將產生的行放入*pstr*參數所參考的記憶體中。 它會在達到*n 上限*所指定的最大字元數目時停止讀取字元。 緩衝區一律會接收終止的 null 字元。

如果您在未先呼叫[SetReadBufferSize](#setreadbuffersize)的情況下呼叫 `ReadString`，您會收到4096個位元組的緩衝區。

##  <a name="seek"></a>CInternetFile：： Seek

呼叫這個成員函式，將指標重新置放在先前開啟的檔案中。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>參數

*lOffset*<br/>
位移（以位元組為單位），用來移動檔案中的讀取/寫入指標。

*n*<br/>
位移的相對參考。 必須為下列其中一個值：

- `CFile::begin` 將檔案指標*lOff*位元組從檔案的開頭往前移動。

- `CFile::current` 從檔案中的目前位置移動檔案指標*lOff*位元組。

- `CFile::end` 從檔案結尾移動檔案指標*lOff*位元組。 *lOff*必須是負數，才能搜尋現有的檔案;正數值會搜尋超過檔案結尾。

### <a name="return-value"></a>傳回值

如果要求的位置是合法的，則為從檔案開頭起算的新位元組位移。否則，此值會是未定義的，而且會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

`Seek` 函式會將指標移到指定的數量（絕對或相對），以允許隨機存取檔案的內容。 搜尋期間不會實際讀取任何資料。

此時，只有與 `CHttpFile` 物件相關聯的資料，才支援呼叫這個成員函式。 不支援 FTP 或 gopher 要求。 如果您為其中一個不支援的服務呼叫 `Seek`，它會將您傳回 Win32 錯誤碼 ERROR_INTERNET_INVALID_OPERATION。

當檔案開啟時，檔案指標會在檔案開頭的位移0。

> [!NOTE]
>  使用 `Seek` 可能會導致隱含的[清除](#flush)呼叫。

### <a name="example"></a>範例

  請參閱基類實作為範例（ [CFile：： Seek](../../mfc/reference/cfile-class.md#seek)）。

##  <a name="setreadbuffersize"></a>CInternetFile：： SetReadBufferSize

呼叫這個成員函式，以設定 `CInternetFile`衍生物件所使用的暫存讀取緩衝區大小。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>參數

*nReadSize*<br/>
需要的緩衝區大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

基礎 WinInet Api 不會執行緩衝處理，因此請選擇緩衝區大小，讓您的應用程式有效率地讀取資料，而不論要讀取的資料量為何。 如果每個[讀取](#read)的呼叫通常牽涉到大量的資料 aount （例如，四個或更多的 kb），您應該不需要緩衝區。 不過，如果您呼叫 `Read` 來取得小型資料區塊，或使用[ReadString](#readstring)一次讀取個別的行，則讀取緩衝區會改善應用程式效能。

根據預設，`CInternetFile` 物件不會提供任何緩衝處理來讀取。 如果您呼叫此成員函式，您必須確定已開啟檔案以供讀取存取。

您可以隨時增加緩衝區大小，但壓縮緩衝區不會有任何作用。 如果您在未先呼叫 `SetReadBufferSize`的情況下呼叫[ReadString](#readstring) ，則會收到4096個位元組的緩衝區。

##  <a name="setwritebuffersize"></a>CInternetFile：： SetWriteBufferSize

呼叫這個成員函式，以設定 `CInternetFile`衍生物件所使用之暫存寫入緩衝區的大小。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>參數

*nWriteSize*<br/>
以位元組為單位的緩衝區大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

基礎 WinInet Api 不會執行緩衝處理，因此請選擇可讓您的應用程式有效率地寫入資料的緩衝區大小，而不論要寫入的資料量為何。 如果每個[寫入](#write)的呼叫通常牽涉到大量的資料（例如，一次四個或更多的 kb），您應該不需要緩衝區。 不過，如果您呼叫[write](#write)來寫入小型資料區塊，寫入緩衝區可改善應用程式的效能。

根據預設，`CInternetFile` 物件不會提供任何用於寫入的緩衝處理。 如果您呼叫此成員函式，您必須確定已開啟檔案以供寫入存取。 您可以隨時變更寫入緩衝區的大小，但這麼做會導致隱含的[清除](#flush)呼叫。

##  <a name="write"></a>CInternetFile：： Write

呼叫這個成員函式，以寫入給定的記憶體*lpvBuf*，指定的位元組數目， *nCount*。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
要寫入的第一個位元組指標。

*nCount*<br/>
指定要寫入的位元組數目。

### <a name="remarks"></a>備註

如果寫入資料時發生任何錯誤，函式會擲回描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

##  <a name="writestring"></a>CInternetFile：： WriteString

此函式會將以 null 結束的字串寫入相關聯的檔案。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>參數

*pstr*<br/>
包含要寫入之內容的字串指標。

### <a name="remarks"></a>備註

如果寫入資料時發生任何錯誤，函式會擲回描述錯誤的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

## <a name="see-also"></a>另請參閱

[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)
