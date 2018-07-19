---
title: CAtlTransactionManager 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15a7f6ad0620591e51d1382cd1199c52dde222ac
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882763"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 類別
CAtlTransactionManager 類別會提供核心交易管理員 (KTM) 的函式的包裝函式。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
|[關閉](#close)|其中一個關閉交易控制代碼。|  
|[認可](#commit)|要求交易被認可。|  
|[建立](#create)|建立交易控制代碼。|  
|[CreateFile](#createfile) (CreateFile 函式)|建立或開啟檔案、 檔案資料流或與交易的作業目錄。|  
|[DeleteFile](#deletefile)|為交易的作業會刪除現有的檔案。|  
|[FindFirstFile](#findfirstfile)|為交易的作業會搜尋檔案或子目錄的目錄。|  
|[GetFileAttributes](#getfileattributes)|為交易的作業會擷取指定的檔案或目錄的檔案系統屬性。|  
|[GetFileAttributesEx](#getfileattributesex)|為交易的作業會擷取指定的檔案或目錄的檔案系統屬性。|  
|[GetHandle](#gethandle)|傳回交易控制代碼。|  
|[IsFallback](#isfallback)|決定是否啟用後援的呼叫。|  
|[MoveFile](#movefile)|移動現有的檔案或目錄，包括及其子系，以交易的作業。|  
|[RegCreateKeyEx](#regcreatekeyex)|建立指定的登錄機碼，並將它與交易產生關聯。 如果索引鍵已經存在，此函式會開啟它。|  
|[RegDeleteKey](#regdeletekey)|從指定的平台特定的登錄檢視中刪除子機碼和其值為交易的作業。|  
|[RegOpenKeyEx](#regopenkeyex)|開啟指定的登錄機碼，並將它與交易產生關聯。|  
|[復原](#rollback)|交易回復的要求。|  
|[SetFileAttributes](#setfileattributes)|將檔案或目錄的屬性設定為交易的作業。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|如果支援此後援;，則為 TRUE。FALSE 否則。|  
|[m_hTransaction](#m_htransaction)|交易控制代碼。|  
  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** atltransactionmanager.h  
  
##  <a name="dtor"></a>  ~ CAtlTransactionManager  
 CAtlTransactionManager 解構函式。  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>備註  
 在正常處理中，會自動認可交易並關閉。 如果例外狀況回溯期間呼叫解構函式時，會回復交易，並將其關閉。  
  
##  <a name="catltransactionmanager"></a>  CAtlTransactionManager  
 CAtlTransactionManager 建構函式。  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bFallback*  
 TRUE 表示支援後援。 如果交易的函式失敗，此類別會自動呼叫 「 非交易式 」 函式。 FALSE 表示不包含 「 遞補 」 呼叫。  
  
 *bAutoCreateTransaction*  
 TRUE 表示建構函式中的交易處理常式會自動建立。 FALSE 表示不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="close"></a>  關閉  
 關閉交易控制代碼。  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CloseHandle`函式。 解構函式中，會自動呼叫的方法。  
  
##  <a name="commit"></a>  認可  
 要求交易被認可。  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CommitTransaction`函式。 解構函式中，會自動呼叫的方法。  
  
##  <a name="create"></a>  建立  
 建立交易控制代碼。  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CreateTransaction`函式。 檢查有  
  
##  <a name="createfile"></a>  CreateFile  
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
 *lpFileName*  
 若要建立或開啟物件的名稱。  
  
 *dwDesiredAccess*  
 存取的物件，可總結為讀取、 寫入、 兩者或兩者都關閉 （零）。 最常使用的值為 GENERIC_READ、 GENERIC_WRITE，或兩者： GENERIC_READ &#124; GENERIC_WRITE。  
  
 *dwShareMode*  
 物件，該物件可以是讀取、 寫入、 兩者、 delete、 none 或所有這些項目，共用的模式： 0，FILE_SHARE_DELETE FILE_SHARE_READ、 FILE_SHARE_WRITE。  
  
 *lpSecurityAttributes*  
 包含選擇性的安全性描述元，而且也會決定子處理序可以繼承傳回的控制代碼 SECURITY_ATTRIBUTES 結構的指標。 參數可以是 NULL。  
  
 *dwCreationDisposition*  
 要存在，且不存在的檔案上採取的動作。 這個參數必須是下列值，無法合併的其中一個： CREATE_ALWAYS、 CREATE_NEW、 OPEN_ALWAYS、 OPEN_EXISTING，還是 TRUNCATE_EXISTING。  
  
 *dwFlagsAndAttributes*  
 檔案屬性和旗標。 這個參數可以包含任何可用的檔案屬性組合 （FILE_ATTRIBUTE_ *）。 所有其他檔案屬性覆寫 FILE_ATTRIBUTE_NORMAL。 這個參數也可以包含旗標的組合 (FILE_FLAG_\*) 的緩衝行為的控制項，存取模式，以及其他的特殊用途旗標。 這些結合任何 FILE_ATTRIBUTE_\*值。  
  
 *hTemplateFile*  
 有效的控制代碼到 GENERIC_READ 存取權限的範本檔案。 檔案屬性和正在建立之檔案的擴充的屬性，就會提供範本檔案。 這個參數可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回可用來存取物件的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`CreateFileTransacted`函式。  
  
##  <a name="deletefile"></a>  DeleteFile  
 為交易的作業會刪除現有的檔案。  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>參數  
 *lpFileName*  
 要刪除的檔案的名稱。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`DeleteFileTransacted`函式。  
  
##  <a name="findfirstfile"></a>  FindFirstFile  
 為交易的作業會搜尋檔案或子目錄的目錄。  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>參數  
 *lpFileName*  
 目錄或路徑，以及要搜尋的檔案名稱。 這個參數可以包含萬用字元，例如星號 （*） 或問號 （）。  
  
 *pNextInfo*  
 接收資訊找到的檔案或子目錄 WIN32_FIND_DATA 結構的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，傳回值是在後續呼叫中使用的搜尋控制代碼`FindNextFile`或`FindClose`。 如果函式會失敗，或找不到檔案中的搜尋字串*lpFileName*參數，傳回值就是 INVALID_HANDLE_VALUE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`FindFirstFileTransacted`函式。  
  
##  <a name="getfileattributes"></a>  GetFileAttributes  
 為交易的作業會擷取指定的檔案或目錄的檔案系統屬性。  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>參數  
 *lpFileName*  
 檔案或目錄的名稱。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`GetFileAttributesTransacted`函式。  
  
##  <a name="getfileattributesex"></a>  GetFileAttributesEx  
 為交易的作業會擷取指定的檔案或目錄的檔案系統屬性。  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>參數  
 *lpFileName*  
 檔案或目錄的名稱。  
  
 *fInfoLevelId*  
 要擷取的屬性資訊的層級。  
  
 *lpFileInformation*  
 接收的屬性資訊的緩衝區指標。 會儲存到這個緩衝區的屬性資訊的類型由值決定*fInfoLevelId*。 如果*fInfoLevelId*參數是 GetFileExInfoStandard，則此參數指向 WIN32_FILE_ATTRIBUTE_DATA 結構。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`GetFileAttributesTransacted`函式。  
  
##  <a name="gethandle"></a>  GetHandle  
 傳回交易控制代碼。  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回類別的交易控制代碼。 如果傳回 NULL`CAtlTransactionManager`未附加至控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isfallback"></a>  IsFallback  
 決定是否啟用後援的呼叫。  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回 TRUE 為類別支援後援呼叫。 FALSE 否則。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bfallback"></a>  m_bFallback  
 如果支援此後援;，則為 TRUE。FALSE 否則。  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_htransaction"></a>  m_hTransaction  
 交易控制代碼。  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="movefile"></a>  MoveFile  
 移動現有的檔案或目錄，包括及其子系，以交易的作業。  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>參數  
 *lpOldFileName*  
 現有的檔案或目錄，在本機電腦上的目前的名稱。  
  
 *lpNewFileName*  
 檔案或目錄的新名稱。 此名稱不能已經存在。 新的檔案可能位於不同的檔案系統或磁碟機。 新的目錄必須位於相同的磁碟機。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`MoveFileTransacted`函式。  
  
##  <a name="regcreatekeyex"></a>  RegCreateKeyEx  
 建立指定的登錄機碼，並將它與交易產生關聯。 如果索引鍵已經存在，此函式會開啟它。  
  
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
 *hKey*  
 開啟登錄機碼的控制代碼。  
  
 *lpSubKey*  
 此函式會開啟或建立子機碼名稱。  
  
 *dwReserved*  
 這個參數已保留，而且必須為零。  
  
 *lpClass*  
 此機碼的使用者定義的類別。 可能會忽略這個參數。 這個參數可以是 NULL。  
  
 *dwOptions*  
 這個參數可以是下列值之一： REG_OPTION_BACKUP_RESTORE、 REG_OPTION_NON_VOLATILE 或 REG_OPTION_VOLATILE。  
  
 *samDesired*  
 遮罩，指定索引鍵的存取權限。  
  
 *lpSecurityAttributes*  
 SECURITY_ATTRIBUTES 建構可判斷子處理序是否可以繼承傳回的控制代碼指標。 如果*lpSecurityAttributes*是 NULL，無法繼承控制代碼。  
  
 *phkResult*  
 收到的開啟或建立金鑰的控制代碼變數的指標。 如果索引鍵不是其中一個預先定義的登錄機碼，呼叫`RegCloseKey`函式之後您完成使用控制代碼。  
  
 *lpdwDisposition*  
 此變數會接收其中一個下列的配置值的指標： REG_CREATED_NEW_KEY 或 REG_OPENED_EXISTING_KEY。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegCreateKeyTransacted`函式。  
  
##  <a name="regdeletekey"></a>  RegDeleteKey  
 從指定的平台特定的登錄檢視中刪除子機碼和其值為交易的作業。  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*hKey*|開啟登錄機碼的控制代碼。|  
|*lpSubKey*|要刪除的金鑰名稱。|  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegDeleteKeyTransacted`函式。  
  
##  <a name="regopenkeyex"></a>  RegOpenKeyEx  
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
 *hKey*  
 開啟登錄機碼的控制代碼。  
  
 *lpSubKey*  
 若要開啟登錄子機碼名稱。  
  
 *ulOptions*  
 這個參數已保留，而且必須為零。  
  
 *samDesired*  
 遮罩，指定索引鍵的存取權限。  
  
 *phkResult*  
 收到的開啟或建立金鑰的控制代碼變數的指標。 如果索引鍵不是其中一個預先定義的登錄機碼，呼叫`RegCloseKey`函式之後您完成使用控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值是 Winerror.h 中定義的非零錯誤碼  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RegOpenKeyTransacted`函式。  
  
##  <a name="rollback"></a>  復原  
 交易回復的要求。  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`RollbackTransaction`函式。  
  
##  <a name="setfileattributes"></a>  SetFileAttributes  
 將檔案或目錄的屬性設定為交易的作業。  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>參數  
 *lpFileName*  
 檔案或目錄的名稱。  
  
 *dwAttributes*  
 若要設定之檔案的檔案屬性。 如需詳細資訊，請參閱 < [SetFileAttributesTransacted](http://go.microsoft.com/fwlink/p/?linkid=158699)。  
  
### <a name="remarks"></a>備註  
 這個包裝函式呼叫`SetFileAttributesTransacted`函式。  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
