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
ms.openlocfilehash: b6787c0e3f075935f19d51aa73bbd66da9cc0fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835593"
---
# <a name="csid-class"></a>CSid 類別

這個類別是 `SID` (安全識別碼) 結構的包裝函式。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
class CSid
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSid：： CSidArray](#csidarray)|`CSid` 物件的陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSid：： CSid](#csid)|建構函式。|
|[CSid：： ~ CSid](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSid：： AccountName](#accountname)|傳回與物件相關聯的帳戶名稱 `CSid` 。|
|[CSid：:D omain](#domain)|傳回與物件相關聯之網域的名稱 `CSid` 。|
|[CSid：： EqualPrefix](#equalprefix)|測試 `SID` (安全識別碼) 首碼是否相等。|
|[CSid：： GetLength](#getlength)|傳回物件的長度 `CSid` 。|
|[CSid：： GetPSID](#getpsid)|傳回結構的指標 `SID` 。|
|[CSid：： GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|傳回結構的指標 `SID_IDENTIFIER_AUTHORITY` 。|
|[CSid：： GetSubAuthority](#getsubauthority)|傳回結構中指定的 subauthority `SID` 。|
|[CSid：： GetSubAuthorityCount](#getsubauthoritycount)|傳回 subauthority 計數。|
|[CSid：： IsValid](#isvalid)|測試 `CSid` 物件的有效性。|
|[CSid：： LoadAccount](#loadaccount)|使用 `CSid` 指定的帳號名稱和網域，或現有的結構來更新物件 `SID` 。|
|[CSid：： Sid](#sid)|傳回識別碼字串。|
|[CSid：： SidNameUse](#sidnameuse)|傳回物件狀態的描述 `CSid` 。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#operator_eq)|指派運算子。|
|[operator const SID *](#operator_const_sid__star)|將 `CSid` 物件轉換為結構的指標 `SID` 。|

### <a name="global-operators"></a>全域運算子

|名稱|描述|
|-|-|
|[operator = =](#operator_eq_eq)|測試兩個安全描述項物件是否相等|
|[operator！ =](#operator_neq)|測試兩個安全描述項物件是否不相等|
|[運算元 \<](#operator_lt)|比較兩個安全描述項物件的相對值。|
|[運算子 >](#operator_gt)|比較兩個安全描述項物件的相對值。|
|[運算元 \<=](#operator_lt__eq)|比較兩個安全描述項物件的相對值。|
|[運算子 >=](#operator_gt__eq)|比較兩個安全描述項物件的相對值。|

## <a name="remarks"></a>備註

`SID`結構是用來唯一識別使用者或群組的可變長度結構。

應用程式不應該 `SID` 直接修改結構，而是改用這個包裝函式類別中提供的方法。 另請參閱 [AtlGetOwnerSid](security-global-functions.md#atlgetownersid)、 [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid)、 [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)和 [AtlSetOwnerSid](security-global-functions.md#atlsetownersid)。

如需 Windows 中存取控制模型的簡介，請參閱 Windows SDK 中的 [存取控制](/windows/win32/SecAuthZ/access-control) 。

## <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="csidaccountname"></a><a name="accountname"></a> CSid：： AccountName

傳回與物件相關聯的帳戶名稱 `CSid` 。

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回指向帳戶名稱的 LPCTSTR。

### <a name="remarks"></a>備註

這個方法會嘗試找出指定 `SID` (安全識別碼) 的名稱。 如需完整的詳細資訊，請參閱 [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到任何帳戶名稱，則會傳回 `SID` `AccountName` 空字串。 如果網路延遲會讓這個方法無法找到名稱，就會發生這種情況。 它也會發生于沒有對應帳戶名稱的安全識別碼，例如 `SID` 識別登入會話的。

## <a name="csidcsid"></a><a name="csid"></a> CSid：： CSid

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
現有的 `CSid` 物件或 `SID` (的安全識別碼) 結構。

*IdentifierAuthority*<br/>
授權單位。

*nSubAuthorityCount*<br/>
Subauthority 計數。

*pszAccountName*<br/>
帳戶名稱。

*pszSystem*<br/>
系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串為 Null，則會改用本機系統。

*pSid*<br/>
結構的指標 `SID` 。

### <a name="remarks"></a>備註

此函式會初始化 `CSid` 物件、將內部資料成員設定為 *SidTypeInvalid*，或從現有的 `CSid` 、 `SID` 或現有的帳戶複製設定。

如果初始化失敗，則此函式會擲回 [CAtlException 類別](../../atl/reference/catlexception-class.md)。

## <a name="csidcsid"></a><a name="dtor"></a> CSid：： ~ CSid

解構函式。

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>備註

此函式會釋放物件所取得的任何資源。

## <a name="csidcsidarray"></a><a name="csidarray"></a> CSid：： CSidArray

[CSid](../../atl/reference/csid-class.md)物件的陣列。

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>備註

這個 typedef 指定的陣列型別，可以用來從 ACL (存取控制清單) 抓取安全性識別碼。 請參閱 [CAcl：： GetAclEntries](../../atl/reference/cacl-class.md#getaclentries)。

## <a name="csiddomain"></a><a name="domain"></a> CSid：:D omain

傳回與物件相關聯之網域的名稱 `CSid` 。

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回 `LPCTSTR` 指向網域的。

### <a name="remarks"></a>備註

這個方法會嘗試找出指定 `SID` (安全識別碼) 的名稱。 如需完整的詳細資訊，請參閱 [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到任何帳戶名稱 `SID` ，則會 `Domain` 以空字串的形式傳回網域。 如果網路延遲會讓這個方法無法找到名稱，就會發生這種情況。 它也會發生于沒有對應帳戶名稱的安全識別碼，例如 `SID` 識別登入會話的。

## <a name="csidequalprefix"></a><a name="equalprefix"></a> CSid：： EqualPrefix

測試 `SID` (安全識別碼) 首碼是否相等。

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>參數

*rhs*<br/>
`SID` (的安全識別碼) 結構或 `CSid` 要比較的物件。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的 [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) 。

## <a name="csidgetlength"></a><a name="getlength"></a> CSid：： GetLength

傳回物件的長度 `CSid` 。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

傳回物件的長度（以位元組為單位） `CSid` 。

### <a name="remarks"></a>備註

如果 `CSid` 結構無效，則傳回值為未定義。 在呼叫之前 `GetLength` ，請使用 [CSid：： IsValid](#isvalid) 成員函式來確認 `CSid` 是否有效。

> [!NOTE]
> 在 debug 組建下，如果物件無效，函式將會導致判斷提示 `CSid` 。

## <a name="csidgetpsid"></a><a name="getpsid"></a> CSid：： GetPSID

傳回 `SID` (安全識別碼) 結構的指標。

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回 `CSid` 物件基礎結構的位址 `SID` 。

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a> CSid：： GetPSID_IDENTIFIER_AUTHORITY

傳回結構的指標 `SID_IDENTIFIER_AUTHORITY` 。

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回結構的位址 `SID_IDENTIFIER_AUTHORITY` 。 如果失敗，則傳回值為未定義。 如果物件無效，則可能會發生失敗 `CSid` ，在此情況下， [CSid：： IsValid](#isvalid) 方法會傳回 FALSE。 您 `GetLastError` 可以針對延伸的錯誤資訊呼叫函式。

> [!NOTE]
> 在 debug 組建下，如果物件無效，函式將會導致判斷提示 `CSid` 。

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a> CSid：： GetSubAuthority

傳回 `SID` (安全識別碼) 結構中指定的 subauthority。

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>參數

*nSubAuthority*<br/>
Subauthority。

### <a name="return-value"></a>傳回值

傳回 NSubAuthority 所參考的 subauthority *。* Subauthority 值是 (RID) 的相對識別碼。

### <a name="remarks"></a>備註

*NSubAuthority*參數會指定索引值，以識別方法將傳回的 subauthority 陣列元素。 方法不會對此值執行任何驗證測試。 應用程式可以呼叫 [CSid：： GetSubAuthorityCount](#getsubauthoritycount) 來探索可接受值的範圍。

> [!NOTE]
> 在 debug 組建下，如果物件無效，函式將會導致判斷提示 `CSid` 。

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a> CSid：： GetSubAuthorityCount

傳回 subauthority 計數。

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>傳回值

如果方法成功，傳回值就是 subauthority 計數。

如果方法失敗，傳回值會是未定義的。 如果物件無效，方法會失敗 `CSid` 。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

> [!NOTE]
> 在 debug 組建下，如果物件無效，函式將會導致判斷提示 `CSid` 。

## <a name="csidisvalid"></a><a name="isvalid"></a> CSid：： IsValid

測試 `CSid` 物件的有效性。

```
bool IsValid() const throw();
```

### <a name="return-value"></a>傳回值

如果 `CSid` 物件有效，則傳回 TRUE，否則傳回 FALSE。 此方法沒有任何延伸的錯誤資訊;請勿呼叫 `GetLastError` 。

### <a name="remarks"></a>備註

方法會驗證 `IsValid` 物件，方法是 `CSid` 確認修訂號碼在已知的範圍內，而且 subauthorities 的數目小於最大值。

## <a name="csidloadaccount"></a><a name="loadaccount"></a> CSid：： LoadAccount

使用 `CSid` 指定的帳號名稱和網域，或現有的 SID (安全識別碼) 結構來更新物件。

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
系統名稱。 這個字串可以是遠端電腦的名稱。 如果這個字串為 Null，則會改用本機系統。

*pSid*<br/>
[SID](/windows/win32/api/winnt/ns-winnt-sid)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

`LoadAccount` 嘗試尋找指定名稱的安全識別碼。 如需詳細資訊，請參閱 [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) 。

## <a name="csidoperator-"></a><a name="operator_eq"></a> CSid：： operator =

指派運算子。

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 指派給 `CSid` 物件。

### <a name="return-value"></a>傳回值

傳回已更新之物件的參考 `CSid` 。

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a> CSid：： operator = =

測試兩個安全描述項物件是否相等。

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在 = = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在 = = 運算子右邊。

### <a name="return-value"></a>傳回值

如果安全描述項相等則為 TRUE，否則為 FALSE。

## <a name="csidoperator-"></a><a name="operator_neq"></a> CSid：： operator！ =

測試兩個安全描述項物件是否不相等。

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子右邊。

### <a name="return-value"></a>傳回值

如果安全描述項不相等，則為 TRUE，否則為 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt"></a> CSid：： operator &lt;

比較兩個安全描述項物件的相對值。

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子右邊。

### <a name="return-value"></a>傳回值

如果 *lhs* 小於 *rhs*，則為 TRUE，否則為 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a> CSid：： operator &lt;=

比較兩個安全描述項物件的相對值。

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子右邊。

### <a name="return-value"></a>傳回值

如果 *lhs* 小於或等於 *rhs*，則為 TRUE，否則為 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt"></a> CSid：： operator &gt;

比較兩個安全描述項物件的相對值。

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子右邊。

### <a name="return-value"></a>傳回值

如果 *lhs* 大於 *rhs*，則為 TRUE，否則為 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a> CSid：： operator &gt;=

比較兩個安全描述項物件的相對值。

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>參數

*lhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子的左邊。

*rhs*<br/>
`SID` (的安全識別碼) 或 `CSid` 出現在！ = 運算子右邊。

### <a name="return-value"></a>傳回值

如果 *lhs* 大於或等於 *rhs*，則為 TRUE，否則為 FALSE。

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a> CSid：： operator const SID \*

將物件轉換為 `CSid` `SID` (安全識別碼) 結構的指標。

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>備註

傳回結構的位址 `SID` 。

## <a name="csidsid"></a><a name="sid"></a> CSid：： Sid

`SID`以字串形式傳回 (的安全識別碼) 結構。

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>傳回值

以 `SID` 適合顯示、儲存或傳輸的格式，傳回結構作為字串。 相當於 [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw)。

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a> CSid：： SidNameUse

傳回物件狀態的描述 `CSid` 。

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>傳回值

傳回資料成員的值，此值會儲存描述物件狀態的值 `CSid` 。

|值|描述|
|-----------|-----------------|
|SidTypeUser|指出使用者 `SID` (的安全識別碼) 。|
|SidTypeGroup|指出群組 `SID` 。|
|SidTypeDomain|表示網域 `SID` 。|
|SidTypeAlias|表示別名 `SID` 。|
|SidTypeWellKnownGroup|指出 `SID` 已知群組的。|
|SidTypeDeletedAccount|表示 `SID` 已刪除之帳戶的。|
|SidTypeInvalid|指出不正確 `SID` 。|
|SidTypeUnknown|表示未知的 `SID` 類型。|
|SidTypeComputer|指出 `SID` 電腦的。|

### <a name="remarks"></a>備註

呼叫 [CSid：： LoadAccount](#loadaccount) 以更新 `CSid` 物件，然後呼叫 `SidNameUse` 以傳回其狀態。 `SidNameUse` 不會藉由呼叫或) 來變更物件 (的 `LookupAccountName` 狀態 `LookupAccountSid` ，但是只會傳回目前的狀態。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)<br/>
[運算子](../../atl/reference/atl-operators.md)
