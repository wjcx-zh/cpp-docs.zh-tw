---
title: "CSid 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSid
- ATL::CSid
- ATL.CSid
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
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
ms.openlocfilehash: ceb0ab95d18e1336584eab45bc00ce769efd7384
ms.lasthandoff: 02/24/2017

---
# <a name="csid-class"></a>CSid 類別
這個類別是包裝函式`SID`（安全性識別碼） 結構。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSid
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|`CSid` 物件的陣列。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSid::CSid](#csid)|建構函式。|  
|[CSid:: ~ CSid](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|傳回關聯的帳戶名稱`CSid`物件。|  
|[CSid::Domain](#domain)|傳回關聯的網域名稱`CSid`物件。|  
|[CSid::EqualPrefix](#equalprefix)|測試`SID`（安全性識別碼） 前置詞是否相等。|  
|[CSid::GetLength](#getlength)|傳回的長度`CSid`物件。|  
|[CSid::GetPSID](#getpsid)|傳回的指標`SID`結構。|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|傳回的指標**SID_IDENTIFIER_AUTHORITY**結構。|  
|[CSid::GetSubAuthority](#getsubauthority)|傳回指定的局部授權中**SID**結構。|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|傳回局部授權計數。|  
|[CSid::IsValid](#isvalid)|測試`CSid`物件的有效性。|  
|[CSid::LoadAccount](#loadaccount)|更新`CSid`指定帳戶名稱和網域，或將現有物件`SID`結構。|  
|[CSid::Sid](#sid)|傳回的識別碼字串。|  
|[CSid::SidNameUse](#sidnameuse)|傳回的狀態描述`CSid`物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|指派運算子。|  
|[運算子 const SID *](#operator_const_sid__star)|轉換 （cast)`CSid`物件的指標`SID`結構。|  
  
### <a name="global-operators"></a>全域運算子  
  
|||  
|-|-|  
|[運算子 = =](#operator_eq_eq)|測試兩個安全性描述元物件相等|  
|[運算子 ！ =](#operator_neq)|測試兩個安全性描述元物件不相等|  
|[運算子\<](#operator_lt_)|比較兩個安全性描述元物件的相對值。|  
|[運算子 >](#operator_gt_)|比較兩個安全性描述元物件的相對值。|  
|[運算子\<=](#operator_lt__eq)|比較兩個安全性描述元物件的相對值。|  
|[運算子 > =](#operator_gt__eq)|比較兩個安全性描述元物件的相對值。|  
  
## <a name="remarks"></a>備註  
 `SID`結構是用來唯一識別使用者或群組的可變長度結構。  
  
 應用程式不應該修改`SID`結構直接，但是改為使用這個包裝函式中提供的方法。 另請參閱[AtlGetOwnerSid](http://msdn.microsoft.com/library/0e3a2606-74b8-4412-9803-bb437e22da85)， [AtlSetGroupSid](http://msdn.microsoft.com/library/83531d32-11ab-4a68-a3c6-1bfa54ab8dfa)， [AtlGetGroupSid](http://msdn.microsoft.com/library/8e7ec6b9-15c8-4a8a-977e-1e4c853d0be7)，和[AtlSetOwnerSid](http://msdn.microsoft.com/library/3a8abb76-1d2c-465d-a5e8-62a12a3c37f3)。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="a-nameaccountnamea--csidaccountname"></a><a name="accountname"></a>CSid::AccountName  
 傳回關聯的帳戶名稱`CSid`物件。  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 傳回`LPCTSTR`指向帳戶的名稱。  
  
### <a name="remarks"></a>備註  
 這個方法會嘗試找不到指定之名稱`SID`（安全性識別碼）。 完整的詳細資訊，請參閱[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果沒有帳戶名稱`SID`可以找到`AccountName`會傳回空字串。 這可能是網路逾時防止這個方法尋找名稱。 它也會發生與任何對應的帳戶名稱，例如登入安全性識別碼`SID`可識別登入工作階段。  
  
##  <a name="a-namecsida--csidcsid"></a><a name="csid"></a>CSid::CSid  
 建構函式。  
  
```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 將現有`CSid`物件或`SID`（安全性識別碼） 結構。  
  
 *IdentifierAuthority*  
 授權單位。  
  
 *nSubAuthorityCount*  
 局部授權計數。  
  
 `pszAccountName`  
 帳戶名稱。  
  
 `pszSystem`  
 系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串為 NULL，會改用本機系統。  
  
 `pSid`  
 指標`SID`結構。  
  
### <a name="remarks"></a>備註  
 建構函式初始化`CSid`物件，將內部資料成員設定為*SidTypeInvalid*，或從現有複製設定`CSid`， `SID`，或現有的帳戶。  
  
 如果初始化失敗，建構函式會擲回[CAtlException 類別](../../atl/reference/catlexception-class.md)。  
  
##  <a name="a-namedtora--csidcsid"></a><a name="dtor"></a>CSid:: ~ CSid  
 解構函式。  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放物件所取得的任何資源。  
  
##  <a name="a-namecsidarraya--csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray  
 陣列[CSid](../../atl/reference/csid-class.md)物件。  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>備註  
 此 typedef 指定可以用於擷取的 ACL （存取控制清單） 的安全性識別元陣列型別。 請參閱[CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。  
  
##  <a name="a-namedomaina--csiddomain"></a><a name="domain"></a>CSid::Domain  
 傳回關聯的網域名稱`CSid`物件。  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 傳回`LPCTSTR`指向網域。  
  
### <a name="remarks"></a>備註  
 這個方法會嘗試找不到指定之名稱`SID`（安全性識別碼）。 完整的詳細資訊，請參閱[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166)。  
  
 如果沒有帳戶名稱`SID`可以找到**網域**傳回的網域為空字串。 這可能是網路逾時防止這個方法尋找名稱。 它也會發生與任何對應的帳戶名稱，例如登入安全性識別碼`SID`可識別登入工作階段。  
  
##  <a name="a-nameequalprefixa--csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix  
 測試`SID`（安全性識別碼） 前置詞是否相等。  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `SID` （安全性識別碼） 的結構或`CSid`来比較的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**成功時， **false**失敗。  
  
### <a name="remarks"></a>備註  
 請參閱[EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-namegetlengtha--csidgetlength"></a><a name="getlength"></a>CSid::GetLength  
 傳回的長度`CSid`物件。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的長度，以位元組為單位的`CSid`物件。  
  
### <a name="remarks"></a>備註  
 如果`CSid`結構無效，則傳回值是未定義。 然後再呼叫`GetLength`，使用[CSid::IsValid](#isvalid)成員函式來確認`CSid`有效。  
  
> [!NOTE]
>  在偵錯組建中的函式會判斷提示，如果`CSid`物件無效。  
  
##  <a name="a-namegetpsida--csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID  
 傳回的指標`SID`（安全性識別碼） 結構。  
  
```
const SID* GetPSID() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 傳回的位址`CSid`物件的基礎`SID`結構。  
  
##  <a name="a-namegetpsididentifierauthoritya--csidgetpsididentifierauthority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY  
 傳回的指標**SID_IDENTIFIER_AUTHORITY**結構。  
  
```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回的位址**SID_IDENTIFIER_AUTHORITY**結構。 如果失敗，傳回的值會是未定義。 如果發生失敗狀況可能`CSid`物件不是有效的在此情況下[CSid::IsValid](#isvalid)方法會傳回**false**。 函式`GetLastError`可以擴充的錯誤資訊來呼叫。  
  
> [!NOTE]
>  在偵錯組建中的函式會判斷提示，如果`CSid`物件無效。  
  
##  <a name="a-namegetsubauthoritya--csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority  
 傳回指定的局部授權中`SID`（安全性識別碼） 結構。  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>參數  
 *nSubAuthority*  
 局部授權。  
  
### <a name="return-value"></a>傳回值  
 傳回所參考的局部授權*nSubAuthority。* 局部授權值是相對識別碼 (RID)。  
  
### <a name="remarks"></a>備註  
 *NSubAuthority*參數會指定用來識別此方法會傳回局部授權陣列元素的索引值。 這個方法會執行任何驗證測試，這個值。 應用程式可以呼叫[CSid::GetSubAuthorityCount](#getsubauthoritycount)探索可接受值的範圍。  
  
> [!NOTE]
>  在偵錯組建中的函式會判斷提示，如果`CSid`物件無效。  
  
##  <a name="a-namegetsubauthoritycounta--csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount  
 傳回局部授權計數。  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則傳回值是局部授權計數。  
  
 如果方法失敗，傳回的值會是未定義。 如果此方法會失敗`CSid`物件無效。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。  
  
> [!NOTE]
>  在偵錯組建中的函式會判斷提示，如果`CSid`物件無效。  
  
##  <a name="a-nameisvalida--csidisvalid"></a><a name="isvalid"></a>CSid::IsValid  
 測試`CSid`物件的有效性。  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果`CSid`物件是否有效， **false**如果不是。 此方法，沒有延伸錯誤資訊請勿呼叫`GetLastError`。  
  
### <a name="remarks"></a>備註  
 `IsValid`方法會驗證`CSid`藉由驗證修訂編號是已知的範圍內，而且 subauthorities 數目小於最大值的物件。  
  
##  <a name="a-nameloadaccounta--csidloadaccount"></a><a name="loadaccount"></a>CSid::LoadAccount  
 更新`CSid`物件指定的帳戶名稱和網域或現有的 SID （安全性識別碼） 結構。  
  
```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszAccountName`  
 帳戶名稱。  
  
 `pszSystem`  
 系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串為 NULL，會改用本機系統。  
  
 `pSid`  
 指標[SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx)結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**成功時， **false**失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。  
  
### <a name="remarks"></a>備註  
 `LoadAccount`嘗試尋找指定之名稱的安全性識別碼。 請參閱[LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx)如需詳細資訊。  
  
##  <a name="a-nameoperatoreqa--csidoperator-"></a><a name="operator_eq"></a>CSid::operator =  
 指派運算子。  
  
```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`要指派給`CSid`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回參考更新的`CSid`物件。  
  
##  <a name="a-nameoperatoreqeqa--csidoperator-"></a><a name="operator_eq_eq"></a>CSid::operator = =  
 測試兩個安全性描述元物件相等。  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 = = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 = = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**安全性描述元相等，否則如果**false**。  
  
##  <a name="a-nameoperatorneqa--csidoperator-"></a><a name="operator_neq"></a>CSid::operator ！ =  
 測試兩個安全性描述元物件不相等。  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 ！ = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 ！ = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**安全性描述元是否不相等，否則如果**false**。  
  
##  <a name="a-nameoperatorlta--csidoperator-lt"></a><a name="operator_lt"></a>CSid::operator&lt;  
 比較兩個安全性描述元物件的相對值。  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 ！ = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 ！ = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**如果`lhs`是小於`rhs`，否則為**false**。  
  
##  <a name="a-nameoperatorlteqa--csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::operator&lt;=  
 比較兩個安全性描述元物件的相對值。  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 ！ = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 ！ = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**如果`lhs`是否小於或等於`rhs`，否則為**false**。  
  
##  <a name="a-nameoperatorgta--csidoperator-gt"></a><a name="operator_gt"></a>CSid::operator&gt;  
 比較兩個安全性描述元物件的相對值。  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 ！ = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 ！ = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**如果`lhs`大於`rhs`，否則為**false**。  
  
##  <a name="a-nameoperatorgteqa--csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::operator&gt;=  
 比較兩個安全性描述元物件的相對值。  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 `SID` （安全性識別碼） 或`CSid`出現在左邊 ！ = 運算子。  
  
 `rhs`  
 `SID` （安全性識別碼） 或`CSid`顯示於右側 ！ = 運算子。  
  
### <a name="return-value"></a>傳回值  
 **true**如果`lhs`大於或等於`rhs`，否則為**false**。  
  
##  <a name="a-nameoperatorconstsidstara--csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::operator const SID *  
 轉換 （cast)`CSid`物件的指標`SID`（安全性識別碼） 結構。  
  
```  
operator const SID *() const throw(...);
```  
  
### <a name="remarks"></a>備註  
 傳回的位址`SID`結構。  
  
##  <a name="a-namesida--csidsid"></a><a name="sid"></a>CSid::Sid  
 傳回`SID`（安全性識別碼） 做為字串的結構。  
  
```
LPCTSTR Sid() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 傳回`SID`以字串形式適用於顯示、 儲存或傳輸的格式結構。 相當於[ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399)雖然此函數僅適用於 Windows 2000 或更新版本，因此模擬舊版作業系統。  
  
##  <a name="a-namesidnameusea--csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse  
 傳回的狀態描述`CSid`物件。  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，描述的狀態會儲存的資料成員值`CSid`物件。  
  
|值|描述|  
|-----------|-----------------|  
|SidTypeUser|表示使用者`SID`（安全性識別碼）。|  
|SidTypeGroup|表示一組`SID`。|  
|SidTypeDomain|表示網域`SID`。|  
|SidTypeAlias|指出別名`SID`。|  
|SidTypeWellKnownGroup|指出`SID`知名的群組。|  
|SidTypeDeletedAccount|表示`SID`已刪除的帳戶。|  
|SidTypeInvalid|表示無效`SID`。|  
|SidTypeUnknown|表示未知`SID`型別。|  
|SidTypeComputer|指出`SID`電腦。|  
  
### <a name="remarks"></a>備註  
 呼叫[CSid::LoadAccount](#loadaccount)更新`CSid`物件之前，先呼叫`SidNameUse`来傳回其狀態。 `SidNameUse`不會變更物件的狀態 (藉由呼叫至**LookupAccountName**或**LookupAccountSid**)，但只會傳回目前的狀態。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)   
 [運算子](../../atl/reference/atl-operators.md)

