---
title: CSid 類別
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: ed19ed3cdeb77612e20d826480ab73b9361366e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496443"
---
# <a name="csid-class"></a>CSid 類別

這個類別是`SID` (安全識別碼) 結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSid
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|`CSid` 物件的陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSid::CSid](#csid)|建構函式。|
|[CSid::~CSid](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSid::AccountName](#accountname)|傳回與`CSid`物件相關聯之帳戶的名稱。|
|[CSid::Domain](#domain)|傳回與`CSid`物件相關聯之網域的名稱。|
|[CSid::EqualPrefix](#equalprefix)|相等`SID`的測試 (安全識別碼) 首碼。|
|[CSid::GetLength](#getlength)|傳回`CSid`物件的長度。|
|[CSid::GetPSID](#getpsid)|傳回`SID`結構的指標。|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|傳回結構的`SID_IDENTIFIER_AUTHORITY`指標。|
|[CSid::GetSubAuthority](#getsubauthority)|傳回`SID`結構中的指定 subauthority。|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|傳回 subauthority 計數。|
|[CSid::IsValid](#isvalid)|`CSid`測試物件的有效性。|
|[CSid::LoadAccount](#loadaccount)|根據指定的帳號名稱和網域, 或現有`SID`的結構來更新物件。`CSid`|
|[CSid::Sid](#sid)|傳回識別碼字串。|
|[CSid::SidNameUse](#sidnameuse)|傳回`CSid`物件狀態的描述。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator_eq)|指派運算子。|
|[operator const SID *](#operator_const_sid__star)|將物件轉換成`SID`結構的指標。 `CSid`|

### <a name="global-operators"></a>全域運算子

|||
|-|-|
|[operator ==](#operator_eq_eq)|測試兩個安全描述項物件是否相等|
|[operator !=](#operator_neq)|測試兩個安全描述項物件是否不相等|
|[操作\<](#operator_lt)|比較兩個安全描述項物件的相對值。|
|[operator >](#operator_gt)|比較兩個安全描述項物件的相對值。|
|[操作\<=](#operator_lt__eq)|比較兩個安全描述項物件的相對值。|
|[operator >=](#operator_gt__eq)|比較兩個安全描述項物件的相對值。|

## <a name="remarks"></a>備註

`SID`結構是用來唯一識別使用者或群組的可變長度結構。

應用程式不應直接`SID`修改結構, 而是使用此包裝函式類別中提供的方法。 另請參閱[AtlGetOwnerSid](security-global-functions.md#atlgetownersid)、 [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid)、 [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)和[AtlSetOwnerSid](security-global-functions.md#atlsetownersid)。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="accountname"></a>  CSid::AccountName

傳回與`CSid`物件相關聯之帳戶的名稱。

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回指向帳戶名稱的 LPCTSTR。

### <a name="remarks"></a>備註

這個方法會嘗試尋找指定`SID` (安全識別碼) 的名稱。 如需完整詳細資料, 請參閱[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到的帳戶`SID`名稱, `AccountName`則會傳回空字串。 如果網路延遲阻止此方法尋找名稱, 就會發生這種情況。 不含對應帳戶名稱的安全識別碼 (例如`SID`識別登入會話的) 也會發生此錯誤。

##  <a name="csid"></a>  CSid::CSid

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

*rhs*<br/>
現有`CSid`的物件或`SID` (安全識別碼) 結構。

*IdentifierAuthority*<br/>
授權單位。

*nSubAuthorityCount*<br/>
Subauthority 計數。

*pszAccountName*<br/>
帳戶名稱。

*pszSystem*<br/>
系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串是 Null, 則會改用本機系統。

*pSid*<br/>
`SID`結構的指標。

### <a name="remarks"></a>備註

此函式會`CSid`初始化物件、將內部資料成員設定為*SidTypeInvalid*, 或從現有`CSid`的、或現有的`SID`帳戶複製設定。

如果初始化失敗, 則此函式會擲回[CAtlException 類別](../../atl/reference/catlexception-class.md)。

##  <a name="dtor"></a>  CSid::~CSid

解構函式。

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放物件所取得的任何資源。

##  <a name="csidarray"></a>  CSid::CSidArray

[CSid](../../atl/reference/csid-class.md)物件的陣列。

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>備註

這個 typedef 會指定可用來從 ACL (存取控制清單) 抓取安全識別碼的陣列類型。 請參閱[CAcl:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。

##  <a name="domain"></a>CSid::D omain

傳回與`CSid`物件相關聯之網域的名稱。

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回指向`LPCTSTR`網域的。

### <a name="remarks"></a>備註

這個方法會嘗試尋找指定`SID` (安全識別碼) 的名稱。 如需完整詳細資料, 請參閱[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到的`SID`帳戶名稱, `Domain`則會傳回網域做為空字串。 如果網路延遲阻止此方法尋找名稱, 就會發生這種情況。 不含對應帳戶名稱的安全識別碼 (例如`SID`識別登入會話的) 也會發生此錯誤。

##  <a name="equalprefix"></a>  CSid::EqualPrefix

相等`SID`的測試 (安全識別碼) 首碼。

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`SID`比較的 (安全識別碼) `CSid`結構或物件。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) 。

##  <a name="getlength"></a>  CSid::GetLength

傳回`CSid`物件的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CSid`物件的長度 (以位元組為單位)。

### <a name="remarks"></a>備註

`CSid`如果結構無效, 則傳回值為未定義。 在呼叫`GetLength`之前, 請使用[CSid:: IsValid](#isvalid)成員函式來`CSid`確認是否有效。

> [!NOTE]
>  在 debug build 底下, 如果`CSid`物件無效, 函式會造成判斷提示。

##  <a name="getpsid"></a>  CSid::GetPSID

傳回`SID` (安全識別碼) 結構的指標。

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回`CSid`物件基礎`SID`結構的位址。

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

傳回結構的`SID_IDENTIFIER_AUTHORITY`指標。

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>傳回值

如果方法成功, 它會傳回`SID_IDENTIFIER_AUTHORITY`結構的位址。 如果失敗, 則傳回值為未定義。 如果`CSid`物件無效, 則可能會發生失敗, 在此情況下, [CSid:: IsValid](#isvalid)方法會傳回 FALSE。 可以針對`GetLastError`擴充的錯誤資訊呼叫函數。

> [!NOTE]
>  在 debug build 底下, 如果`CSid`物件無效, 函式會造成判斷提示。

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

傳回`SID` (安全識別碼) 結構中的指定 subauthority。

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>參數

*nSubAuthority*<br/>
Subauthority。

### <a name="return-value"></a>傳回值

傳回 NSubAuthority 所參考的 subauthority *。* Subauthority 值是相對識別碼 (RID)。

### <a name="remarks"></a>備註

*NSubAuthority*參數會指定索引值, 以識別方法將傳回的 subauthority 陣列元素。 此方法不會對此值執行任何驗證測試。 應用程式可以呼叫[CSid:: GetSubAuthorityCount](#getsubauthoritycount)來探索可接受值的範圍。

> [!NOTE]
>  在 debug build 底下, 如果`CSid`物件無效, 函式會造成判斷提示。

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

傳回 subauthority 計數。

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回值為 subauthority 計數。

如果方法失敗, 則傳回值為未定義。 如果`CSid`物件無效, 方法會失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

> [!NOTE]
>  在 debug build 底下, 如果`CSid`物件無效, 函式會造成判斷提示。

##  <a name="isvalid"></a>  CSid::IsValid

`CSid`測試物件的有效性。

```
bool IsValid() const throw();
```

### <a name="return-value"></a>傳回值

如果`CSid`物件有效, 則傳回 TRUE, 否則傳回 FALSE。 這個方法沒有任何擴充的錯誤資訊;請勿呼叫`GetLastError`。

### <a name="remarks"></a>備註

`IsValid` 方法`CSid`驗證物件的方式是確認修訂編號在已知的範圍內, 而且 subauthorities 的數目小於最大值。

##  <a name="loadaccount"></a>CSid:: LoadAccount

根據指定的帳號名稱和網域, 或現有的 SID (安全識別碼) 結構, 更新物件。`CSid`

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>參數

*pszAccountName*<br/>
帳戶名稱。

*pszSystem*<br/>
系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串是 Null, 則會改用本機系統。

*pSid*<br/>
[SID](/windows/win32/api/winnt/ns-winnt-sid)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE, 失敗時傳回 FALSE。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

`LoadAccount`嘗試尋找指定名稱的安全識別碼。 如需詳細資訊, 請參閱[LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) 。

##  <a name="operator_eq"></a>CSid:: operator =

指派運算子。

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
(安全識別碼), 或`CSid`指派`CSid`給物件。 `SID`

### <a name="return-value"></a>傳回值

傳回已更新`CSid`物件的參考。

##  <a name="operator_eq_eq"></a>CSid:: operator = =

測試兩個安全描述項物件是否相等。

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
(安全識別碼), 或`CSid`出現在 = = 運算子的左邊。 `SID`

*rhs*<br/>
(安全識別碼), 或`CSid`出現在 = = 運算子右邊的。 `SID`

### <a name="return-value"></a>傳回值

如果安全描述項相等, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_neq"></a>CSid:: operator! =

測試兩個安全描述項物件是否不相等。

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
出現在! = 運算子左邊`CSid`的(安全識別碼)或。`SID`

*rhs*<br/>
出現在! = 運算子右邊`CSid`的(安全識別碼)。`SID`

### <a name="return-value"></a>傳回值

如果安全描述項不相等, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_lt"></a>CSid:: operator&lt;

比較兩個安全描述項物件的相對值。

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
出現在! = 運算子左邊`CSid`的(安全識別碼)或。`SID`

*rhs*<br/>
出現在! = 運算子右邊`CSid`的(安全識別碼)。`SID`

### <a name="return-value"></a>傳回值

如果*lhs*小於*rhs*, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_lt__eq"></a>CSid:: operator&lt;=

比較兩個安全描述項物件的相對值。

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
出現在! = 運算子左邊`CSid`的(安全識別碼)或。`SID`

*rhs*<br/>
出現在! = 運算子右邊`CSid`的(安全識別碼)。`SID`

### <a name="return-value"></a>傳回值

如果*lhs*小於或等於*rhs*, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_gt"></a>CSid:: operator&gt;

比較兩個安全描述項物件的相對值。

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
出現在! = 運算子左邊`CSid`的(安全識別碼)或。`SID`

*rhs*<br/>
出現在! = 運算子右邊`CSid`的(安全識別碼)。`SID`

### <a name="return-value"></a>傳回值

如果*lhs*大於*rhs*, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_gt__eq"></a>CSid:: operator&gt;=

比較兩個安全描述項物件的相對值。

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>參數

*lhs*<br/>
出現在! = 運算子左邊`CSid`的(安全識別碼)或。`SID`

*rhs*<br/>
出現在! = 運算子右邊`CSid`的(安全識別碼)。`SID`

### <a name="return-value"></a>傳回值

如果*lhs*大於或等於*rhs*, 則為 TRUE, 否則為 FALSE。

##  <a name="operator_const_sid__star"></a>CSid:: operator const SID\*

將物件轉換成`SID` (安全識別碼) 結構的指標。 `CSid`

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>備註

傳回`SID`結構的位址。

##  <a name="sid"></a>  CSid::Sid

以字串形式傳回(安全識別碼)結構。`SID`

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>傳回值

以適用于顯示、儲存或傳輸的格式, 傳回結構做為字串。`SID` 相當於[ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw)。

##  <a name="sidnameuse"></a>CSid:: SidNameUse

傳回`CSid`物件狀態的描述。

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>傳回值

傳回資料成員的值, 該值會儲存描述`CSid`物件狀態的值。

|值|描述|
|-----------|-----------------|
|SidTypeUser|表示使用者`SID` (安全識別碼)。|
|SidTypeGroup|表示群組`SID`。|
|SidTypeDomain|表示網域`SID`。|
|SidTypeAlias|表示別名`SID`。|
|SidTypeWellKnownGroup|`SID`表示適用于已知群組的。|
|SidTypeDeletedAccount|`SID`表示已刪除之帳戶的。|
|SidTypeInvalid|表示無效`SID`的。|
|SidTypeUnknown|表示未知`SID`的類型。|
|SidTypeComputer|`SID`表示電腦的。|

### <a name="remarks"></a>備註

呼叫[CSid:: LoadAccount](#loadaccount)來更新`CSid`物件, 然後再`SidNameUse`呼叫以傳回其狀態。 `SidNameUse`不會變更物件的狀態 (藉由呼叫`LookupAccountName`或`LookupAccountSid`), 而只會傳回目前的狀態。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)<br/>
[運算子](../../atl/reference/atl-operators.md)
