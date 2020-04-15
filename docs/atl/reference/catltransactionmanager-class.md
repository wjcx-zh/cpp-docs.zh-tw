---
title: CAtl 交易管理員類別
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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321330"
---
# <a name="catltransactionmanager-class"></a>CAtl 交易管理員類別

CAtl交易管理員類提供內核事務管理員 (KTM) 函數的包裝。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlTransactionManager;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[*交易管理員](#dtor)|CAtl交易管理員析構函數。|
|[CAtl 交易管理員](#catltransactionmanager)|CAtl交易管理器建構函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[關閉](#close)|關閉事務句柄的一個。|
|[認可](#commit)|請求提交事務。|
|[建立](#create)|創建事務句柄。|
|[CreateFile](#createfile)|建立或打開檔案、檔案流或目錄作為事務操作。|
|[DeleteFile](#deletefile)|將現有檔案刪除為事務操作。|
|[尋找第一檔案](#findfirstfile)|將檔或子目錄搜索為已處理的操作。|
|[取得檔案屬性](#getfileattributes)|檢索指定檔或目錄的檔案系統屬性作為事務操作。|
|[取得檔案屬性Ex](#getfileattributesex)|檢索指定檔或目錄的檔案系統屬性作為事務操作。|
|[取得手柄](#gethandle)|返回事務句柄。|
|[是倒退](#isfallback)|確定是否啟用回退調用。|
|[MoveFile](#movefile)|將現有檔案或目錄(包括其子檔)作為事務操作移動。|
|[註冊創造鍵Ex](#regcreatekeyex)|創建指定的註冊表項並將其與事務關聯。 如果金鑰已存在,則函數將打開它。|
|[註冊刪除鍵](#regdeletekey)|從註冊表的指定平臺特定視圖中刪除子鍵及其值,作為事務操作。|
|[RegOpenKeyEx](#regopenkeyex)|打開指定的註冊表項並將其與事務關聯。|
|[捲軸](#rollback)|請求回滾事務。|
|[設定檔案屬性](#setfileattributes)|將檔案或目錄的屬性設置為事務處理操作。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|如果支援回退,則為 TRUE;否則。|
|[m_hTransaction](#m_htransaction)|事務句柄。|

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ATL::CAtl交易管理員](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>需求

**標題:** atl交易管理員.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>*交易管理員

CAtl交易管理員析構函數。

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>備註

在正常處理中,事務將自動提交並關閉。 如果在異常展開期間調用析構函數,則事務將回滾並關閉。

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtl 交易管理員

CAtl交易管理器建構函數。

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>參數

*b 回退*<br/>
TRUE 表示支援回退。 如果事務處理的函數失敗,類將自動調用"非事務化"函數。 FALSE 表示沒有「回退」呼叫。

*b 自動建立交易*<br/>
TRUE 表示事務處理程式是在建構函數中自動創建的。 FALSE 表示它不是。

### <a name="remarks"></a>備註

## <a name="close"></a><a name="close"></a>關閉

關閉事務句柄。

```
inline BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝器呼叫函數`CloseHandle`。 該方法在析構函數中自動調用。

## <a name="commit"></a><a name="commit"></a>提交

請求提交事務。

```
inline BOOL Commit();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝器呼叫函數`CommitTransaction`。 該方法在析構函數中自動調用。

## <a name="create"></a><a name="create"></a>建立

創建事務句柄。

```
inline BOOL Create();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝器呼叫函數`CreateTransaction`。 檢查其

## <a name="createfile"></a><a name="createfile"></a>建立檔案

建立或打開檔案、檔案流或目錄作為事務操作。

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

*lpFile 名稱*<br/>
要建立或打開的物件的名稱。

*dwddAccess*<br/>
對對象的訪問,可以概括為讀取、寫入,兩者,或兩者(零)。 最常用的值是GENERIC_READ、GENERIC_WRITE 或兩者:GENERIC_READ&#124;GENERIC_WRITE。

*dwShareMode*<br/>
對象的共用模式,可以讀取、寫入、刪除所有這些內容,或者無:0、FILE_SHARE_DELETE、FILE_SHARE_READFILE_SHARE_WRITE。

*lp安全屬性*<br/>
指向SECURITY_ATTRIBUTES結構的指標,其中包含可選的安全描述符,並確定返回的句柄是否可以由子進程繼承。 參數可以是 NULL。

*德沃創意*<br/>
要對存在和不存在的檔執行的操作。 此參數必須是無法組合的以下值之一:CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING或TRUNCATE_EXISTING。

*dwflags 與屬性*<br/>
檔屬性和標誌。 此參數可以包括可用檔案屬性 (FILE_ATTRIBUTE_* 的任意組合。 所有其他文件屬性都覆蓋FILE_ATTRIBUTE_NORMAL。 此參數還可以包含用於控制緩衝行為、訪問\*模式和其他特殊用途標誌的標誌 (FILE_FLAG_ ) 的組合。 這些值與任何FILE_ATTRIBUTE_\*值結合使用。

*h範本檔案*<br/>
具有GENERIC_READ訪問許可權的範本檔的有效句柄。 樣本檔為正在創建的檔案提供文件屬性和擴展屬性。 此參數可以是 NULL。

### <a name="return-value"></a>傳回值

返回可用於訪問物件的句柄。

### <a name="remarks"></a>備註

此包裝器呼叫函數`CreateFileTransacted`。

## <a name="deletefile"></a><a name="deletefile"></a>刪除檔案

將現有檔案刪除為事務操作。

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFile 名稱*<br/>
要刪除的檔案的名稱。

### <a name="remarks"></a>備註

此包裝器呼叫函數`DeleteFileTransacted`。

## <a name="findfirstfile"></a><a name="findfirstfile"></a>尋找第一檔案

將檔或子目錄搜索為已處理的操作。

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>參數

*lpFile 名稱*<br/>
要搜索的目錄或路徑以及檔名。 此參數可以包括通配符,如星號 (*) 或問號 ()。

*pNext資訊*<br/>
指向WIN32_FIND_DATA結構的指標,該結構接收有關找到的檔或子目錄的資訊。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值是後續調用`FindNextFile``FindClose`或 中使用的搜索句柄。 如果函數失敗或無法從*lpFileName*參數中的搜尋字串中尋找檔案,則傳回值INVALID_HANDLE_VALUE。

### <a name="remarks"></a>備註

此包裝器呼叫函數`FindFirstFileTransacted`。

## <a name="getfileattributes"></a><a name="getfileattributes"></a>取得檔案屬性

檢索指定檔或目錄的檔案系統屬性作為事務操作。

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>參數

*lpFile 名稱*<br/>
檔案或目錄的名稱。

### <a name="remarks"></a>備註

此包裝器呼叫函數`GetFileAttributesTransacted`。

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>取得檔案屬性Ex

檢索指定檔或目錄的檔案系統屬性作為事務操作。

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>參數

*lpFile 名稱*<br/>
檔案或目錄的名稱。

*fInfoLevelId*<br/>
要檢索的屬性信息級別。

*lpFile 資訊*<br/>
指向接收屬性資訊的緩衝區的指標。 存儲在此緩衝區中的屬性資訊的類型由*fInfoLevelId*的值決定。 如果*fInfoLevelId*參數為 GetFileExInfoStandard,則此參數指向WIN32_FILE_ATTRIBUTE_DATA結構。

### <a name="remarks"></a>備註

此包裝器呼叫函數`GetFileAttributesTransacted`。

## <a name="gethandle"></a><a name="gethandle"></a>取得手柄

返回事務句柄。

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>傳回值

返回類的事務句柄。 如果 未附加`CAtlTransactionManager`到句柄,則傳回 NULL。

### <a name="remarks"></a>備註

## <a name="isfallback"></a><a name="isfallback"></a>是倒退

確定是否啟用回退調用。

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>傳回值

返回 TRUE 是類支援回退調用。 否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

如果支援回退,則為 TRUE;否則。

```
BOOL m_bFallback;
```

### <a name="remarks"></a>備註

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

事務句柄。

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>備註

## <a name="movefile"></a><a name="movefile"></a>移動檔案

將現有檔案或目錄(包括其子檔)作為事務操作移動。

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>參數

*lpOld 檔案名稱*<br/>
本地電腦上的現有檔案或目錄的目前名稱。

*lpNewFile 名稱*<br/>
檔案或目錄的新名稱。 此名稱必須不存在。 新檔可能位於其他文件系統或驅動器上。 新目錄必須位於同一驅動器上。

### <a name="remarks"></a>備註

此包裝器呼叫函數`MoveFileTransacted`。

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>註冊創造鍵Ex

創建指定的註冊表項並將其與事務關聯。 如果金鑰已存在,則函數將打開它。

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

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
此函數打開或創建的子鍵的名稱。

*dw 保留*<br/>
此參數已保留,必須為零。

*lpClass*<br/>
此鍵的使用者定義類。 可以忽略此參數。 此參數可以是 NULL。

*dwOptions*<br/>
此參數可以是以下值之一:REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE 或REG_OPTION_VOLATILE。

*薩姆·阿喬*<br/>
指定金鑰的存取權限的掩碼。

*lp安全屬性*<br/>
SECURITY ATTRIBUTES 結構的指標，這個結構會判斷子處理序是否可以繼承傳回的控制代碼。 如果*lpSecurity 屬性*為 NULL,則無法繼承該句柄。

*phkResult*<br/>
指向接收打開或創建的鍵的句柄的變數的指標。 如果密鑰不是預定義的註冊表項之一,則在使用完句柄`RegCloseKey`后調用該函數。

*lpdw 處理*<br/>
指向接收以下處置值之一的變數的指標:REG_CREATED_NEW_KEY或REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="remarks"></a>備註

此包裝器呼叫函數`RegCreateKeyTransacted`。

## <a name="regdeletekey"></a><a name="regdeletekey"></a>註冊刪除鍵

從註冊表的指定平臺特定視圖中刪除子鍵及其值,作為事務操作。

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*h鍵*|打開註冊表項的句柄。|
|*lpSubkey*|要刪除的鍵的名稱。|

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="remarks"></a>備註

此包裝器呼叫函數`RegDeleteKeyTransacted`。

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

打開指定的註冊表項並將其與事務關聯。

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>參數

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
要打開的註冊表子鍵的名稱。

*ulOptions*<br/>
此參數已保留,必須為零。

*薩姆·阿喬*<br/>
指定金鑰的存取權限的掩碼。

*phkResult*<br/>
指向接收打開或創建的鍵的句柄的變數的指標。 如果密鑰不是預定義的註冊表項之一,則在使用完句柄`RegCloseKey`后調用該函數。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="remarks"></a>備註

此包裝器呼叫函數`RegOpenKeyTransacted`。

## <a name="rollback"></a><a name="rollback"></a>捲軸

請求回滾事務。

```
inline BOOL Rollback();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此包裝器呼叫函數`RollbackTransaction`。

## <a name="setfileattributes"></a><a name="setfileattributes"></a>設定檔案屬性

將檔案或目錄的屬性設置為事務處理操作。

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>參數

*lpFile 名稱*<br/>
檔案或目錄的名稱。

*dwAttributes*<br/>
要為檔設定的文件屬性。 關於詳細資訊,請參考[設定檔屬性轉換](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)。

### <a name="remarks"></a>備註

此包裝器呼叫函數`SetFileAttributesTransacted`。

## <a name="see-also"></a>另請參閱

[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
