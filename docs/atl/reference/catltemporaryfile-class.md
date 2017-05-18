---
title: "CAtlTemporaryFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9673c5a137feddb0eb696945ec6abeb5f3cb062e
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 類別
這個類別提供建立和使用的暫存檔案的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlTemporaryFile
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|建構函式。|  
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](#close)|呼叫這個方法來關閉暫存檔，請刪除其內容或將它們儲存在指定的檔案名稱。|  
|[CAtlTemporaryFile::Create](#create)|呼叫此方法以建立暫存檔。|  
|[CAtlTemporaryFile::Flush](#flush)|呼叫這個方法，以強制寫入暫存檔案，檔案緩衝區剩餘的任何資料。|  
|[CAtlTemporaryFile::GetPosition](#getposition)|呼叫這個方法，取得目前的檔案位置指標。|  
|[CAtlTemporaryFile::GetSize](#getsize)|呼叫這個方法，以取得以位元組為單位的暫存檔案的大小。|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|呼叫這個方法來取消關聯的檔案從`CAtlTemporaryFile`物件。|  
|[CAtlTemporaryFile::HandsOn](#handson)|呼叫這個方法來開啟現有的暫存檔案並在檔案結尾指標。|  
|[CAtlTemporaryFile::LockRange](#lockrange)|呼叫此方法以鎖定可防止其他處理序存取該檔案中的區域。|  
|[CAtlTemporaryFile::Read](#read)|呼叫這個方法從檔案指標所指示的位置開始，暫存檔案讀取資料。|  
|[CAtlTemporaryFile::Seek](#seek)|呼叫這個方法來移動檔案指標的暫存檔案。|  
|[CAtlTemporaryFile::SetSize](#setsize)|呼叫這個方法來設定暫存檔案的大小。|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|呼叫這個方法傳回的暫存檔案的名稱。|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|呼叫這個方法來解除鎖定暫存檔案的區域。|  
|[CAtlTemporaryFile::Write](#write)|呼叫這個方法將資料寫入至暫存檔檔案指標所指示的位置開始。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator 控制代碼](#operator_handle)|傳回的控制代碼到暫存檔。|  
  
## <a name="remarks"></a>備註  
 `CAtlTemporaryFile`可讓您輕鬆建立及使用暫存檔。 檔案會自動是名為、 開啟、 關閉，並且刪除。 如果檔案內容需要關閉檔案後，可以儲存至具有指定名稱的新檔案。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlfile.h  
  
## <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile  
 建構函式。  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>備註  
 檔案並未實際開啟之前呼叫[CAtlTemporaryFile::Create](#create)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&73;](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 解構函式。  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式呼叫[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="close"></a>CAtlTemporaryFile::Close  
 呼叫這個方法來關閉暫存檔，請刪除其內容或將它們儲存在指定的檔案名稱。  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 *szNewName*  
 新的檔案來儲存暫存檔中的內容名稱。 如果這個引數為 NULL，則會刪除暫存檔案的內容。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="create"></a>CAtlTemporaryFile::Create  
 呼叫此方法以建立暫存檔。  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszDir`  
 暫存檔案的路徑。 如果這是 NULL， [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992)將被呼叫來指派的路徑。  
  
 `dwDesiredAccess`  
 所需的存取。 請參閱`dwDesiredAccess`中[CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="flush"></a>CAtlTemporaryFile::Flush  
 呼叫這個方法，以強制寫入暫存檔案，檔案緩衝區剩餘的任何資料。  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 類似於[CAtlTemporaryFile::HandsOff](#handsoff)，但不關閉檔案。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition  
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
 若要變更檔案指標的位置，請使用[CAtlTemporaryFile::Seek](#seek)。  
  
##  <a name="getsize"></a>CAtlTemporaryFile::GetSize  
 呼叫這個方法，以取得以位元組為單位的暫存檔案的大小。  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>參數  
 `nLen`  
 在檔案中的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff  
 呼叫這個方法來取消關聯的檔案從`CAtlTemporaryFile`物件。  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 `HandsOff`和[CAtlTemporaryFile::HandsOn](#handson)用來解除關聯物件的檔案，並視需要將它重新附加。 `HandsOff`會強制執行任何寫入暫存檔案中，將檔案緩衝區中剩餘的資料，然後關閉檔案。 如果您想要關閉，並永久刪除檔案，或如果您想要關閉並保留檔案具有指定名稱的內容，請使用[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="handson"></a>CAtlTemporaryFile::HandsOn  
 呼叫這個方法來開啟現有的暫存檔案並在檔案結尾指標。  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 [CAtlTemporaryFile::HandsOff](#handsoff)和`HandsOn`用來解除關聯物件的檔案，並視需要將它重新附加。  
  
##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange  
 呼叫此方法以鎖定可防止其他處理序存取該暫存檔中的區域。  
  
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
 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案中，多個區域，但允許沒有重疊的區域。 若要成功地解除鎖定的區域，請使用[CAtlTemporaryFile::UnlockRange](#unlockrange)，確保位元組範圍就相當於先前鎖定的區域。 `LockRange`不會合併相鄰地區。如果兩個鎖定的區域是相鄰的您必須個別解除每個鎖定。  
  
##  <a name="operator_handle"></a>CAtlTemporaryFile::operator 控制代碼  
 傳回的控制代碼到暫存檔。  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>CAtlTemporaryFile::Read  
 呼叫這個方法從檔案指標所指示的位置開始，暫存檔案讀取資料。  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>參數  
 `pBuffer`  
 接收從檔案讀取資料的緩衝區指標。  
  
 `nBufSize`  
 緩衝區大小，以位元組為單位。  
  
 `nBytesRead`  
 讀取的位元組數。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Read](../../atl/reference/catlfile-class.md#read)。 若要變更之檔案指標的位置，請呼叫[CAtlTemporaryFile::Seek](#seek)。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="seek"></a>CAtlTemporaryFile::Seek  
 呼叫這個方法來移動檔案指標的暫存檔案。  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>參數  
 `nOffset`  
 以位元組為單位，從所指定的起始位置的位移， *dwFrom。*  
  
 `dwFrom`  
 起始點 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek)。 若要取得目前的檔案位置指標，呼叫[CAtlTemporaryFile::GetPosition](#getposition)。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="setsize"></a>CAtlTemporaryFile::SetSize  
 呼叫這個方法來設定暫存檔案的大小。  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>參數  
 `nNewLen`  
 新的檔案，以位元組為單位的長度。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize)。 在傳回時，檔案指標位於檔案結尾。  
  
##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName  
 呼叫這個方法傳回的暫存檔案的名稱。  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`LPCTSTR`指向的檔案名稱。  
  
### <a name="remarks"></a>備註  
 在產生檔案名稱[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)呼叫[GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]函式。 副檔名存檔一律為"TFR"。  
  
##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange  
 呼叫這個方法來解除鎖定暫存檔案的區域。  
  
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
 呼叫[CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)。  
  
##  <a name="write"></a>CAtlTemporaryFile::Write  
 呼叫這個方法將資料寫入至暫存檔檔案指標所指示的位置開始。  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `pBuffer`  
 包含要寫入檔案的資料緩衝區。  
  
 `nBufSize`  
 從緩衝區中要傳輸的位元組數目。  
  
 `pnBytesWritten`  
 寫入的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFile::Write](../../atl/reference/catlfile-class.md#write)。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [CAtlFile 類別](../../atl/reference/catlfile-class.md)

