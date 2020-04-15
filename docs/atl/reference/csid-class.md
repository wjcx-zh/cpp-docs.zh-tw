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
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330914"
---
# <a name="csid-class"></a>CSid 類別

此類是`SID`(安全標識符)結構的包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSid
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSid:CSidArray](#csidarray)|`CSid` 物件的陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSid:CSid](#csid)|建構函式。|
|[CSid:_CSid](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSid::帳戶名稱](#accountname)|返回與`CSid`物件關聯的帳戶的名稱。|
|[CSid::D奧曼](#domain)|返回與`CSid`物件關聯的域的名稱。|
|[CSid:等於前置碼](#equalprefix)|相等`SID`性測試(安全標識符)首碼。|
|[CSid:取得長度](#getlength)|返回`CSid`物件的長度。|
|[CSid:GetPSID](#getpsid)|返回指向結構的`SID`指標。|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|返回指向結構的`SID_IDENTIFIER_AUTHORITY`指標。|
|[CSid:抓取子授權](#getsubauthority)|傳回結構中的指定子頒發`SID`機構 。|
|[CSid:抓取子授權計數](#getsubauthoritycount)|返回子頒發機構計數。|
|[CSid:有效](#isvalid)|測試`CSid`物件的有效性。|
|[CSid::載入帳戶](#loadaccount)|更新給定`CSid`帳戶名稱和域或現有`SID`結構的物件。|
|[CSid:*Ssid](#sid)|返回 ID 字串。|
|[CSid::SidNameUse](#sidnameuse)|返回`CSid`物件狀態的說明。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算符 |](#operator_eq)|指派運算子。|
|[操作員 CONst SID |](#operator_const_sid__star)|將`CSid`物件轉換為指向結構`SID`的指標。|

### <a name="global-operators"></a>全球運營商

|||
|-|-|
|[運算符 |](#operator_eq_eq)|測試兩個安全性描述子物件是否相等|
|[操作員 !]](#operator_neq)|測試兩個安全性描述子物件是否不等式|
|[算子\<](#operator_lt)|比較兩個安全描述符對象的相對值。|
|[運算子>](#operator_gt)|比較兩個安全描述符對象的相對值。|
|[算子\<=](#operator_lt__eq)|比較兩個安全描述符對象的相對值。|
|[操作員>|](#operator_gt__eq)|比較兩個安全描述符對象的相對值。|

## <a name="remarks"></a>備註

結構`SID`是一種可變長度結構,用於唯一標識使用者或組。

應用程式不應直接修改`SID`結構,而應使用此包裝類中提供的方法。 另見[AtlGetOwnerSid](security-global-functions.md#atlgetownersid)AtlGetOwnerSid,AtlSetGroupSid,AtlGetGroupSid,和[AtlSetOwnerSid。](security-global-functions.md#atlsetownersid) [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid) [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::帳戶名稱

返回與`CSid`物件關聯的帳戶的名稱。

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>傳回值

返回指向帳戶名稱的 LPCTSTR。

### <a name="remarks"></a>備註

此方法嘗試查找指定`SID`的名稱(安全標識符)。 有關詳細資訊,請參閱[查找帳戶 Sid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到`SID`的 帳戶名稱,`AccountName`則傳回一個空字串。 如果網路超時阻止此方法查找名稱,則可能發生此情況。 對於沒有相應帳戶名稱的安全標識符(如標識登錄會話`SID`的安全標識符)也會發生這種情況。

## <a name="csidcsid"></a><a name="csid"></a>CSid:CSid

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
現有`CSid`物件`SID`或 (安全標識符)結構。

*識別符頒發機構*<br/>
權威。

*nSubAuthority( S) Count*<br/>
子頒發機構計數。

*psz帳號名稱*<br/>
帳戶名稱。

*psz系統*<br/>
系統名稱。 此字串可以是遠端電腦的名稱。 如果此字串為 NULL,則改為使用本機系統。

*pSid*<br/>
指向結構的`SID`指標。

### <a name="remarks"></a>備註

`CSid`建構函數初始化物件,將內部資料成員設置為*SidTypeInvalid,* 或透過`CSid`從現有`SID`、或現有帳戶複製設置。

如果初始化失敗,建構函數將引發[CAtlException 類別](../../atl/reference/catlexception-class.md)。

## <a name="csidcsid"></a><a name="dtor"></a>CSid:_CSid

解構函式。

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>備註

析構函數釋放對象獲取的任何資源。

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid:CSidArray

[CSid](../../atl/reference/csid-class.md)物件的陣列。

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>備註

此 typedef 指定可用於從 ACL(存取控制列表)檢索安全識別符的陣列類型。 請參考[CAcl:取得 Acl 項目](../../atl/reference/cacl-class.md#getaclentries)。

## <a name="csiddomain"></a><a name="domain"></a>CSid::D奧曼

返回與`CSid`物件關聯的域的名稱。

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>傳回值

返回指向`LPCTSTR`域的指標。

### <a name="remarks"></a>備註

此方法嘗試查找指定`SID`的名稱(安全標識符)。 有關詳細資訊,請參閱[查找帳戶 Sid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)。

如果找不到的`SID`帳號名稱,`Domain`則將域作為空字串返回。 如果網路超時阻止此方法查找名稱,則可能發生此情況。 對於沒有相應帳戶名稱的安全標識符(如標識登錄會話`SID`的安全標識符)也會發生這種情況。

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid:等於前置碼

相等`SID`性測試(安全標識符)首碼。

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`SID`比較的(安全標識符)`CSid`結構或物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EqualPrefixSid。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid)

## <a name="csidgetlength"></a><a name="getlength"></a>CSid:取得長度

返回`CSid`物件的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

返回`CSid`物件的長度(以位元組為單位)。

### <a name="remarks"></a>備註

如果`CSid`結構無效,則返回值未定義。 在調用`GetLength`之前,使用[CSid::IsValid](#isvalid)成員`CSid`函數來 驗證該函數是否有效。

> [!NOTE]
> 在除錯產生下,如果物件無效,`CSid`該函數將導致 ASSERT。

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid:GetPSID

返回指向(安全標識符`SID`)結構的指標。

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>傳回值

傳`CSid`回 物件`SID`的基礎結構的位址。

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

返回指向結構的`SID_IDENTIFIER_AUTHORITY`指標。

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>傳回值

如果該方法成功,它將傳回結構的`SID_IDENTIFIER_AUTHORITY`位址 。 如果失敗,則返回值未定義。 如果物件無效,`CSid`則可能發生失敗,在這種情況下[,CSid::isValid](#isvalid)方法將返回 FALSE。 可以調用`GetLastError`該函數以提供擴展的錯誤資訊。

> [!NOTE]
> 在除錯產生下,如果物件無效,`CSid`該函數將導致 ASSERT。

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid:抓取子授權

返回`SID`(安全標識)結構中的指定子頒發機構。

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>參數

*nSubAuthority*<br/>
子頒發機構。

### <a name="return-value"></a>傳回值

返回*nSubAuthority*引用的子頒發機構。 子頒發者值是相對識別符 (RID)。

### <a name="remarks"></a>備註

*nSubAuthority*參數指定一個索引值,用於標識方法將返回的子權威陣列元素。 該方法不執行此值的驗證測試。 應用程式可以調用[CSid::獲取 SubAuthorityCount 以](#getsubauthoritycount)發現可接受的值的範圍。

> [!NOTE]
> 在除錯產生下,如果物件無效,`CSid`該函數將導致 ASSERT。

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid:抓取子授權計數

返回子頒發機構計數。

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>傳回值

如果該方法成功,則返回值為子頒發機構計數。

如果方法失敗,則返回值未定義。 如果物件無效,`CSid`該方法將失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

> [!NOTE]
> 在除錯產生下,如果物件無效,`CSid`該函數將導致 ASSERT。

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid:有效

測試`CSid`物件的有效性。

```
bool IsValid() const throw();
```

### <a name="return-value"></a>傳回值

如果物件有效,`CSid`則傳回 TRUE,如果無效,則傳回 FALSE。 此方法沒有擴展的錯誤資訊;因此,此方法沒有擴展錯誤資訊。不呼叫`GetLastError`。

### <a name="remarks"></a>備註

該方法`IsValid`通過驗證修訂編`CSid`號 是否在已知範圍內以及子許可權數小於最大值來驗證物件。

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::載入帳戶

更新給定`CSid`帳戶名稱和域或現有 SID(安全識別符)結構的物件。

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>參數

*psz帳號名稱*<br/>
帳戶名稱。

*psz系統*<br/>
系統名稱。 此字串可以是遠端電腦的名稱。 如果此字串為 NULL,則改為使用本機系統。

*pSid*<br/>
指向[SID](/windows/win32/api/winnt/ns-winnt-sid)結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

`LoadAccount`嘗試尋找指定名稱的安全識別碼。 有關詳細資訊[,請參閱查找帳戶Sid。](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::運算符 |

指派運算子。

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`SID` (安全標識符)或`CSid`要分配`CSid`給 物件。

### <a name="return-value"></a>傳回值

返回對更新`CSid`物件的引用。

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::運算符 |

測試兩個安全描述符物件是否相等。

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
或`SID`顯示在 _`CSid`運算符 左側的(安全識別碼)。

*rhs*<br/>
(`SID`安全識別碼`CSid`) 或 顯示在 _ 運算符右側的。。

### <a name="return-value"></a>傳回值

如果安全描述符相等,則為 TRUE,否則為 FALSE。

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::操作員!*

測試兩個安全描述符物件是否不平等。

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
(`SID`安全識別碼)`CSid`或 顯示在 !+ 運算符左側的。。

*rhs*<br/>
(`SID`安全識別子)`CSid`或 顯示在 !# 運算符右側的。。

### <a name="return-value"></a>傳回值

如果安全描述符不相等,則為 TRUE,否則為 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::運算子&lt;

比較兩個安全描述符對象的相對值。

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
(`SID`安全識別碼)`CSid`或 顯示在 !+ 運算符左側的。。

*rhs*<br/>
(`SID`安全識別子)`CSid`或 顯示在 !# 運算符右側的。。

### <a name="return-value"></a>傳回值

如果*lhs*小於*rhs,* 則為 TRUE,否則為 FALSE。

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::運算子&lt;=

比較兩個安全描述符對象的相對值。

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
(`SID`安全識別碼)`CSid`或 顯示在 !+ 運算符左側的。。

*rhs*<br/>
(`SID`安全識別子)`CSid`或 顯示在 !# 運算符右側的。。

### <a name="return-value"></a>傳回值

如果*lhs*小於或等於*rhs,* 則為 TRUE,否則為 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::運算子&gt;

比較兩個安全描述符對象的相對值。

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
(`SID`安全識別碼)`CSid`或 顯示在 !+ 運算符左側的。。

*rhs*<br/>
(`SID`安全識別子)`CSid`或 顯示在 !# 運算符右側的。。

### <a name="return-value"></a>傳回值

如果*lhs*大於*rhs,* 則為 TRUE,否則為 FALSE。

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::運算子&gt;=

比較兩個安全描述符對象的相對值。

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>參數

*lhs*<br/>
(`SID`安全識別碼)`CSid`或 顯示在 !+ 運算符左側的。。

*rhs*<br/>
(`SID`安全識別子)`CSid`或 顯示在 !# 運算符右側的。。

### <a name="return-value"></a>傳回值

如果*lhs*大於或等於*rhs,* 則為 TRUE,否則為 FALSE。

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::操作員同心SID\*

將`CSid`物件強制轉換為指向(安全標識符`SID`) 結構的指標。

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>備註

傳回結構的`SID`位址 。

## <a name="csidsid"></a><a name="sid"></a>CSid:*Ssid

將`SID`(安全標識)結構作為字串返回。

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>傳回值

以適合`SID`顯示、儲存或傳輸的格式將結構作為字串返回。 等效於[轉換 SidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw)。

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse

返回`CSid`物件狀態的說明。

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>傳回值

返回存儲描述`CSid`物件狀態的值的數據成員的值。

|值|描述|
|-----------|-----------------|
|西德類型使用者|指示使用者`SID`(安全標識)。|
|西德類型集團|指示群組`SID`。|
|西德域|指示網`SID`域 。|
|西德里亞斯|指示別名`SID`。|
|西德迪韋爾·韋爾認識集團|指示已知`SID`群組的 的 。|
|SidType 刪除帳戶|指示已`SID`刪除帳號的 。|
|SidType 無效|指示不`SID`合法 。|
|西德類型未知|指示未知`SID`類型。|
|西德類型電腦|指示`SID`電腦的 a。|

### <a name="remarks"></a>備註

呼叫[CSid::LoadAccount](#loadaccount)`CSid`在`SidNameUse`呼叫 以返回其狀態之前更新物件。 `SidNameUse`不更改物件的狀態(通過調用`LookupAccountName``LookupAccountSid`或 ),但僅返回當前狀態。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)<br/>
[操作員](../../atl/reference/atl-operators.md)
