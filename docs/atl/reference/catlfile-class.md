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
ms.openlocfilehash: 784086b1c2edef5eb0de3bba4a97d1e3cc6272e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497824"
---
# <a name="catlfile-class"></a>CAtlFile 類別

這個類別會提供 Windows 檔案處理 API 的精簡型包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlFile : public CHandle
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlFile::Create](#create)|呼叫這個方法來建立或開啟檔案。|
|[CAtlFile::Flush](#flush)|呼叫這個方法來清除檔案的緩衝區, 並造成所有緩衝資料都寫入檔案中。|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|呼叫這個方法, 以取得檔案上重迭作業的結果。|
|[CAtlFile::GetPosition](#getposition)|呼叫這個方法, 從檔案中取得目前的檔案指標位置。|
|[CAtlFile::GetSize](#getsize)|呼叫此方法以取得檔案的大小 (以位元組為單位)。|
|[CAtlFile::LockRange](#lockrange)|呼叫這個方法來鎖定檔案中的區域, 以防止其他處理常式存取它。|
|[CAtlFile::Read](#read)|呼叫這個方法, 從檔案指標所指示的位置開始, 讀取檔案中的資料。|
|[CAtlFile::Seek](#seek)|呼叫這個方法來移動檔案的檔案指標。|
|[CAtlFile::SetSize](#setsize)|呼叫這個方法來設定檔案的大小。|
|[CAtlFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定檔案的區域。|
|[CAtlFile::Write](#write)|呼叫這個方法, 從檔案指標所指示的位置開始, 將資料寫入檔案。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|物件的`CAtlTransactionManager`指標|

## <a name="remarks"></a>備註

當檔案處理需求相當簡單, 但需要比 Windows API 提供的更多抽象概念時, 請使用這個類別, 而不需包含 MFC 相依性。

## <a name="inheritance-hierarchy"></a>繼承階層

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>需求

**標頭:** atlfile。h

##  <a name="catlfile"></a>CAtlFile::CAtlFile

建構函式。

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>參數

*file*<br/>
File 物件。

*hFile*<br/>
檔案控制代碼。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

複製的函式會將檔案控制代碼的擁有權`CAtlFile`從原始物件轉移至新建立的物件。

##  <a name="create"></a>CAtlFile:: Create

呼叫這個方法來建立或開啟檔案。

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

*dwDesiredAccess*<br/>
所需的存取權。 請參閱 Windows SDK 中[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)的*dwDesiredAccess* 。

*dwShareMode*<br/>
共用模式。 請參閱中`CreateFile`的 dwShareMode。

*dwCreationDisposition*<br/>
建立配置。 請參閱中`CreateFile`的 dwCreationDisposition。

*dwFlagsAndAttributes*<br/>
旗標和屬性。 請參閱中`CreateFile`的 dwFlagsAndAttributes。

*lpsa*<br/>
安全性屬性。 請參閱中`CreateFile`的 lpSecurityAttributes。

*hTemplateFile*<br/>
範本檔案。 請參閱中`CreateFile`的 hTemplateFile。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)以建立或開啟檔案。

##  <a name="flush"></a>CAtlFile:: Flush

呼叫這個方法來清除檔案的緩衝區, 並造成所有緩衝資料都寫入檔案中。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers)以將緩衝的資料排清到檔案。

##  <a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

呼叫這個方法, 以取得檔案上重迭作業的結果。

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>參數

*pOverlapped*<br/>
重迭的結構。 請參閱 Windows SDK 中[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)的*lpOverlapped* 。

*dwBytesTransferred*<br/>
傳輸的位元組數。 請參閱中`GetOverlappedResult`的 lpNumberOfBytesTransferred。

*bWait*<br/>
Wait 選項。 請參閱中`GetOverlappedResult`的 bWait。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)以取得檔案上重迭作業的結果。

##  <a name="getposition"></a>CAtlFile::GetPosition

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

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)以取得目前的檔案指標位置。

##  <a name="getsize"></a>CAtlFile:: GetSize

呼叫此方法以取得檔案的大小 (以位元組為單位)。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>參數

*nLen*<br/>
檔案中的位元組數目。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize)來取得檔案的大小 (以位元組為單位)。

##  <a name="lockrange"></a>CAtlFile::LockRange

呼叫這個方法來鎖定檔案中的區域, 以防止其他處理常式存取它。

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

呼叫[LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile)以鎖定檔案中的區域。 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定一個以上的檔案區域, 但不允許重迭的區域。 當您使用[CAtlFile:: UnlockRange](#unlockrange)解除鎖定區域時, 位元組範圍必須完全對應到先前鎖定的區域。 `LockRange`不會合並相鄰區域;如果兩個鎖定的區域是連續的, 您必須分別解除鎖定。

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="read"></a>CAtlFile:: Read

呼叫這個方法, 從檔案指標所指示的位置開始, 讀取檔案中的資料。

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
緩衝區的指標, 將會接收從檔案讀取的資料。

*nBufSize*<br/>
緩衝區大小，以位元組為單位。

*nBytesRead*<br/>
讀取的位元組數。

*pOverlapped*<br/>
重迭的結構。 請參閱 Windows SDK 中[ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)的*lpOverlapped* 。

*pfnCompletionRoutine*<br/>
完成常式。 請參閱 Windows SDK 中[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)的*lpCompletionRoutine* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單會呼叫[ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile), 最後一個[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)從檔案讀取資料。 使用[CAtlFile:: Seek](#seek)來移動檔案指標。

##  <a name="seek"></a>CAtlFile:: Seek

呼叫這個方法來移動檔案的檔案指標。

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>參數

*nOffset*<br/>
*DwFrom*所指定之起點的位移。

*dwFrom*<br/>
起始點 (FILE_BEGIN、FILE_CURRENT 或 FILE_END)。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)以移動檔案指標。

##  <a name="setsize"></a>CAtlFile:: SetSize

呼叫這個方法來設定檔案的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>參數

*nNewLen*<br/>
檔案的新長度 (以位元組為單位)。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)和[SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile)來設定檔案的大小。 在傳回時, 檔案指標會放在檔案結尾。

##  <a name="unlockrange"></a>CAtlFile::UnlockRange

呼叫這個方法來解除鎖定檔案的區域。

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

呼叫[UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile)來解除鎖定檔案的區域。

##  <a name="write"></a>CAtlFile:: Write

呼叫這個方法, 從檔案指標所指示的位置開始, 將資料寫入檔案。

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
包含要寫入檔案之資料的緩衝區。

*nBufSize*<br/>
要從緩衝區傳送的位元組數目。

*pOverlapped*<br/>
重迭的結構。 請參閱 Windows SDK 中[WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)的*lpOverlapped* 。

*pfnCompletionRoutine*<br/>
完成常式。 請參閱 Windows SDK 中[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)的*lpCompletionRoutine* 。

*pnBytesWritten*<br/>
寫入的位元組。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單呼叫[WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), 最後一次呼叫[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)將資料寫入檔案。 使用[CAtlFile:: Seek](#seek)來移動檔案指標。

## <a name="see-also"></a>另請參閱

[天棚範例](../../overview/visual-cpp-samples.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[CHandle 類別](../../atl/reference/chandle-class.md)
