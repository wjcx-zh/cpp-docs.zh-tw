---
title: CAtlFile 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ec124d1010a5870d47b9f1504655a7822505fe6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040488"
---
# <a name="catlfile-class"></a>CAtlFile 類別

這個類別會提供 Windows 精簡型包裝函式的檔案處理 API。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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
|[CAtlFile::Flush](#flush)|呼叫這個方法來清除檔案緩衝區，並造成所有緩衝的資料寫入檔案。|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|呼叫這個方法來取得檔案的重疊作業的結果。|
|[CAtlFile::GetPosition](#getposition)|呼叫這個方法，以從檔案取得目前的檔案指標位置。|
|[CAtlFile::GetSize](#getsize)|呼叫這個方法來取得以位元組為單位之檔案的大小。|
|[CAtlFile::LockRange](#lockrange)|呼叫這個方法，以鎖定可防止其他處理序存取該檔案中的區域。|
|[CAtlFile::Read](#read)|呼叫這個方法來讀取檔案，檔案指標所指示的位置開始的資料。|
|[CAtlFile::Seek](#seek)|呼叫這個方法來移動檔案指標的檔案。|
|[CAtlFile::SetSize](#setsize)|呼叫此方法以設定檔的大小。|
|[CAtlFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定檔案的區域。|
|[CAtlFile::Write](#write)|呼叫這個方法，以將資料寫入至檔案指標所指示的位置開始的檔案。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件|

## <a name="remarks"></a>備註

當檔案處理需求相當簡單，但比 Windows API 所提供的更多抽象概念是必要的但不包含 MFC 的相依性時，請使用這個類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>需求

**標頭：** atlfile.h

##  <a name="catlfile"></a>  CAtlFile::CAtlFile

建構函式。

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>參數

*file*<br/>
「 檔案 」 物件。

*hFile*<br/>
檔案控制代碼。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

複製建構函式傳輸的檔案控制代碼的擁有權從原始`CAtlFile`物件與新建構的物件。

##  <a name="create"></a>  CAtlFile::Create

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
所需的存取。 請參閱*dwDesiredAccess*中[CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) Windows SDK 中。

*dwShareMode*<br/>
共用模式中。 請參閱*dwShareMode*在`CreateFile`。

*dwCreationDisposition*<br/>
建立配置中。 請參閱*dwCreationDisposition*在`CreateFile`。

*dwFlagsAndAttributes*<br/>
旗標與屬性。 請參閱*dwFlagsAndAttributes*在`CreateFile`。

*lpsa*<br/>
安全性屬性。 請參閱*lpSecurityAttributes*在`CreateFile`。

*hTemplateFile*<br/>
範本檔案。 請參閱*hTemplateFile*在`CreateFile`。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea)建立或開啟檔案。

##  <a name="flush"></a>  CAtlFile::Flush

呼叫這個方法來清除檔案緩衝區，並造成所有緩衝的資料寫入檔案。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[FlushFileBuffers](/windows/desktop/api/fileapi/nf-fileapi-flushfilebuffers)排清緩衝處理的資料到檔案。

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

呼叫這個方法來取得檔案的重疊作業的結果。

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>參數

*pOverlapped*<br/>
重疊的結構。 請參閱*lpOverlapped*中[GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) Windows SDK 中。

*dwBytesTransferred*<br/>
傳輸的位元組。 請參閱*lpNumberOfBytesTransferred*在`GetOverlappedResult`。

*bWait*<br/>
[等候] 選項。 請參閱*bWait*在`GetOverlappedResult`。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult)來取得檔案的重疊作業結果。

##  <a name="getposition"></a>  CAtlFile::GetPosition

呼叫這個方法來取得目前的檔案指標位置。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
以位元組為單位的位置。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)來取得目前的檔案指標位置。

##  <a name="getsize"></a>  CAtlFile::GetSize

呼叫這個方法來取得以位元組為單位之檔案的大小。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>參數

*nLen*<br/>
在檔案中的位元組數目。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[GetFileSize](/windows/desktop/api/fileapi/nf-fileapi-getfilesize)來取得以位元組為單位之檔案的大小。

##  <a name="lockrange"></a>  CAtlFile::LockRange

呼叫這個方法，以鎖定可防止其他處理序存取該檔案中的區域。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
鎖定應該開始的位置的檔案中的位置。

*nCount*<br/>
位元組範圍鎖定的長度。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[鎖定](/windows/desktop/api/fileapi/nf-fileapi-lockfile)鎖定檔案中的區域。 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案的多個區域，但允許任何重疊的區域。 當您解除鎖定的區域時，使用[CAtlFile::UnlockRange](#unlockrange)，位元組範圍必須確實對應到先前鎖定的區域。 `LockRange` 不會合併相鄰區域;如果兩個鎖定的區域相鄰，您必須個別取消每個鎖定。

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="read"></a>  CAtlFile::Read

呼叫這個方法來讀取檔案，檔案指標所指示的位置開始的資料。

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
從檔案讀取至接收資料的緩衝區的指標。

*nBufSize*<br/>
緩衝區大小，以位元組為單位。

*nBytesRead*<br/>
讀取的位元組數。

*pOverlapped*<br/>
重疊的結構。 請參閱*lpOverlapped*中[ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile) Windows SDK 中。

*pfnCompletionRoutine*<br/>
完成常式。 請參閱*lpCompletionRoutine*中[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) Windows SDK 中。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單呼叫[ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile)，最後[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex)從檔案讀取資料。 使用[CAtlFile::Seek](#seek)移動檔案指標。

##  <a name="seek"></a>  CAtlFile::Seek

呼叫這個方法來移動檔案指標的檔案。

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>參數

*nOffset*<br/>
從所指定的起始點的位移*dwFrom*。

*dwFrom*<br/>
起始點 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)移動檔案指標。

##  <a name="setsize"></a>  CAtlFile::SetSize

呼叫此方法以設定檔的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>參數

*nNewLen*<br/>
新的長度，以位元組為單位的檔案。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer)並[SetEndOfFile](/windows/desktop/api/fileapi/nf-fileapi-setendoffile)設定檔的大小。 在傳回時，檔案指標被位於檔案結尾。

##  <a name="unlockrange"></a>  CAtlFile::UnlockRange

呼叫這個方法來解除鎖定檔案的區域。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>參數

*nPos*<br/>
解除鎖定應該開始的位置的檔案中的位置。

*nCount*<br/>
要解除鎖定的位元組範圍的長度。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

呼叫[UnlockFile](/windows/desktop/api/fileapi/nf-fileapi-unlockfile)來解除鎖定檔案的區域。

##  <a name="write"></a>  CAtlFile::Write

呼叫這個方法，以將資料寫入至檔案指標所指示的位置開始的檔案。

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
包含要寫入檔案的資料緩衝區。

*nBufSize*<br/>
若要從緩衝區傳送的位元組數目。

*pOverlapped*<br/>
重疊的結構。 請參閱*lpOverlapped*中[WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) Windows SDK 中。

*pfnCompletionRoutine*<br/>
完成常式。 請參閱*lpCompletionRoutine*中[WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex) Windows SDK 中。

*pnBytesWritten*<br/>
寫入的位元組。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

前三個表單呼叫[WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile)，最後一個呼叫[WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex)將資料寫入檔案。 使用[CAtlFile::Seek](#seek)移動檔案指標。

## <a name="see-also"></a>另請參閱

[跑馬燈範例](../../visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CHandle 類別](../../atl/reference/chandle-class.md)
