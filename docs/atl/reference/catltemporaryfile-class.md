---
title: CAtlTemporaryFile 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: d6a7a61d1886a264f8575e8d7325d6639d21338d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497706"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 類別

這個類別會提供建立和使用暫存檔案的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlTemporaryFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|建構函式。|
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlTemporaryFile::Close](#close)|呼叫這個方法來關閉暫存檔案, 並刪除其內容或將其儲存在指定的檔案名底下。|
|[CAtlTemporaryFile::Create](#create)|呼叫這個方法以建立暫存檔案。|
|[CAtlTemporaryFile::Flush](#flush)|呼叫這個方法, 以強制將檔案緩衝區中剩餘的任何資料寫入暫存檔案。|
|[CAtlTemporaryFile::GetPosition](#getposition)|呼叫這個方法, 以取得目前的檔案指標位置。|
|[CAtlTemporaryFile::GetSize](#getsize)|呼叫此方法以取得暫存檔案的大小 (以位元組為單位)。|
|[CAtlTemporaryFile::HandsOff](#handsoff)|呼叫這個方法, 將檔案與`CAtlTemporaryFile`物件取消關聯。|
|[CAtlTemporaryFile::HandsOn](#handson)|呼叫這個方法來開啟現有的暫存檔案, 並將指標放在檔案結尾。|
|[CAtlTemporaryFile::LockRange](#lockrange)|呼叫這個方法來鎖定檔案中的區域, 以防止其他處理常式存取它。|
|[CAtlTemporaryFile::Read](#read)|呼叫這個方法, 從檔案指標所指示的位置開始, 讀取暫存檔中的資料。|
|[CAtlTemporaryFile::Seek](#seek)|呼叫這個方法來移動暫存檔案的檔案指標。|
|[CAtlTemporaryFile::SetSize](#setsize)|呼叫這個方法來設定暫存檔案的大小。|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|呼叫這個方法, 以傳回暫存檔案的名稱。|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定暫存檔案的區域。|
|[CAtlTemporaryFile::Write](#write)|呼叫這個方法, 從檔案指標所指示的位置開始, 將資料寫入至暫存檔。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlTemporaryFile:: operator 控制碼](#operator_handle)|傳回暫存檔案的控制碼。|

## <a name="remarks"></a>備註

`CAtlTemporaryFile`可讓您輕鬆地建立和使用暫存檔案。 檔案會自動命名為、已開啟、已關閉和已刪除。 如果檔案在關閉後需要檔案內容, 則可以儲存到具有指定名稱的新檔案。

## <a name="requirements"></a>需求

**標頭:** atlfile。h

## <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

建構函式。

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>備註

在對[CAtlTemporaryFile:: Create](#create)進行呼叫之前, 檔案實際上不會開啟。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile

解構函式。

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>備註

此析構函式會呼叫[CAtlTemporaryFile:: Close](#close)。

##  <a name="close"></a>CAtlTemporaryFile:: Close

呼叫這個方法來關閉暫存檔案, 並刪除其內容或將其儲存在指定的檔案名底下。

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>參數

*szNewName*<br/>
要在其中儲存暫存檔案內容的新檔案名稱。 如果這個引數為 Null, 則會刪除暫存檔案的內容。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="create"></a>CAtlTemporaryFile:: Create

呼叫這個方法以建立暫存檔案。

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>參數

*pszDir*<br/>
暫存檔案的路徑。 如果這是 Null, 則會呼叫[GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)來指派路徑。

*dwDesiredAccess*<br/>
所需的存取權。 請參閱 Windows SDK 中[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)的*dwDesiredAccess* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="flush"></a>CAtlTemporaryFile:: Flush

呼叫這個方法, 以強制將檔案緩衝區中剩餘的任何資料寫入暫存檔案。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

類似于[CAtlTemporaryFile:: HandsOff](#handsoff), 但不會關閉檔案。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition

呼叫這個方法, 以取得目前的檔案指標位置。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
以位元組為單位的位置。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

若要變更檔案指標位置, 請使用[CAtlTemporaryFile:: Seek](#seek)。

##  <a name="getsize"></a>CAtlTemporaryFile:: GetSize

呼叫此方法以取得暫存檔案的大小 (以位元組為單位)。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>參數

*nLen*<br/>
檔案中的位元組數目。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff

呼叫這個方法, 將檔案與`CAtlTemporaryFile`物件取消關聯。

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`HandsOff`和[CAtlTemporaryFile:: HandsOn](#handson)是用來將檔案與物件解除關聯, 並在需要時重新附加。 `HandsOff`會強制將檔案緩衝區中剩餘的任何資料寫入暫存檔案, 然後關閉檔案。 如果您想要永久關閉和刪除檔案, 或想要以指定的名稱關閉並保留檔案的內容, 請使用[CAtlTemporaryFile:: close](#close)。

##  <a name="handson"></a>CAtlTemporaryFile::HandsOn

呼叫這個方法來開啟現有的暫存檔案, 並將指標放在檔案結尾。

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CAtlTemporaryFile:: HandsOff](#handsoff)和`HandsOn`用來將檔案與物件解除關聯, 並在需要時重新附加。

##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange

呼叫這個方法來鎖定暫存檔案中的區域, 以防止其他進程存取它。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
檔案中應該開始鎖定的位置。

*nCount*<br/>
要鎖定的位元組範圍長度。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定一個以上的檔案區域, 但不允許重迭的區域。 若要成功解除鎖定區域, 請使用[CAtlTemporaryFile:: UnlockRange](#unlockrange), 確保位元組範圍與先前鎖定的區域完全對應。 `LockRange`不會合並相鄰區域;如果兩個鎖定的區域是連續的, 您必須分別解除鎖定。

##  <a name="operator_handle"></a>CAtlTemporaryFile:: operator 控制碼

傳回暫存檔案的控制碼。

```
operator HANDLE() throw();
```

##  <a name="read"></a>CAtlTemporaryFile:: Read

呼叫這個方法, 從檔案指標所指示的位置開始, 讀取暫存檔中的資料。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
緩衝區的指標, 將會接收從檔案讀取的資料。

*nBufSize*<br/>
緩衝區大小，以位元組為單位。

*nBytesRead*<br/>
讀取的位元組數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: Read](../../atl/reference/catlfile-class.md#read)。 若要變更檔案指標的位置, 請呼叫[CAtlTemporaryFile:: Seek](#seek)。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="seek"></a>CAtlTemporaryFile:: Seek

呼叫這個方法來移動暫存檔案的檔案指標。

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>參數

*nOffset*<br/>
DwFrom 所指定之起始點的位移 (以位元組為單位) *。*

*dwFrom*<br/>
起始點 (FILE_BEGIN、FILE_CURRENT 或 FILE_END)。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: Seek](../../atl/reference/catlfile-class.md#seek)。 若要取得目前的檔案指標位置, 請呼叫[CAtlTemporaryFile:: GetPosition](#getposition)。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

##  <a name="setsize"></a>CAtlTemporaryFile:: SetSize

呼叫這個方法來設定暫存檔案的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>參數

*nNewLen*<br/>
檔案的新長度 (以位元組為單位)。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: SetSize](../../atl/reference/catlfile-class.md#setsize)。 在傳回時, 檔案指標會放在檔案結尾。

##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

呼叫這個方法, 以傳回暫存檔案的名稱。

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>傳回值

傳回指向檔案名的 LPCTSTR。

### <a name="remarks"></a>備註

在[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)中, 使用[GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 函式的呼叫來產生檔案名。 暫存檔案的副檔名一律會是 "TFR"。

##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

呼叫這個方法來解除鎖定暫存檔案的區域。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
檔案中應開始解除鎖定的位置。

*nCount*<br/>
要解除鎖定的位元組範圍長度。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)。

##  <a name="write"></a>CAtlTemporaryFile:: Write

呼叫這個方法, 從檔案指標所指示的位置開始, 將資料寫入至暫存檔。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
包含要寫入檔案之資料的緩衝區。

*nBufSize*<br/>
要從緩衝區傳送的位元組數目。

*pnBytesWritten*<br/>
寫入的位元組數目。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: Write](../../atl/reference/catlfile-class.md#write)。

### <a name="example"></a>範例

請參閱[CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile)的範例。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[CAtlFile 類別](../../atl/reference/catlfile-class.md)
