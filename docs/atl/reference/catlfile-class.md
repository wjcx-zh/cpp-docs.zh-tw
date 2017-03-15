---
title: "CAtlFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFile
- ATL::CAtlFile
- ATL.CAtlFile
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5ba8aa0bc5544d8d541fecb87e2eb0108c2c5ebd
ms.lasthandoff: 02/24/2017

---
# <a name="catlfile-class"></a>CAtlFile 類別
這個類別會提供 Windows 的精簡型包裝函式的檔案處理 API。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlFile : public CHandle
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](#catlfile)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFile::Create](#create)|呼叫這個方法來建立或開啟檔案。|  
|[CAtlFile::Flush](#flush)|呼叫此方法來清除檔案緩衝區，並造成所有緩衝的資料寫入檔案。|  
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|呼叫這個方法來取得重疊在檔案上作業的結果。|  
|[CAtlFile::GetPosition](#getposition)|呼叫此方法以從檔案取得目前的檔案位置指標。|  
|[CAtlFile::GetSize](#getsize)|呼叫這個方法，以取得以位元組為單位的檔案大小。|  
|[CAtlFile::LockRange](#lockrange)|呼叫此方法以鎖定可防止其他處理序存取該檔案中的區域。|  
|[CAtlFile::Read](#read)|呼叫這個方法來讀取資料檔案，檔案指標所指示的位置開始。|  
|[CAtlFile::Seek](#seek)|呼叫這個方法來移動檔案的檔案的指標。|  
|[CAtlFile::SetSize](#setsize)|呼叫這個方法，設定檔的大小。|  
|[CAtlFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定檔案的區域。|  
|[CAtlFile::Write](#write)|呼叫這個方法將資料寫入檔案的檔案指標所指示的位置開始。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件|  
  
## <a name="remarks"></a>備註  
 當檔案處理需求相當簡單，但比 Windows API 提供更多的抽象概念是必要的但不包括 MFC 相依性時，請使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlfile.h  
  
##  <a name="a-namecatlfilea--catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile  
 建構函式。  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>參數  
 `file`  
 「 檔案 」 物件。  
  
 `hFile`  
 檔案控制代碼。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 複製建構函式的檔案控制代碼擁有權轉移原始`CAtlFile`新建構的物件的物件。  
  
##  <a name="a-namecreatea--catlfilecreate"></a><a name="create"></a>CAtlFile::Create  
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
 *szFilename*  
 檔案名稱。  
  
 `dwDesiredAccess`  
 所需的存取。 請參閱`dwDesiredAccess`中[CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwShareMode`  
 共用模式。 請參閱`dwShareMode`中**CreateFile**。  
  
 `dwCreationDisposition`  
 建立配置。 請參閱`dwCreationDisposition`中**CreateFile**。  
  
 `dwFlagsAndAttributes`  
 旗標與屬性。 請參閱`dwFlagsAndAttributes`中**CreateFile**。  
  
 `lpsa`  
 安全性屬性。 請參閱*lpSecurityAttributes*中**CreateFile**。  
  
 `hTemplateFile`  
 範本檔案。 請參閱`hTemplateFile`中**CreateFile**。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858)來建立或開啟檔案。  
  
##  <a name="a-nameflusha--catlfileflush"></a><a name="flush"></a>CAtlFile::Flush  
 呼叫此方法來清除檔案緩衝區，並造成所有緩衝的資料寫入檔案。  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[FlushFileBuffers](http://msdn.microsoft.com/library/windows/desktop/aa364439)排清緩衝處理的資料檔案。  
  
##  <a name="a-namegetoverlappedresulta--catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult  
 呼叫這個方法來取得重疊在檔案上作業的結果。  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>參數  
 `pOverlapped`  
 重疊的結構。 請參閱`lpOverlapped`中[GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *dwBytesTransferred*  
 傳輸的位元組。 請參閱*lpNumberOfBytesTransferred*中`GetOverlappedResult`。  
  
 `bWait`  
 [等候] 選項。 See `bWait` in `GetOverlappedResult`.  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209)取得重疊在檔案上作業的結果。  
  
##  <a name="a-namegetpositiona--catlfilegetposition"></a><a name="getposition"></a>CAtlFile::GetPosition  
 呼叫這個方法，取得目前的檔案位置指標。  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 以位元組為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541)取得目前的檔案位置指標。  
  
##  <a name="a-namegetsizea--catlfilegetsize"></a><a name="getsize"></a>CAtlFile::GetSize  
 呼叫這個方法，以取得以位元組為單位的檔案大小。  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nLen`  
 在檔案中的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955)以取得以位元組為單位的檔案大小。  
  
##  <a name="a-namelockrangea--catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange  
 呼叫此方法以鎖定可防止其他處理序存取該檔案中的區域。  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 應該鎖定檔案中的位置。  
  
 `nCount`  
 要鎖定的位元組範圍的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[鎖定](http://msdn.microsoft.com/library/windows/desktop/aa365202)鎖定檔案中的區域。 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案中，多個區域，但允許沒有重疊的區域。 當您解除鎖定的區域時，使用[CAtlFile::UnlockRange](#unlockrange)，位元組範圍必須確實對應到先前鎖定的區域。 `LockRange`不會合併相鄰地區。如果兩個鎖定的區域是相鄰的您必須個別解除每個鎖定。  
  
##  <a name="a-namemptma--catlfilemptm"></a><a name="m_ptm"></a>CAtlFile::m_pTM  
 指向 `CAtlTransactionManager` 物件的指標。  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namereada--catlfileread"></a><a name="read"></a>CAtlFile::Read  
 呼叫這個方法來讀取資料檔案，檔案指標所指示的位置開始。  
  
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
 `pBuffer`  
 接收從檔案讀取資料的緩衝區指標。  
  
 `nBufSize`  
 緩衝區大小，以位元組為單位。  
  
 `nBytesRead`  
 讀取的位元組數。  
  
 `pOverlapped`  
 重疊的結構。 請參閱`lpOverlapped`中[ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pfnCompletionRoutine`  
 完成常式中。 請參閱*lpCompletionRoutine*中[ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 前三個表單呼叫[ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467)，最後一個[ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468)從檔案讀取資料。 使用[CAtlFile::Seek](#seek)移動檔案指標。  
  
##  <a name="a-nameseeka--catlfileseek"></a><a name="seek"></a>CAtlFile::Seek  
 呼叫這個方法來移動檔案的檔案的指標。  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>參數  
 `nOffset`  
 從所指定的起始位置的位移`dwFrom`。  
  
 `dwFrom`  
 起始點 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541)移動檔案指標。  
  
##  <a name="a-namesetsizea--catlfilesetsize"></a><a name="setsize"></a>CAtlFile::SetSize  
 呼叫這個方法，設定檔的大小。  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>參數  
 `nNewLen`  
 新的檔案，以位元組為單位的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541)和[SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531)設定檔的大小。 在傳回時，檔案指標位於檔案結尾。  
  
##  <a name="a-nameunlockrangea--catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange  
 呼叫這個方法來解除鎖定檔案的區域。  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 應該解除鎖定的檔案中的位置。  
  
 `nCount`  
 要解除鎖定的位元組範圍的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715)來解除鎖定檔案的區域。  
  
##  <a name="a-namewritea--catlfilewrite"></a><a name="write"></a>CAtlFile::Write  
 呼叫這個方法將資料寫入檔案的檔案指標所指示的位置開始。  
  
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
 `pBuffer`  
 包含要寫入檔案的資料緩衝區。  
  
 `nBufSize`  
 從緩衝區中要傳輸的位元組數目。  
  
 `pOverlapped`  
 重疊的結構。 請參閱`lpOverlapped`中[WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pfnCompletionRoutine`  
 完成常式中。 請參閱*lpCompletionRoutine*中[WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pnBytesWritten`  
 寫入的位元組數。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 前三個表單呼叫[WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747)，最後一個呼叫[WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748)將資料寫入至檔案。 使用[CAtlFile::Seek](#seek)移動檔案指標。  
  
## <a name="see-also"></a>另請參閱  
 [跑馬燈範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CHandle 類別](../../atl/reference/chandle-class.md)

