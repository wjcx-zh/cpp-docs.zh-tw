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
ms.openlocfilehash: 74afc1a82c12d6138198f5696d300825e06aba1e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562212"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 類別

CAtlTransactionManager 類別提供 (KTM) 函式的核心交易管理員包裝函式。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager 的函式。|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[關閉](#close)|關閉一個交易控制碼。|
|[認可](#commit)|要求認可交易。|
|[建立](#create)|建立交易控制碼。|
|[CreateFile](#createfile)|建立或開啟檔案、檔案資料流程或目錄做為交易作業。|
|[DeleteFile](#deletefile)|將現有的檔案刪除為交易作業。|
|[FindFirstFile](#findfirstfile)|在目錄中搜尋檔案或子目錄，以做為交易作業。|
|[GetFileAttributes](#getfileattributes)|將指定檔案或目錄的檔案系統屬性抓取為交易作業。|
|[GetFileAttributesEx](#getfileattributesex)|將指定檔案或目錄的檔案系統屬性抓取為交易作業。|
|[GetHandle](#gethandle)|傳回交易控制碼。|
|[IsFallback](#isfallback)|判斷是否已啟用回溯呼叫。|
|[MoveFile](#movefile)|將現有的檔案或目錄（包括其子系）移為交易作業。|
|[RegCreateKeyEx](#regcreatekeyex)|建立指定的登錄機碼，並將它與交易產生關聯。 如果索引鍵已經存在，則函式會將它開啟。|
|[RegDeleteKey](#regdeletekey)|從登錄中指定的平臺特定視圖，刪除子機碼和其值，以做為交易作業。|
|[RegOpenKeyEx](#regopenkeyex)|開啟指定的登錄機碼，並將它與交易產生關聯。|
|[回 滾](#rollback)|要求回復交易。|
|[SetFileAttributes](#setfileattributes)|將檔案或目錄的屬性設定為交易作業。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果支援回溯，則為 TRUE;否則為 FALSE。|
|[m_hTransaction](#m_htransaction)|交易控制碼。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ATL：： CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>規格需求

**標頭：** atltransactionmanager。h

## <a name="catltransactionmanager"></a><a name="dtor"></a>  ~ CAtlTransactionManager

CAtlTransactionManager 的函式。

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>備註

在正常處理過程中，會自動認可和關閉交易。 如果在例外狀況回溯期間呼叫此函式，則會回復並關閉交易。

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a> CAtlTransactionManager

CAtlTransactionManager 函式。

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>參數

*bFallback*<br/>
TRUE 表示支援回滾。 如果交易函式失敗，類別會自動呼叫「非交易」函數。 FALSE 表示沒有任何「回溯」呼叫。

*bAutoCreateTransaction*<br/>
TRUE 表示在函式中自動建立交易處理常式。 FALSE 表示它不是。

### <a name="remarks"></a>備註

## <a name="close"></a><a name="close"></a> 關閉

關閉交易控制碼。

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `CloseHandle` 函數。 方法會在「函式」中自動呼叫。

## <a name="commit"></a><a name="commit"></a> 提交

要求認可交易。

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `CommitTransaction` 函數。 方法會在「函式」中自動呼叫。

## <a name="create"></a><a name="create"></a> 建立

建立交易控制碼。

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `CreateTransaction` 函數。 查看

## <a name="createfile"></a><a name="createfile"></a> CreateFile

建立或開啟檔案、檔案資料流程或目錄做為交易作業。

```cpp
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
物件的存取權，可以摘要為讀取、寫入、兩者或不 (零) 。 最常使用的值為 GENERIC_READ、GENERIC_WRITE 或兩者： GENERIC_READ &#124; GENERIC_WRITE。

*dwShareMode*<br/>
物件的共用模式，可以是 [讀取]、[寫入]、[刪除]、[全部] 或 [無]：0、FILE_SHARE_DELETE、FILE_SHARE_READ FILE_SHARE_WRITE。

*lpSecurityAttributes*<br/>
SECURITY_ATTRIBUTES 結構的指標，其中包含選擇性的安全描述項，也會判斷傳回的控制碼是否可由子進程繼承。 參數可以是 Null。

*dwCreationDisposition*<br/>
要對存在且不存在的檔案採取的動作。 此參數必須是下列其中一個值（無法合併）： CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING 或 TRUNCATE_EXISTING。

*dwFlagsAndAttributes*<br/>
檔案屬性和旗標。 此參數可包含可用檔案屬性的任意組合 (FILE_ATTRIBUTE_ * ) 。 所有其他檔案屬性都會覆寫 FILE_ATTRIBUTE_NORMAL。 此參數也可以包含旗標 (FILE_FLAG_ \*) 的組合，以控制緩衝行為、存取模式和其他特殊用途旗標。 這些會與任何 FILE_ATTRIBUTE_ \* 值結合。

*hTemplateFile*<br/>
具有 GENERIC_READ 存取權限之範本檔案的有效控制碼。 範本檔案提供所建立檔案的檔案屬性和擴充屬性。 這個參數可以是 Null。

### <a name="return-value"></a>傳回值

傳回可以用來存取物件的控制碼。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `CreateFileTransacted` 函數。

## <a name="deletefile"></a><a name="deletefile"></a> DeleteFile

將現有的檔案刪除為交易作業。

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
要刪除的檔案的名稱。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `DeleteFileTransacted` 函數。

## <a name="findfirstfile"></a><a name="findfirstfile"></a> FindFirstFile

在目錄中搜尋檔案或子目錄，以做為交易作業。

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
目錄或路徑，以及要搜尋的檔案名。 這個參數可以包含萬用字元，例如星號 ( * ) 或 ( # A3 的問號。

*pNextInfo*<br/>
WIN32_FIND_DATA 結構的指標，此結構會接收找到之檔案或子目錄的相關資訊。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值是在或的後續呼叫中使用的搜尋控制碼 `FindNextFile` `FindClose` 。 如果函式失敗或無法從 *lpFileName* 參數的搜尋字串中找到檔案，則傳回值為 INVALID_HANDLE_VALUE。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `FindFirstFileTransacted` 函數。

## <a name="getfileattributes"></a><a name="getfileattributes"></a> GetFileAttributes

將指定檔案或目錄的檔案系統屬性抓取為交易作業。

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `GetFileAttributesTransacted` 函數。

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a> GetFileAttributesEx

將指定檔案或目錄的檔案系統屬性抓取為交易作業。

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

*fInfoLevelId*<br/>
要取得之屬性資訊的層級。

*lpFileInformation*<br/>
接收屬性資訊之緩衝區的指標。 儲存在這個緩衝區中的屬性資訊型別取決於 *fInfoLevelId*的值。 如果 *fInfoLevelId* 參數為 GetFileExInfoStandard，則這個參數會指向 WIN32_FILE_ATTRIBUTE_DATA 結構。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `GetFileAttributesTransacted` 函數。

## <a name="gethandle"></a><a name="gethandle"></a> GetHandle

傳回交易控制碼。

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>傳回值

傳回類別的交易控制碼。 如果未 `CAtlTransactionManager` 附加至控制碼，則傳回 Null。

### <a name="remarks"></a>備註

## <a name="isfallback"></a><a name="isfallback"></a> IsFallback

判斷是否已啟用回溯呼叫。

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>傳回值

如果類別支援回溯呼叫，則傳回 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="m_bfallback"></a><a name="m_bfallback"></a> m_bFallback

如果支援回溯，則為 TRUE;否則為 FALSE。

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>備註

## <a name="m_htransaction"></a><a name="m_htransaction"></a> m_hTransaction

交易控制碼。

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>備註

## <a name="movefile"></a><a name="movefile"></a> MoveFile

將現有的檔案或目錄（包括其子系）移為交易作業。

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>參數

*lpOldFileName*<br/>
目前在本機電腦上的現有檔案或目錄的名稱。

*lpNewFileName*<br/>
檔案或目錄的新名稱。 此名稱不能已經存在。 新檔案可能位於不同的檔案系統或磁片磁碟機上。 新的目錄必須位於相同的磁片磁碟機上。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `MoveFileTransacted` 函數。

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a> RegCreateKeyEx

建立指定的登錄機碼，並將它與交易產生關聯。 如果索引鍵已經存在，則函式會將它開啟。

```cpp
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

*>dwreserved*<br/>
此參數是保留的，而且必須為零。

*lpClass*<br/>
此索引鍵的使用者定義類別。 您可以忽略這個參數。 這個參數可以是 Null。

*>dwoptions*<br/>
這個參數可以是下列其中一個值： REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。

*samDesired*<br/>
指定金鑰存取權限的遮罩。

*lpSecurityAttributes*<br/>
SECURITY ATTRIBUTES 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果 *lpSecurityAttributes* 為 Null，則無法繼承控制碼。

*phkResult*<br/>
變數的指標，此變數會接收開啟或建立之索引鍵的控制碼。 如果金鑰不是其中一個預先定義的登錄機碼， `RegCloseKey` 則在您完成使用控制碼之後，請呼叫該函式。

*lpdwDisposition*<br/>
變數的指標，此變數會接收下列其中一個配置值： REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `RegCreateKeyTransacted` 函數。

## <a name="regdeletekey"></a><a name="regdeletekey"></a> RegDeleteKey

從登錄中指定的平臺特定視圖，刪除子機碼和其值，以做為交易作業。

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>參數

*hKey*\
開啟登錄機碼的控制碼。

*lpSubKey*\
要刪除之金鑰的名稱。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `RegDeleteKeyTransacted` 函數。

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a> RegOpenKeyEx

開啟指定的登錄機碼，並將它與交易產生關聯。

```cpp
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
要開啟的登錄子機碼名稱。

*ulOptions*<br/>
此參數是保留的，而且必須為零。

*samDesired*<br/>
指定金鑰存取權限的遮罩。

*phkResult*<br/>
變數的指標，此變數會接收開啟或建立之索引鍵的控制碼。 如果金鑰不是其中一個預先定義的登錄機碼， `RegCloseKey` 則在您完成使用控制碼之後，請呼叫該函式。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `RegOpenKeyTransacted` 函數。

## <a name="rollback"></a><a name="rollback"></a> 回 滾

要求回復交易。

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `RollbackTransaction` 函數。

## <a name="setfileattributes"></a><a name="setfileattributes"></a> SetFileAttributes

將檔案或目錄的屬性設定為交易作業。

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>參數

*lpFileName*<br/>
檔案或目錄的名稱。

*dwAttributes*<br/>
要為檔案設定的檔案屬性。 如需詳細資訊，請參閱 [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)。

### <a name="remarks"></a>備註

這個包裝函式會呼叫 `SetFileAttributesTransacted` 函數。

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
