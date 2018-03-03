---
title: "CAtlTransactionManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0def8aa809cd1ccc115ccc2a09b1ae752316098f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 類別
CAtlTransactionManager 類別提供的核心交易管理員 (KTM) 的函式的包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager 解構函式。|  
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[關閉](#close)|關閉一個交易控制代碼。|  
|[認可](#commit)|要求交易被認可。|  
|[建立](#create)|建立交易控制代碼。|  
|[CreateFile](#createfile) (CreateFile 函式)|建立或開啟檔案、 檔案資料流或與交易的作業目錄。|  
|[DeleteFile](#deletefile)|為交易的作業會刪除現有的檔案。|  
|[FindFirstFile](#findfirstfile)|搜尋檔案或子目錄的目錄，以交易的作業。|  
|[GetFileAttributes](#getfileattributes)|擷取指定的檔案或目錄的檔案系統屬性成為交易的作業。|  
|[GetFileAttributesEx](#getfileattributesex)|擷取指定的檔案或目錄的檔案系統屬性成為交易的作業。|  
|[GetHandle](#gethandle)|傳回交易控制代碼。|  
|[IsFallback](#isfallback)|判斷是否啟用後援的呼叫。|  
|[MoveFile](#movefile)|移動現有的檔案或目錄，包括子系，以交易的作業。|  
|[RegCreateKeyEx](#regcreatekeyex)|建立指定的登錄機碼，並將它與交易產生關聯。 如果金鑰已存在，則此函式會開啟它。|  
|[RegDeleteKey](#regdeletekey)|從指定的平台特定的登錄檢視中刪除子機碼和其值以交易的作業。|  
|[RegOpenKeyEx](#regopenkeyex)|開啟指定的登錄機碼，並將它與交易產生關聯。|  
|[復原](#rollback)|交易回復的要求。|  
|[SetFileAttributes](#setfileattributes)|將檔案或目錄的屬性設定為交易的作業。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|`TRUE`如果支援此後援。`FALSE`否則。|  
|[m_hTransaction](#m_htransaction)|交易控制代碼。|  
  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** atltransactionmanager.h  
  
##  <a name="dtor"></a>~ CAtlTransactionManager  
 CAtlTransactionManager 解構函式。  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>備註  
 在正常處理中，會自動認可交易並關閉。 如果例外狀況回溯期間呼叫解構函式時，交易已回復，且關閉。  
  
##  <a name="catltransactionmanager"></a>CAtlTransactionManager  
 CAtlTransactionManager 建構函式。  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bFallback`  
 `TRUE`表示支援後援。 如果交易的函式失敗，，類別會自動呼叫 「 非交易式 」 函式。 `FALSE`表示沒有 「 遞補 」 呼叫。  
  
 `bAutoCreateTransaction`  
 `TRUE`指出交易處理常式會自動建立在建構函式。 `FALSE`表示它不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="close"></a>關閉  
 關閉交易控制代碼。  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CloseHandle`函式。 方法會自動呼叫解構函式中。  
  
##  <a name="commit"></a>認可  
 要求交易被認可。  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CommitTransaction`函式。 方法會自動呼叫解構函式中。  
  
##  <a name="create"></a>建立  
 建立交易控制代碼。  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CreateTransaction`函式。 檢查有  
  
##  <a name="createfile"></a>CreateFile  
 建立或開啟檔案、 檔案資料流或與交易的作業目錄。  
  
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
 `lpFileName`  
 若要建立或開啟物件的名稱。  
  
 `dwDesiredAccess`  
 存取的物件，可摘要如下讀取、 寫入、 兩者皆是或都沒有 （零）。 最常使用的值為 GENERIC_READ、 GENERIC_WRITE，或兩者： GENERIC_READ &#124;GENERIC_WRITE。  
  
 `dwShareMode`  
 物件，該物件可讀取、 寫入、 兩者，刪除所有的這些項目，或沒有任何共用的模式： 0，FILE_SHARE_DELETE、 FILE_SHARE_READ、 FILE_SHARE_WRITE。  
  
 `lpSecurityAttributes`  
 Security ATTRIBUTES 結構，包含選擇性的安全性描述元，而且也會決定子處理序可以繼承傳回的控制代碼的指標。 這個參數可以是`NULL`。  
  
 `dwCreationDisposition`  
 要存在，且不存在的檔案上採取的動作。 這個參數必須是下列值，不能結合的其中一個： CREATE_ALWAYS、 CREATE_NEW、 OPEN_ALWAYS、 OPEN_EXISTING 或 TRUNCATE_EXISTING。  
  
 `dwFlagsAndAttributes`  
 檔案屬性和旗標。 這個參數可以包含可用的檔案屬性 （FILE_ATTRIBUTE_ *） 的任何組合。 所有其他檔案屬性覆寫 FILE_ATTRIBUTE_NORMAL。 這個參數也可以包含旗標的組合 (FILE_FLAG_\*) 控制的緩衝行為，存取模式和其他特殊用途的旗標。 這些組合與任何 FILE_ATTRIBUTE_\*值。  
  
 `hTemplateFile`  
 GENERIC_READ 存取權限的範本檔案有效控制代碼。 範本檔案會提供檔案屬性和檔案所建立的擴充的屬性。 這個參數可以是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 傳回可以用來存取物件的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CreateFileTransacted`函式。  
  
##  <a name="deletefile"></a>DeleteFile  
 為交易的作業會刪除現有的檔案。  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>參數  
 `lpFileName`  
 要刪除的檔案的名稱。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`DeleteFileTransacted`函式。  
  
##  <a name="findfirstfile"></a>FindFirstFile  
 搜尋檔案或子目錄的目錄，以交易的作業。  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>參數  
 `lpFileName`  
 目錄或路徑，以及要搜尋的檔案名稱。 這個參數可以包含萬用字元，例如星號 （*） 或問號 （）。  
  
 `pNextInfo`  
 接收有關找到的檔案或子目錄資訊 WIN32_FIND_DATA 結構的指標。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，傳回值是在後續呼叫中使用的搜尋控制代碼`FindNextFile`或`FindClose`。 如果函式會失敗，或無法找出檔案中的搜尋字串從`lpFileName`參數，則傳回值就是 INVALID_HANDLE_VALUE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`FindFirstFileTransacted`函式。  
  
##  <a name="getfileattributes"></a>GetFileAttributes  
 擷取指定的檔案或目錄的檔案系統屬性成為交易的作業。  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>參數  
 `lpFileName`  
 檔案或目錄的名稱。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`GetFileAttributesTransacted`函式。  
  
##  <a name="getfileattributesex"></a>GetFileAttributesEx  
 擷取指定的檔案或目錄的檔案系統屬性成為交易的作業。  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>參數  
 `lpFileName`  
 檔案或目錄的名稱。  
  
 `fInfoLevelId`  
 要擷取的屬性資訊的層級。  
  
 `lpFileInformation`  
 接收屬性資訊的緩衝區指標。 儲存到這個緩衝區的屬性資訊的類型由值`fInfoLevelId`。 如果`fInfoLevelId`參數是 GetFileExInfoStandard，則此參數指向 WIN32_FILE_ATTRIBUTE_DATA 結構。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`GetFileAttributesTransacted`函式。  
  
##  <a name="gethandle"></a>GetHandle  
 傳回交易控制代碼。  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回類別的交易控制代碼。 傳回`NULL`如果`CAtlTransactionManager`未附加至控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isfallback"></a>IsFallback  
 判斷是否啟用後援的呼叫。  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`是此類別支援後援的呼叫。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bfallback"></a>m_bFallback  
 `TRUE`如果支援此後援。`FALSE`否則。  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_htransaction"></a>m_hTransaction  
 交易控制代碼。  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="movefile"></a>MoveFile  
 移動現有的檔案或目錄，包括子系，以交易的作業。  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>參數  
 `lpOldFileName`  
 目前的現有檔案或本機電腦上的目錄名稱。  
  
 `lpNewFileName`  
 新檔案或目錄名稱。 這個名稱必須存在。 新的檔案可能是不同的檔案系統或磁碟機上。 新的目錄必須位於相同的磁碟機上。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`MoveFileTransacted`函式。  
  
##  <a name="regcreatekeyex"></a>RegCreateKeyEx  
 建立指定的登錄機碼，並將它與交易產生關聯。 如果金鑰已存在，則此函式會開啟它。  
  
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
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 此函式會開啟或建立一個子機碼名稱。  
  
 `dwReserved`  
 這個參數已保留，而且必須是零。  
  
 `lpClass`  
 此機碼的使用者定義的類別。 可能會忽略這個參數。 這個參數可以是 NULL。  
  
 `dwOptions`  
 這個參數可以是下列值之一： REG_OPTION_BACKUP_RESTORE、 REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。  
  
 `samDesired`  
 遮罩，指定索引鍵的存取權限。  
  
 `lpSecurityAttributes`  
 Security ATTRIBUTES 結構，決定子處理序是否可以繼承傳回的控制代碼指標。 如果`lpSecurityAttributes`是`NULL`，無法繼承控制代碼。  
  
 `phkResult`  
 此變數會接收到已開啟或建立機碼的控制代碼指標。 如果索引鍵不是其中一個預先定義的登錄機碼，呼叫`RegCloseKey`函式在您完成使用此控制代碼後。  
  
 `lpdwDisposition`  
 指標變數會接收下列配置值的其中一個： REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegCreateKeyTransacted`函式。  
  
##  <a name="regdeletekey"></a>RegDeleteKey  
 從指定的平台特定的登錄檢視中刪除子機碼和其值以交易的作業。  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`hKey`|開啟登錄機碼的控制代碼。|  
|`lpSubKey`|要刪除之索引鍵名稱。|  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegDeleteKeyTransacted`函式。  
  
##  <a name="regopenkeyex"></a>RegOpenKeyEx  
 開啟指定的登錄機碼，並將它與交易產生關聯。  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 若要開啟之登錄子機碼名稱。  
  
 `ulOptions`  
 這個參數已保留，而且必須是零。  
  
 `samDesired`  
 遮罩，指定索引鍵的存取權限。  
  
 `phkResult`  
 此變數會接收到已開啟或建立機碼的控制代碼指標。 如果索引鍵不是其中一個預先定義的登錄機碼，呼叫`RegCloseKey`函式在您完成使用此控制代碼後。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值是定義於 Winerror.h 中則為非零的錯誤代碼  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegOpenKeyTransacted`函式。  
  
##  <a name="rollback"></a>復原  
 交易回復的要求。  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RollbackTransaction`函式。  
  
##  <a name="setfileattributes"></a>SetFileAttributes  
 將檔案或目錄的屬性設定為交易的作業。  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>參數  
 `lpFileName`  
 檔案或目錄的名稱。  
  
 `dwAttributes`  
 若要為檔案設定檔案屬性。 如需詳細資訊，請參閱[SetFileAttributesTransacted](http://go.microsoft.com/fwlink/p/?linkid=158699)。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`SetFileAttributesTransacted`函式。  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
