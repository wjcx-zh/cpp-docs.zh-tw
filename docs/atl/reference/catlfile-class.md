---
title: CAtlFile 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318969"
---
# <a name="catlfile-class"></a>CAtlFile 類別

此類在 Windows 檔處理 API 周圍提供一個精簡包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlFile : public CHandle
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlFile:CAtlFile](#catlfile)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlFile:建立](#create)|呼叫此方法以建立或打開檔。|
|[CAtlFile:沖洗](#flush)|呼叫此方法以清除檔的緩衝區,並導致將所有緩衝資料寫入該檔。|
|[CAtlFile:取得重疊結果](#getoverlappedresult)|調用此方法以獲取檔上重疊操作的結果。|
|[CAtlFile:抓取位置](#getposition)|呼叫此方法從檔案中獲取當前檔指標位置。|
|[CAtlFile:取得 Size](#getsize)|呼叫此方法以獲取檔的大小(以位元組為單位)。|
|[CAtlFile:鎖定範圍](#lockrange)|調用此方法以鎖定檔中的區域,以防止其他進程訪問它。|
|[CAtlFile:閱讀](#read)|調用此方法從檔讀取數據,從檔指標指示的位置開始。|
|[CAtlFile:尋找](#seek)|呼叫此方法以移動檔的檔指標。|
|[CAtlFile:設定大小](#setsize)|呼叫此方法以設定檔的大小。|
|[CAtlFile:解鎖範圍](#unlockrange)|呼叫此方法以解鎖檔的區域。|
|[CAtlFile:寫入](#write)|調用此方法將數據寫入檔,從檔指標指示的位置開始。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlFile:m_pTM](#m_ptm)|指向`CAtlTransactionManager`物件的指標|

## <a name="remarks"></a>備註

當文件處理需求相對簡單,但需要比 Windows API 提供的更多的抽象,但不包括 MFC 依賴項時,請使用此類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[手柄](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>需求

**標題:** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile:CAtlFile

建構函式。

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>參數

*檔案*<br/>
檔物件。

*hFile*<br/>
檔句柄。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

複製建構函數將檔句柄的擁有權從`CAtlFile`原始 物件轉移到新構造的物件。

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile:建立

呼叫此方法以建立或打開檔。

```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>參數

*szFilename*<br/>
檔案名稱。

*dwddAccess*<br/>
所需的訪問。 請參閱 Windows SDK 中的[「創建檔案](/windows/win32/api/fileapi/nf-fileapi-createfilew)」中的*dwdDAccess。*

*dwShareMode*<br/>
共用模式。 請參閱`CreateFile`中的*dwShareMode。*

*德沃創意*<br/>
創建處置。 請參閱`CreateFile`中的*dw 創造處理。*

*dwflags 與屬性*<br/>
標誌和屬性。 請參考中的`CreateFile` *dwFlags 與屬性*。

*lpsa*<br/>
安全屬性。 請參考中的`CreateFile` *lpSecurity 屬性*。

*h範本檔案*<br/>
範本檔。 請參閱`CreateFile`中的*hTemplateFile。*

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)建立或開啟檔案。

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile:沖洗

呼叫此方法以清除檔的緩衝區,並導致將所有緩衝資料寫入該檔。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[FlushFileBuffer 以](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers)刷新緩衝的資料到檔。

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile:取得重疊結果

調用此方法以獲取檔上重疊操作的結果。

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>參數

*p 重疊*<br/>
重疊的結構。 在 Windows SDK 中查看 *「重疊*[結果](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)」。。

*dwBytes 傳輸*<br/>
傳輸的位元組數。 請參考 在中`GetOverlappedResult`*傳輸的 lp 編號數*。

*b 等待*<br/>
等待選項。 請參閱*b*`GetOverlappedResult`等待。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

調用[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)獲取檔上重疊操作的結果。

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile:抓取位置

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

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)取得目前的檔案指標位置。

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile:取得 Size

呼叫此方法以獲取檔的大小(以位元組為單位)。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>參數

*nLen*<br/>
檔中的位元組數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize)以取得檔案的大小(以位元組為單位)。

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile:鎖定範圍

調用此方法以鎖定檔中的區域,以防止其他進程訪問它。

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

呼叫[鎖定檔案](/windows/win32/api/fileapi/nf-fileapi-lockfile)中的區域。 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 可以鎖定檔的多個區域,但不允許重疊區域。 當您解鎖區域時,使用[CAtlFile::unlockRange,](#unlockrange)位元組範圍必須與以前鎖定的區域完全對應。 `LockRange`不合併相鄰區域;不合併相鄰區域。如果兩個鎖定區域相鄰,則必須單獨解鎖每個區域。

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile:m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

## <a name="catlfileread"></a><a name="read"></a>CAtlFile:閱讀

調用此方法從檔讀取數據,從檔指標指示的位置開始。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
指向將接收從檔讀取的數據的緩衝區的指標。

*nBufSize*<br/>
緩衝區大小，以位元組為單位。

*n 位元組讀取*<br/>
讀取的位元組數。

*p 重疊*<br/>
重疊的結構。 在 Windows SDK 中的[「讀取檔案](/windows/win32/api/fileapi/nf-fileapi-readfile)」 中檢視*lp 重疊*。

*pfn 完成常式*<br/>
完成例程。 請參考 Windows SDK 中的[「閱讀檔更新](/windows/win32/api/fileapi/nf-fileapi-readfileex)」 的*lp 完成例程式*。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單調用[ReadFile,](/windows/win32/api/fileapi/nf-fileapi-readfile)這是最後一個從檔讀取資料的[ReadFileEx。](/windows/win32/api/fileapi/nf-fileapi-readfileex) 使用[CAtlFile::尋求](#seek)移動檔指標。

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile:尋找

呼叫此方法以移動檔的檔指標。

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>參數

*n位移*<br/>
dwFrom 給出的起始點的偏*dwFrom*移 量。

*dwfrom*<br/>
起點(FILE_BEGIN、FILE_CURRENT或FILE_END)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)以移動檔指標。

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile:設定大小

呼叫此方法以設定檔的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>參數

*n 紐倫*<br/>
檔的新長度(以位元組為單位)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)和[SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile)來設定檔的大小。 返回時,檔指標位於檔的末尾。

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile:解鎖範圍

呼叫此方法以解鎖檔的區域。

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

呼叫[解鎖檔](/windows/win32/api/fileapi/nf-fileapi-unlockfile)以解鎖檔的區域。

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile:寫入

調用此方法將數據寫入檔,從檔指標指示的位置開始。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>參數

*pBuffer*<br/>
包含要寫入文件的數據的緩衝區。

*nBufSize*<br/>
要從緩衝區傳輸的位元組數。

*p 重疊*<br/>
重疊的結構。 在 Windows SDK 的[寫入檔案](/windows/win32/api/fileapi/nf-fileapi-writefile)中檢視*lp 重疊*。

*pfn 完成常式*<br/>
完成例程。 請參考 Windows SDK 中[寫入檔案Ex](/windows/win32/api/fileapi/nf-fileapi-writefileex)中的*lp 完成例程式*。

*pn位元組寫入*<br/>
寫入的位元組。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單調用[WriteFile,](/windows/win32/api/fileapi/nf-fileapi-writefile)最後呼叫[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)將資料寫入檔。 使用[CAtlFile::尋求](#seek)移動檔指標。

## <a name="see-also"></a>另請參閱

[選取方塊範例](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CHandle 類別](../../atl/reference/chandle-class.md)
