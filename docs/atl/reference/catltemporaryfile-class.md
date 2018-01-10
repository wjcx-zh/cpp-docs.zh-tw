---
title: "CAtlTemporaryFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5911de856d13d9d66e8c950d446083a36811f535
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 類別
這個類別提供建立和使用的暫存檔案的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
|[CAtlTemporaryFile::Close](#close)|呼叫這個方法來關閉暫存檔，並刪除其內容或將它們儲存在指定的檔案名稱。|  
|[CAtlTemporaryFile::Create](#create)|呼叫此方法以建立暫存檔。|  
|[CAtlTemporaryFile::Flush](#flush)|呼叫這個方法，以強制執行任何寫入暫存檔案將檔案緩衝區中剩餘的資料。|  
|[CAtlTemporaryFile::GetPosition](#getposition)|呼叫這個方法來取得目前的檔案指標位置。|  
|[CAtlTemporaryFile::GetSize](#getsize)|呼叫此方法以取得以位元組為單位的暫存檔案的大小。|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|呼叫這個方法來取消關聯的檔案從`CAtlTemporaryFile`物件。|  
|[CAtlTemporaryFile::HandsOn](#handson)|呼叫這個方法，以開啟現有的暫存檔案，並將位於檔案結尾的指標。|  
|[CAtlTemporaryFile::LockRange](#lockrange)|呼叫此方法以鎖定可防止其他處理序存取該檔案中的區域。|  
|[CAtlTemporaryFile::Read](#read)|呼叫此方法以從檔案指標所指示的位置開始，暫存檔案讀取資料。|  
|[CAtlTemporaryFile::Seek](#seek)|呼叫這個方法來移動檔案指標的暫存檔案。|  
|[CAtlTemporaryFile::SetSize](#setsize)|呼叫這個方法來設定暫存檔案的大小。|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|呼叫此方法以傳回暫存檔案的名稱。|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定的暫存檔的區域。|  
|[CAtlTemporaryFile::Write](#write)|呼叫這個方法將資料寫入暫存檔案的檔案指標所指示的位置開始。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator 控制代碼](#operator_handle)|傳回的控制代碼到暫存檔。|  
  
## <a name="remarks"></a>備註  
 `CAtlTemporaryFile`可讓您輕鬆地建立及使用暫存檔。 會自動名為、 開啟、 關閉，並刪除檔案。 如果檔案內容是必要的檔案已關閉之後，可以儲存到新的檔案具有指定名稱。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlfile.h  
  
## <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile  
 建構函式。  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>備註  
 開啟檔案時不實際進行呼叫，直到[CAtlTemporaryFile::Create](#create)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 解構函式。  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式呼叫[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="close"></a>CAtlTemporaryFile::Close  
 呼叫這個方法來關閉暫存檔，並刪除其內容或將它們儲存在指定的檔案名稱。  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 *szNewName*  
 新的檔案來儲存暫存檔案的內容名稱。 如果這個引數為 NULL，則會刪除暫存檔案的內容。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="create"></a>CAtlTemporaryFile::Create  
 呼叫此方法以建立暫存檔。  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszDir`  
 暫存檔案的路徑。 如果這是 NULL， [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992)將呼叫指派的路徑。  
  
 `dwDesiredAccess`  
 所需的存取。 請參閱`dwDesiredAccess`中[CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="flush"></a>CAtlTemporaryFile::Flush  
 呼叫這個方法，以強制執行任何寫入暫存檔案將檔案緩衝區中剩餘的資料。  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 類似於[CAtlTemporaryFile::HandsOff](#handsoff)，但不關閉檔案。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition  
 呼叫這個方法來取得目前的檔案指標位置。  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 以位元組為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 若要變更檔案指標的位置，請使用[CAtlTemporaryFile::Seek](#seek)。  
  
##  <a name="getsize"></a>CAtlTemporaryFile::GetSize  
 呼叫此方法以取得以位元組為單位的暫存檔案的大小。  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nLen`  
 在檔案中的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff  
 呼叫這個方法來取消關聯的檔案從`CAtlTemporaryFile`物件。  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 `HandsOff`和[CAtlTemporaryFile::HandsOn](#handson)可用來取消關聯的檔案從該物件，並視需要將它重新附加。 `HandsOff`會強制執行任何寫入暫存檔案中，將檔案緩衝區中剩餘的資料，然後關閉檔案。 如果您想要關閉並永久刪除檔案，或如果您想要關閉和保留的檔案具有指定名稱的內容，請使用[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="handson"></a>CAtlTemporaryFile::HandsOn  
 呼叫這個方法，以開啟現有的暫存檔案，並將位於檔案結尾的指標。  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 [CAtlTemporaryFile::HandsOff](#handsoff)和`HandsOn`可用來取消關聯的檔案從該物件，並視需要將它重新附加。  
  
##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange  
 呼叫此方法以鎖定來防止其他處理程序存取它暫存檔中的區域。  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 鎖定的開始位置的檔案中的位置。  
  
 `nCount`  
 位元組範圍鎖定的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案的多個區域，但允許沒有重疊的區域。 若要成功解除鎖定的區域，使用[CAtlTemporaryFile::UnlockRange](#unlockrange)，確保位元組範圍完全對應於先前鎖定的區域。 `LockRange`不會合併相鄰地區。如果相鄰兩個鎖定的區域，您必須個別取消每個鎖定。  
  
##  <a name="operator_handle"></a>CAtlTemporaryFile::operator 控制代碼  
 傳回的控制代碼到暫存檔。  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>CAtlTemporaryFile::Read  
 呼叫此方法以從檔案指標所指示的位置開始，暫存檔案讀取資料。  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>參數  
 `pBuffer`  
 將接收從檔案讀取資料的緩衝區指標。  
  
 `nBufSize`  
 緩衝區大小，以位元組為單位。  
  
 `nBytesRead`  
 讀取的位元組數。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Read](../../atl/reference/catlfile-class.md#read)。 若要變更檔案指標的位置，請呼叫[CAtlTemporaryFile::Seek](#seek)。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="seek"></a>CAtlTemporaryFile::Seek  
 呼叫這個方法來移動檔案指標的暫存檔案。  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>參數  
 `nOffset`  
 位移，以位元組為單位，以指定的起始點從*dwFrom。*  
  
 `dwFrom`  
 起點 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek)。 若要取得目前的檔案指標位置，請呼叫[CAtlTemporaryFile::GetPosition](#getposition)。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="setsize"></a>CAtlTemporaryFile::SetSize  
 呼叫這個方法來設定暫存檔案的大小。  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>參數  
 `nNewLen`  
 新的檔案，以位元組為單位的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize)。 在傳回時，檔案指標位於檔案結尾。  
  
##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName  
 呼叫此方法以傳回暫存檔案的名稱。  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`LPCTSTR`指向檔案名稱。  
  
### <a name="remarks"></a>備註  
 檔案名稱會以產生[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)呼叫[GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991)Windows SDK 函式。 檔案的副檔名一律為"TFR"存檔。  
  
##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange  
 呼叫這個方法來解除鎖定的暫存檔的區域。  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 解除鎖定的開始位置的檔案中的位置。  
  
 `nCount`  
 要解除鎖定的位元組範圍的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)。  
  
##  <a name="write"></a>CAtlTemporaryFile::Write  
 呼叫這個方法將資料寫入暫存檔案的檔案指標所指示的位置開始。  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `pBuffer`  
 包含要寫入檔案資料的緩衝區。  
  
 `nBufSize`  
 從緩衝區中要傳輸的位元組數目。  
  
 `pnBytesWritten`  
 寫入的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功或錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Write](../../atl/reference/catlfile-class.md#write)。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [CAtlFile 類別](../../atl/reference/catlfile-class.md)
