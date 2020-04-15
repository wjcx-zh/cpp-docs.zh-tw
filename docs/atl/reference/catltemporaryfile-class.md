---
title: CAtl 暫存檔類別
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
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321314"
---
# <a name="catltemporaryfile-class"></a>CAtl 暫存檔類別

此類提供創建和使用臨時檔的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlTemporaryFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtl 暫存檔:CAtl暫存檔](#catltemporaryfile)|建構函式。|
|[CAtl 暫存檔:*CAtl暫存檔](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtl 暫存檔:關閉](#close)|呼叫此方法以關閉暫存檔並刪除其內容或將其儲存在指定的檔名下。|
|[CAtl 暫存檔:建立](#create)|呼叫此方法以建立暫存檔。|
|[CAtl 暫存檔::Flush](#flush)|呼叫此方法以強制將檔案緩衝區中剩餘的任何資料寫入暫存檔。|
|[CAtl 暫存檔:抓取位置](#getposition)|呼叫此方法獲取當前檔指標位置。|
|[CAtl 暫存檔:取得Size](#getsize)|呼叫此方法以取得暫存檔的大小(以位元組為單位)。|
|[CAtl 暫存檔:手關閉](#handsoff)|呼叫此方法以取消檔與物件關聯的`CAtlTemporaryFile`檔。|
|[CAtl暫存檔::手](#handson)|呼叫此方法以打開現有暫存檔並將指標放置在檔的末尾。|
|[CAtl 暫存檔:鎖定範圍](#lockrange)|調用此方法以鎖定檔中的區域,以防止其他進程訪問它。|
|[CAtl 暫存檔:閱讀](#read)|呼叫此方法從暫存檔讀取從檔指標指示的位置開始的資料。|
|[CAtl 暫存檔:尋找](#seek)|呼叫此方法以移動暫存檔的檔指標。|
|[CAtl 暫存檔::設定大小](#setsize)|呼叫此方法以設定暫存檔的大小。|
|[CAtl暫存檔::聖殿檔名稱](#tempfilename)|呼叫此方法以返回暫存檔的名稱。|
|[CAtl 暫存檔::解鎖範圍](#unlockrange)|呼叫此方法以解鎖暫存檔的區域。|
|[CAtl 暫存檔:寫入](#write)|呼叫此方法將資料寫入從檔指標指示的位置開始的暫存檔。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtl暫存檔::管理員HANDLE](#operator_handle)|返回臨時檔的句柄。|

## <a name="remarks"></a>備註

`CAtlTemporaryFile`便於創建和使用臨時檔。 該檔將自動命名、打開、關閉和刪除。 如果在檔案關閉後需要檔內容,則可以將文件內容保存到具有指定名稱的新檔中。

## <a name="requirements"></a>需求

**標題:** atlfile.h

## <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtl 暫存檔:CAtl暫存檔

建構函式。

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>備註

在調用[CAtlTemporaryFile:::創建](#create)之前,文件實際上不會打開。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtl 暫存檔:*CAtl暫存檔

解構函式。

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>備註

解構函數呼叫[CAtl 暫存檔:關閉](#close)。

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtl 暫存檔:關閉

呼叫此方法以關閉暫存檔並刪除其內容或將其儲存在指定的檔名下。

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>參數

*szNewName*<br/>
用於將暫存檔的內容儲存在其中的新文件的名稱。 如果此參數為 NULL,則刪除暫存檔的內容。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtl 暫存檔:建立

呼叫此方法以建立暫存檔。

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>參數

*皮茲迪爾*<br/>
臨時文件的路徑。 如果這是 NULL,則將調用[GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)來分配路徑。

*dwddAccess*<br/>
所需的訪問。 請參閱 Windows SDK 中的[「創建檔案](/windows/win32/api/fileapi/nf-fileapi-createfilew)」中的*dwdDAccess。*

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtl 暫存檔::Flush

呼叫此方法以強制將檔案緩衝區中剩餘的任何資料寫入暫存檔。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

類似於[CAtl 臨時檔::Handsoff,](#handsoff)只是檔未關閉。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtl 暫存檔:抓取位置

呼叫此方法獲取當前檔指標位置。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
位元組中的位置。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

要變更檔案指標位置,請使用[CAtl 暫存檔::尋找](#seek)。

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtl 暫存檔:取得Size

呼叫此方法以取得暫存檔的大小(以位元組為單位)。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>參數

*nLen*<br/>
檔中的位元組數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtl 暫存檔:手關閉

呼叫此方法以取消檔與物件關聯的`CAtlTemporaryFile`檔。

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

`HandsOff`和[CAtl 暫存檔:HandsOn](#handson)用於取消檔與物件關聯的關聯,並在需要時重新附加該檔。 `HandsOff`將強制將檔緩衝區中剩餘的任何數據寫入暫存檔,然後關閉該檔。 如果要永久關閉與刪除此檔案,或是要關閉與保留有指定名稱的檔案的內容,請使用[CAtlTemporaryFile:關閉](#close)。

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtl暫存檔::手

呼叫此方法以打開現有暫存檔並將指標放置在檔的末尾。

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CAtl暫存檔::HandsOff,](#handsoff)`HandsOn`用於取消檔與物件的關聯,並在需要時重新附加它。

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtl 暫存檔:鎖定範圍

調用此方法以鎖定臨時檔中的區域,以防止其他進程訪問它。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
鎖應開始的檔中的位置。

*n( N) Count*<br/>
要鎖定的位元組範圍的長度。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

鎖定檔案中的位元組可防止其他處理序存取這些位元組。 可以鎖定檔的多個區域,但不允許重疊區域。 要成功解鎖區域,請使用[CAtlTemporaryFile::unlockRange,](#unlockrange)確保位元組範圍與以前鎖定的區域完全對應。 `LockRange`不合併相鄰區域;不合併相鄰區域。如果兩個鎖定區域相鄰,則必須單獨解鎖每個區域。

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtl暫存檔::管理員HANDLE

返回臨時檔的句柄。

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtl 暫存檔:閱讀

呼叫此方法從暫存檔讀取從檔指標指示的位置開始的資料。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
指向將接收從檔讀取的數據的緩衝區的指標。

*nBufSize*<br/>
緩衝區大小，以位元組為單位。

*n 位元組讀取*<br/>
讀取的位元組數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼[叫 CAtlFile:讀取](../../atl/reference/catlfile-class.md#read)。 要變更檔案指標的位置,請致電[CAtlTemporaryFile::seek](#seek)。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtl 暫存檔:尋找

呼叫此方法以移動暫存檔的檔指標。

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>參數

*n位移*<br/>
從*dwFrom*給出的起始點偏移(以位元組為單位)。

*dwfrom*<br/>
起點(FILE_BEGIN、FILE_CURRENT或FILE_END)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:: 尋找](../../atl/reference/catlfile-class.md#seek)。 要取得目前的檔案指標位置,請致電[CAtl 暫存檔::get定位](#getposition)。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtl 暫存檔::設定大小

呼叫此方法以設定暫存檔的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>參數

*n 紐倫*<br/>
檔的新長度(以位元組為單位)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile::設定大小](../../atl/reference/catlfile-class.md#setsize)。 返回時,檔指標位於檔的末尾。

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtl暫存檔::聖殿檔名稱

呼叫此方法以返回暫存檔的名稱。

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>傳回值

返回指向檔名的 LPCTSTR。

### <a name="remarks"></a>備註

檔名在[CAtl 暫存檔::CAtl 暫存檔](#catltemporaryfile)與存[取 GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 功能時生成。 臨時檔的檔擴展名將始終為"TFR"。

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtl 暫存檔::解鎖範圍

呼叫此方法以解鎖暫存檔的區域。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
應開始解鎖的檔中的位置。

*n( N) Count*<br/>
要解鎖的位元組範圍的長度。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼[叫 CAtlFile:解鎖範圍](../../atl/reference/catlfile-class.md#unlockrange)。

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtl 暫存檔:寫入

呼叫此方法將資料寫入從檔指標指示的位置開始的暫存檔。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
包含要寫入文件的數據的緩衝區。

*nBufSize*<br/>
要從緩衝區傳輸的位元組數。

*pn位元組寫入*<br/>
已寫入的位元組數目。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CAtlFile:寫入](../../atl/reference/catlfile-class.md#write)。

### <a name="example"></a>範例

請參考[CAtl 暫存檔的範例:CAtl 暫存檔](#catltemporaryfile)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[CAtlFile 類別](../../atl/reference/catlfile-class.md)
