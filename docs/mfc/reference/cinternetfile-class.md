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
ms.openlocfilehash: 309d4210f72f7ecd83ed6a8eb79874a1c8170d59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586871"
---
# <a name="cinternetfile-class"></a>CInternetFile 類別

允許在使用網際網路通訊協定的遠端系統上的檔案的存取權。

## <a name="syntax"></a>語法

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|建構 `CInternetFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInternetFile::Abort](#abort)|關閉檔案，並忽略所有的警告和錯誤。|
|[CInternetFile::Close](#close)|關閉`CInternetFile`並釋放其資源。|
|[CInternetFile::Flush](#flush)|排清寫入緩衝區的內容，並確保記憶體中的資料會寫入到目標電腦。|
|[CInternetFile::GetLength](#getlength)|傳回檔案的大小。|
|[Cinternetfile:: Read](#read)|讀取指定的位元組數。|
|[CInternetFile::ReadString](#readstring)|讀取字元資料流。|
|[CInternetFile::Seek](#seek)|指標重新置放在開啟的檔案。|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|設定緩衝區的大小會讀取資料。|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|設定資料將會寫入緩衝區的大小。|
|[CInternetFile::Write](#write)|寫入指定的位元組數目。|
|[CInternetFile::WriteString](#writestring)|以 null 結束的字串寫入檔案。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CInternetFile::operator HINTERNET](#operator_hinternet)|轉型運算子，針對網際網路的控制代碼。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|檔案控制代碼。|

## <a name="remarks"></a>備註

提供的基底類別[CHttpFile](../../mfc/reference/chttpfile-class.md)並[CGopherFile](../../mfc/reference/cgopherfile-class.md)檔案類別。 您永遠不會建立`CInternetFile`直接物件。 相反地，建立物件的其中一個衍生的類別，藉由呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或是[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您也可以建立`CInternetFile`藉由呼叫物件[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。

`CInternetFile`成員函式`Open`， `LockRange`， `UnlockRange`，並`Duplicate`並未實作`CInternetFile`。 如果您在上呼叫這些函式`CInternetFile`物件，您會收到[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

若要進一步了解如何`CInternetFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="abort"></a>  CInternetFile::Abort

關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果您已不關閉檔案，然後再終結物件，解構函式會關閉它為您。

處理例外狀況，當`Abort`有別[關閉](#close)兩種重要方式。 首先，`Abort`函式不會擲回例外狀況失敗因為它會忽略失敗。 第二個，`Abort`則否**ASSERT**如果檔案尚未開啟，或先前已關閉。

##  <a name="cinternetfile"></a>  CInternetFile::CInternetFile

此成員函式時，會呼叫`CInternetFile`建立物件。

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
網際網路檔案控制代碼。

*pstrFileName*<br/>
包含檔案名稱的字串指標。

*pConnection*<br/>
指標[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件。

*bReadMode*<br/>
指出檔案是否為唯讀。

*hSession*<br/>
網際網路工作階段控制代碼。

*pstrServer*<br/>
包含伺服器名稱的字串指標。

*dwContext*<br/>
內容識別碼`CInternetFile`物件。 請參閱[WinInet 基本概念](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

### <a name="remarks"></a>備註

您永遠不會建立`CInternetFile`直接物件。 相反地，建立物件的其中一個衍生的類別，藉由呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或是[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您也可以建立`CInternetFile`藉由呼叫物件[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。

##  <a name="close"></a>  CInternetFile::Close

關閉`CInternetFile`並釋放任何它的資源。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果開啟檔案進行寫入，則隱含呼叫[排清](#flush)以確保所有緩衝資料寫入至主機。 您應該呼叫`Close`當您完成使用檔案。

##  <a name="flush"></a>  CInternetFile::Flush

呼叫此成員函式，以排清寫入緩衝區的內容。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

使用`Flush`對確保在記憶體中的所有資料到目標電腦中實際上已都寫入，以確保您具有主機上的交易完成。 `Flush` 才有效上`CInternetFile`物件開啟供寫入。

##  <a name="getlength"></a>  CInternetFile::GetLength

傳回檔案的大小。

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>  CInternetFile::m_hFile

與這個物件相關聯的檔案控制代碼。

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>  CInternetFile::operator HINTERNET

您可以使用這個運算子來取得目前的網際網路工作階段的 Windows 控制代碼。

```
operator HINTERNET() const;
```

##  <a name="read"></a>  Cinternetfile:: Read

呼叫此成員函式，讀取至指定的記憶體，起價*lpvBuf*，則指定的位元組數目*nCount*。

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

傳輸至緩衝區的位元組數目。 傳回的值可能會小於*nCount*如果已到達檔案結尾。

### <a name="remarks"></a>備註

函數會傳回實際讀取的位元組數目 — 可能是數字小於*nCount*如果檔案結束。 如果在讀取檔案時發生錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。 請注意，讀取超過檔案結尾不被視為錯誤，而且會擲回任何例外狀況。

若要確保擷取所有的資料，應用程式必須繼續呼叫`CInternetFile::Read`方法，直到此方法會傳回零。

##  <a name="readstring"></a>  CInternetFile::ReadString

呼叫此成員函式可讀取的字元資料流，直到找到新行字元。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>參數

*pstr*<br/>
將會收到所讀取的行的字串指標。

*nMax*<br/>
要讀取的字元數目上限。

*rString*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收讀取的行的物件。

### <a name="return-value"></a>傳回值

包含從擷取的純文字資料緩衝區的指標[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件。 不論傳遞給這個方法之緩衝區的資料類型，它不會執行任何操作資料 （例如，轉換成 Unicode） 中，因此您必須將傳回的資料對應至結構，您預期，如同**void** <strong>\*</strong> 傳回型別。

如果沒有讀取任何資料; 達到檔案結尾，則為 NULL或者，如果布林值，如果檔案結尾，則為 FALSE。 已達到未讀取任何資料。

### <a name="remarks"></a>備註

此函式會產生列放入所參考的記憶體*pstr*參數。 它會停止讀取字元達到指定的字元的數目上限時*nMax*。 緩衝區一律會收到結束的 null 字元。

如果您呼叫`ReadString`情況下先呼叫[SetReadBufferSize](#setreadbuffersize)，您會收到 4096 個位元組的緩衝區。

##  <a name="seek"></a>  CInternetFile::Seek

呼叫此成員函式，將指標重新置放在先前開啟的檔案。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>參數

*lOffset*<br/>
以位元組為單位來讀取/寫入將指標移至檔案中的位移。

*nFrom*<br/>
相對位移的參考。 必須是下列值之一：

- `CFile::begin` 檔案指標移到*lOff*轉送從檔案開頭的位元組。

- `CFile::current` 檔案指標移到*lOff*位元組從目前位置在檔案中。

- `CFile::end` 檔案指標移到*lOff*從檔案結尾的位元組。 *lOff*必須是要搜尋到現有的負數檔案; 正整數值將會搜尋超過檔案結尾。

### <a name="return-value"></a>傳回值

新要求的位置是合法的; 如果從檔案開頭位移的位元組否則，值就是未定義並[CInternetException](../../mfc/reference/cinternetexception-class.md)物件就會擲回。

### <a name="remarks"></a>備註

`Seek`函式允許隨機存取檔案內容移動指標，即可指定的數量，具有絕對或相對。 在搜尋期間實際不讀取任何資料。

在此階段中，呼叫此成員函式僅適用於相關聯的資料`CHttpFile`物件。 不支援 FTP 或 gopher 的要求。 如果您呼叫`Seek`針對其中一個這些不支援的服務，它會傳回您 ERROR_INTERNET_INVALID_OPERATION Win32 錯誤碼。

開啟檔案時，檔案指標時，位移 0，檔案開頭處。

> [!NOTE]
>  使用`Seek`可能會導致隱含呼叫[排清](#flush)。

### <a name="example"></a>範例

  基底類別實作範例，請參閱 ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek))。

##  <a name="setreadbuffersize"></a>  CInternetFile::SetReadBufferSize

呼叫此成員函式設定所使用的暫時讀取緩衝區的大小`CInternetFile`-衍生物件。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>參數

*nReadSize*<br/>
需要的緩衝區大小 (以位元組為單位)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

### <a name="remarks"></a>備註

基礎的 WinInet Api 請勿執行緩衝處理，因此請選擇可讓您的應用程式，不論要讀取的資料量，有效地讀取資料的緩衝區大小。 如果每個呼叫[讀取](#read)通常牽涉到大型 aount 的資料 （例如，四個或多個 kb 為單位），您應該不需要緩衝區。 不過，如果您呼叫`Read`以取得小塊資料，或如果您使用[ReadString](#readstring)一次讀取個別的線條，然後讀取的緩衝區可改善應用程式的效能。

根據預設，`CInternetFile`物件不提供任何緩衝讀取。 如果您呼叫此成員函式時，您必須確定已開啟檔案進行讀取存取。

您可以隨時增加緩衝區大小，但壓縮緩衝區會有任何作用。 如果您呼叫[ReadString](#readstring)情況下先呼叫`SetReadBufferSize`，您會收到 4096 個位元組的緩衝區。

##  <a name="setwritebuffersize"></a>  CInternetFile::SetWriteBufferSize

呼叫此成員函式設定所使用的暫時寫入緩衝區的大小`CInternetFile`-衍生物件。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>參數

*nWriteSize*<br/>
以位元組為單位的緩衝區大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

### <a name="remarks"></a>備註

基礎的 WinInet Api 不會執行緩衝處理，因此選擇可讓您的應用程式有效率地不論要寫入的資料量的資料寫入的緩衝區大小。 如果每個呼叫[寫入](#write)通常牽涉到大量的資料 (例如，四個 kb 或更多一次），您應該不需要緩衝區。 不過，如果您呼叫[寫入](#write)撰寫小塊資料，寫入緩衝區可以改善您的應用程式效能。

根據預設，`CInternetFile`物件不提供寫入任何緩衝。 如果您呼叫此成員函式時，您必須確定已開啟檔案進行寫入存取權。 您可以在任何時間，變更寫入緩衝區的大小，但這麼做會導致隱含呼叫[排清](#flush)。

##  <a name="write"></a>  CInternetFile::Write

呼叫此成員函式，將寫入至指定的記憶體中， *lpvBuf*，則指定的位元組數目*nCount*。

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

如果在寫入資料時，就會發生任何錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。

##  <a name="writestring"></a>  CInternetFile::WriteString

此函式會將以 null 結束的字串寫入相關聯的檔案。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>參數

*pstr*<br/>
字串，包含要寫入的內容指標。

### <a name="remarks"></a>備註

如果在寫入資料時，就會發生任何錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。

## <a name="see-also"></a>另請參閱

[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)
