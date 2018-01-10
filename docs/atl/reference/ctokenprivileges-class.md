---
title: "CTokenPrivileges 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs: C++
helpviewer_keywords: CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dc0fb58d1b92fac1462b355b9afb353554f3f23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 類別
這個類別是包裝函式**TOKEN_PRIVILEGES**結構。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|建構函式。|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|新增一或多個權限可以`CTokenPrivileges`物件。|  
|[CTokenPrivileges::Delete](#delete)|刪除權限`CTokenPrivileges`物件。|  
|[CTokenPrivileges::DeleteAll](#deleteall)|刪除所有的權限從`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetCount](#getcount)|傳回的權限中的項目數`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|擷取顯示名稱中包含的權限`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetLength](#getlength)|傳回以位元組為單位來保存所需的緩衝區大小**TOKEN_PRIVILEGES**結構由`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|擷取的本機唯一識別碼 (Luid) 和屬性的旗標從`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|擷取的權限名稱和屬性的旗標從`CTokenPrivileges`物件。|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|將指標傳回至**TOKEN_PRIVILEGES**結構。|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|擷取與指定權限名稱相關聯的屬性。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|將值轉換為指標**TOKEN_PRIVILEGES**結構。|  
|[CTokenPrivileges::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一個物件，描述處理序或執行緒的安全性內容，並配置給每位使用者登入 Windows NT 或 Windows 2000 的系統。  
  
 存取權杖用來描述不同的安全性權限授與給每位使用者。 權限呼叫本機唯一識別碼的 64 位元數字所組成 ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) 和描述元字串。  
  
 `CTokenPrivileges`類別是包裝函式[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構，並包含 0 或更多權限。 可以新增權限，已刪除或查詢使用提供的類別方法。  
  
 如需在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h  
  
##  <a name="add"></a>CTokenPrivileges::Add  
 新增一或多個權限可以`CTokenPrivileges`存取權杖的物件。  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 以 null 終止的字串指定的權限，名稱 WINNT 中所定義的指標。H 標頭檔。  
  
 `bEnable`  
 如果為 true，則會啟用特殊權限。 如果為 false，則會停用權限。  
  
 `rPrivileges`  
 若要參考[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構。 權限和屬性會從這個結構複製並新增到`CTokenPrivileges`物件。  
  
### <a name="return-value"></a>傳回值  
 這個方法的第一種形式傳回權限已成功新增，false 否則如果為 true。  
  
##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges  
 建構函式。  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CTokenPrivileges`將指派給新物件的物件。  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構，以指派給新`CTokenPrivileges`物件。  
  
### <a name="remarks"></a>備註  
 `CTokenPrivileges`物件可以選擇性地建立使用**TOKEN_PRIVILEGES**結構或先前已定義`CTokenPrivileges`物件。  
  
##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges  
 解構函式。  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放所有配置的資源。  
  
##  <a name="delete"></a>CTokenPrivileges::Delete  
 刪除權限`CTokenPrivileges`存取權杖的物件。  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 以 null 終止的字串指定的權限，名稱 WINNT 中所定義的指標。H 標頭檔。 例如，這個參數可以指定常數 SE_SECURITY_NAME 或其對應的字串"SeSecurityPrivilege。 」  
  
### <a name="return-value"></a>傳回值  
 如果權限程式已成功刪除，則為 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 此方法相當實用，做為建立受限制的權杖，在 Windows 2000 的工具。  
  
##  <a name="deleteall"></a>CTokenPrivileges::DeleteAll  
 刪除所有的權限從`CTokenPrivileges`存取權杖的物件。  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>備註  
 刪除所有的權限包含在`CTokenPrivileges`存取權杖的物件。  
  
##  <a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames  
 擷取顯示名稱中包含的權限`CTokenPrivileges`存取權杖的物件。  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pDisplayNames`  
 `CString` 物件陣列的指標。 **Cname**定義為 typedef: **CTokenPrivileges::CAtlArray\<CString >**。  
  
### <a name="remarks"></a>備註  
 參數`pDisplayNames`是陣列的指標`CString`物件將會接收對應中所包含的權限顯示名稱`CTokenPrivileges`物件。 這個方法會擷取顯示名稱，只會針對 WINNT 定義權限區段中指定的權限。H.  
  
 這個方法會擷取可顯示名稱： 例如，如果 SE_REMOTE_SHUTDOWN_NAME 屬性名稱，可顯示的名稱是 「 從遠端系統強制關閉 」。 若要取得系統名稱，請使用[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)。  
  
##  <a name="getcount"></a>CTokenPrivileges::GetCount  
 傳回的權限中的項目數`CTokenPrivileges`物件。  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回中所包含的權限的`CTokenPrivileges`物件。  
  
##  <a name="getlength"></a>CTokenPrivileges::GetLength  
 傳回的長度`CTokenPrivileges`物件。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回保留所需的位元組數目**TOKEN_PRIVILEGES**結構由`CTokenPrivileges`物件，包括所有包含的權限項目。  
  
##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes  
 擷取的本機唯一識別碼 (Luid) 和屬性的旗標從`CTokenPrivileges`物件。  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pPrivileges`  
 陣列的指標[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)物件。 **CLUIDArray** typedef 定義為**CAtlArray\<LUID > CLUIDArray**。  
  
 `pAttributes`  
 DWORD 物件的陣列指標。 如果這個參數省略或是 NULL，不會擷取屬性。 **CAttributes** typedef 定義為**CAtlArray \<DWORD > CAttributes**。  
  
### <a name="remarks"></a>備註  
 這個方法會列舉中所包含的權限的所有`CTokenPrivileges`存取權杖的物件，並將個別的 Luid，以及 （選擇性） 的屬性旗標放入陣列物件。  
  
##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes  
 擷取的名稱和屬性的旗標從`CTokenPrivileges`物件。  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pNames*  
 陣列的指標`CString`物件。 **Cname** typedef 定義為**CAtlArray \<CString > Cname**。  
  
 `pAttributes`  
 DWORD 物件的陣列指標。 如果這個參數省略或是 NULL，不會擷取屬性。 **CAttributes** typedef 定義為**CAtlArray \<DWORD > CAttributes**。  
  
### <a name="remarks"></a>備註  
 這個方法會列舉中所包含的權限的所有`CTokenPrivileges`物件，將放入陣列物件的名稱，以及 （選擇性） 的屬性旗標。  
  
 這個方法會擷取的屬性名稱，而不是可顯示名稱： 例如，如果 SE_REMOTE_SHUTDOWN_NAME 屬性名稱，系統名稱是"SeRemoteShutdownPrivilege。 」 若要取得可顯示的名稱，請使用方法[CTokenPrivileges::GetDisplayNames](#getdisplaynames)。  
  
##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 將指標傳回至**TOKEN_PRIVILEGES**結構。  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構。  
  
##  <a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege  
 擷取與指定權限名稱相關聯的屬性。  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 以 null 終止的字串指定的權限，名稱 WINNT 中所定義的指標。H 標頭檔。 例如，這個參數可以指定常數 SE_SECURITY_NAME 或其對應的字串"SeSecurityPrivilege。 」  
  
 `pdwAttributes`  
 接收屬性的變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果屬性因已順利擷取，則為 false，則傳回 true。  
  
##  <a name="operator_eq"></a>CTokenPrivileges::operator =  
 指派運算子。  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構来指派給`CTokenPrivileges`物件。  
  
 `rhs`  
 `CTokenPrivileges`將指派給物件的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CTokenPrivileges`物件。  
  
##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 將值轉換為指標**TOKEN_PRIVILEGES**結構。  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>備註  
 將值轉換為指標[TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)結構。  
  
## <a name="see-also"></a>請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)
