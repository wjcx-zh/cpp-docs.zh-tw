---
title: CAtlTransactionManager 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: d72867eaa449a20e676d4eddc4c94c02090334e5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497725"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 類別

CAtlTransactionManager 類別提供核心交易管理員 (KTM) 函數的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlTransactionManager;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~CAtlTransactionManager](#dtor)|CAtlTransactionManager 的析構函式。|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 的構造函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[關閉](#close)|關閉其中一個交易控制碼。|
|[Commit](#commit)|要求認可交易。|
|[建立](#create)|建立交易控制碼。|
|[CreateFile](#createfile)|建立或開啟檔案、檔案資料流程或目錄做為交易作業。|
|[DeleteFile](#deletefile)|刪除現有的檔案做為交易作業。|
|[FindFirstFile](#findfirstfile)|在目錄中搜尋檔案或子目錄, 做為交易作業。|
|[GetFileAttributes](#getfileattributes)|以交易作業的形式, 抓取指定檔案或目錄的檔案系統屬性。|
|[GetFileAttributesEx](#getfileattributesex)|以交易作業的形式, 抓取指定檔案或目錄的檔案系統屬性。|
|[GetHandle](#gethandle)|傳回交易控制碼。|
|[IsFallback](#isfallback)|判斷是否已啟用 fallback 呼叫。|
|[MoveFile](#movefile)|將現有的檔案或目錄 (包括其子系) 移動為交易作業。|
|[RegCreateKeyEx](#regcreatekeyex)|建立指定的登錄機碼, 並將它與交易產生關聯。 如果索引鍵已經存在, 則函式會將它開啟。|
|[RegDeleteKey](#regdeletekey)|從登錄的指定平臺特定視圖中, 將子機碼和其值刪除為交易作業。|
|[RegOpenKeyEx](#regopenkeyex)|開啟指定的登錄機碼, 並將它與交易產生關聯。|
|[回退](#rollback)|要求回復交易。|
|[SetFileAttributes](#setfileattributes)|將檔案或目錄的屬性設定為交易作業。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果支援 fallback, 則為 TRUE;否則為 FALSE。|
|[m_hTransaction](#m_htransaction)|交易控制碼。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>需求

**標頭:** atltransactionmanager。h

##  <a name="dtor"></a>  ~CAtlTransactionManager

CAtlTransactionManager 的析構函式。

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>備註

在正常處理中, 會自動認可和關閉交易。 如果在例外狀況回溯期間呼叫了此函式, 則會回復和關閉交易。

##  <a name="catltransactionmanager"></a>  CAtlTransactionManager

CAtlTransactionManager 的構造函式。

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>參數

*bFallback*<br/>
TRUE 表示支援 fallback。 如果交易函數失敗, 類別會自動呼叫「非交易」函式。 FALSE 表示沒有 "fallback" 呼叫。

*bAutoCreateTransaction*<br/>
TRUE 表示交易處理常式會在此函式中自動建立。 FALSE 表示它不是。

### <a name="remarks"></a>備註

##  <a name="close"></a>關閉

關閉交易控制碼。

```
inline BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝函式`CloseHandle`會呼叫函數。 方法會在析構函式中自動呼叫。

##  <a name="commit"></a>Commit

要求認可交易。

```
inline BOOL Commit();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝函式`CommitTransaction`會呼叫函數。 方法會在析構函式中自動呼叫。

##  <a name="create"></a>建立

建立交易控制碼。

```
inline BOOL Create();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝函式`CreateTransaction`會呼叫函數。 檢查

##  <a name="createfile"></a>CreateFile

建立或開啟檔案、檔案資料流程或目錄做為交易作業。

```
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
要建立或開啟之物件的名稱。

*dwDesiredAccess*<br/>
物件的存取權, 可以摘要為讀取、寫入、兩者或兩者 (零)。 最常使用的值為 GENERIC_READ、GENERIC_WRITE 或兩者:GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
物件的共用模式, 可以是 [讀取]、[寫入]、[刪除]、[全部]、[全部] 或 [無]:0、FILE_SHARE_DELETE、FILE_SHARE_READ、FILE_SHARE_WRITE。

*lpSecurityAttributes*<br/>
SECURITY ATTRIBUTES 這個結構的指標, 其中包含選擇性的安全描述項, 而且也會決定子進程是否可以繼承傳回的控制碼。 參數可以是 Null。

*dwCreationDisposition*<br/>
要對存在但不存在的檔案採取的動作。 這個參數必須是下列其中一個不能結合的值:CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING 或 TRUNCATE_EXISTING。

*dwFlagsAndAttributes*<br/>
檔案屬性和旗標。 這個參數可以包含可用檔案屬性的任意組合 (FILE_ATTRIBUTE_ *)。 所有其他的檔案屬性都會覆寫 FILE_ATTRIBUTE_NORMAL。 這個參數也可以包含用來控制緩衝行為\*、存取模式和其他特殊用途旗標的旗標 (FILE_FLAG_) 組合。 這些會結合任何 FILE_ATTRIBUTE_\*值。

*hTemplateFile*<br/>
具有 GENERIC_READ 存取權限之範本檔案的有效控制碼。 範本檔案提供所建立之檔案的檔案屬性和擴充屬性。 這個參數可以是 Null。

### <a name="return-value"></a>傳回值

傳回可用於存取物件的控制碼。

### <a name="remarks"></a>備註

此包裝函式`CreateFileTransacted`會呼叫函數。

##  <a name="deletefile"></a>  DeleteFile

刪除現有的檔案做為交易作業。

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
要刪除的檔案的名稱。

### <a name="remarks"></a>備註

此包裝函式`DeleteFileTransacted`會呼叫函數。

##  <a name="findfirstfile"></a>FindFirstFile

在目錄中搜尋檔案或子目錄, 做為交易作業。

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
目錄或路徑, 以及要搜尋的檔案名。 這個參數可以包含萬用字元, 例如星號 (*) 或問號 ()。

*pNextInfo*<br/>
WIN32_FIND_DATA 結構的指標, 它會接收找到的檔案或子目錄的相關資訊。

### <a name="return-value"></a>傳回值

如果函式成功, 則傳回值是用於後續呼叫`FindNextFile`或`FindClose`的搜尋控制碼。 如果函式失敗, 或無法在*lpFileName*參數中從搜尋字串尋找檔案, 則傳回值會是 INVALID_HANDLE_VALUE。

### <a name="remarks"></a>備註

此包裝函式`FindFirstFileTransacted`會呼叫函數。

##  <a name="getfileattributes"></a>GetFileAttributes

以交易作業的形式, 抓取指定檔案或目錄的檔案系統屬性。

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

### <a name="remarks"></a>備註

此包裝函式`GetFileAttributesTransacted`會呼叫函數。

##  <a name="getfileattributesex"></a>  GetFileAttributesEx

以交易作業的形式, 抓取指定檔案或目錄的檔案系統屬性。

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

*fInfoLevelId*<br/>
要取出的屬性資訊層級。

*lpFileInformation*<br/>
接收屬性資訊之緩衝區的指標。 儲存在這個緩衝區中的屬性資訊類型是由*fInfoLevelId*的值決定。 如果*fInfoLevelId*參數為 GetFileExInfoStandard, 則此參數會指向 WIN32_FILE_ATTRIBUTE_DATA 結構。

### <a name="remarks"></a>備註

此包裝函式`GetFileAttributesTransacted`會呼叫函數。

##  <a name="gethandle"></a>  GetHandle

傳回交易控制碼。

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>傳回值

傳回類別的交易控制碼。 如果未附加至`CAtlTransactionManager`控制碼, 則會傳回 Null。

### <a name="remarks"></a>備註

##  <a name="isfallback"></a>IsFallback

判斷是否已啟用 fallback 呼叫。

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>傳回值

如果類別支援回溯呼叫, 則傳回 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="m_bfallback"></a>  m_bFallback

如果支援 fallback, 則為 TRUE;否則為 FALSE。

```
BOOL m_bFallback;
```

### <a name="remarks"></a>備註

##  <a name="m_htransaction"></a>  m_hTransaction

交易控制碼。

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>備註

##  <a name="movefile"></a>  MoveFile

將現有的檔案或目錄 (包括其子系) 移動為交易作業。

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>參數

*lpOldFileName*<br/>
本機電腦上現有檔案或目錄的目前名稱。

*lpNewFileName*<br/>
檔案或目錄的新名稱。 這個名稱不能已經存在。 新檔案可能在不同的檔案系統或磁片磁碟機上。 新的目錄必須位於相同的磁片磁碟機上。

### <a name="remarks"></a>備註

此包裝函式`MoveFileTransacted`會呼叫函數。

##  <a name="regcreatekeyex"></a>RegCreateKeyEx

建立指定的登錄機碼, 並將它與交易產生關聯。 如果索引鍵已經存在, 則函式會將它開啟。

```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
此函式開啟或建立的子機碼名稱。

*dwReserved*<br/>
這個參數是保留的, 而且必須為零。

*lpClass*<br/>
此索引鍵的使用者定義類別。 可以忽略這個參數。 這個參數可以是 Null。

*dwOptions*<br/>
這個參數可以是下列其中一個值:REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。

*samDesired*<br/>
遮罩, 指定金鑰的存取權限。

*lpSecurityAttributes*<br/>
SECURITY ATTRIBUTES 這個結構的指標, 判斷子進程是否可以繼承傳回的控制碼。 如果*lpSecurityAttributes*為 Null, 則無法繼承控制碼。

*phkResult*<br/>
可接收已開啟或已建立索引鍵控制碼之變數的指標。 如果索引鍵不是其中一個預先定義的登錄機碼, `RegCloseKey`則在您完成使用控制碼之後, 請呼叫函式。

*lpdwDisposition*<br/>
可接收下列其中一個配置值之變數的指標:REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>傳回值

如果函式成功, 則傳回值為 ERROR_SUCCESS。 如果函式失敗, 則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="remarks"></a>備註

此包裝函式`RegCreateKeyTransacted`會呼叫函數。

##  <a name="regdeletekey"></a>RegDeleteKey

從登錄的指定平臺特定視圖中, 將子機碼和其值刪除為交易作業。

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*hKey*|開啟登錄機碼的控制碼。|
|*lpSubKey*|要刪除之金鑰的名稱。|

### <a name="return-value"></a>傳回值

如果函式成功, 則傳回值為 ERROR_SUCCESS。 如果函式失敗, 則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="remarks"></a>備註

此包裝函式`RegDeleteKeyTransacted`會呼叫函數。

##  <a name="regopenkeyex"></a>RegOpenKeyEx

開啟指定的登錄機碼, 並將它與交易產生關聯。

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
要開啟之登錄子機碼的名稱。

*ulOptions*<br/>
這個參數是保留的, 而且必須為零。

*samDesired*<br/>
遮罩, 指定金鑰的存取權限。

*phkResult*<br/>
可接收已開啟或已建立索引鍵控制碼之變數的指標。 如果索引鍵不是其中一個預先定義的登錄機碼, `RegCloseKey`則在您完成使用控制碼之後, 請呼叫函式。

### <a name="return-value"></a>傳回值

如果函式成功, 則傳回值為 ERROR_SUCCESS。 如果函式失敗, 則傳回值為 Winerror.h 中定義的非零的錯誤碼。

### <a name="remarks"></a>備註

此包裝函式`RegOpenKeyTransacted`會呼叫函數。

##  <a name="rollback"></a>回退

要求回復交易。

```
inline BOOL Rollback();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝函式`RollbackTransaction`會呼叫函數。

##  <a name="setfileattributes"></a>SetFileAttributes

將檔案或目錄的屬性設定為交易作業。

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

*dwAttributes*<br/>
要為檔案設定的檔案屬性。 如需詳細資訊, 請參閱[SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)。

### <a name="remarks"></a>備註

此包裝函式`SetFileAttributesTransacted`會呼叫函數。

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
