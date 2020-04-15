---
title: CSecurityDesc 類別
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330966"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 類別

此類是結構的`SECURITY_DESCRIPTOR`包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSecurityDesc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc:CSecurityDesc](#csecuritydesc)|建構函式。|
|[CSecurityDesc:*CSecurityDesc](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc:從弦](#fromstring)|將字串格式的安全描述符轉換為有效的功能安全描述符。|
|[CSecurityDesc:取得控制](#getcontrol)|從安全描述符檢索控制資訊。|
|[CSecurityDesc:getDacl](#getdacl)|從安全描述符檢索可自由存取控制列表 (DACL) 資訊。|
|[CSecurityDesc:取得群組](#getgroup)|從安全描述符檢索主組資訊。|
|[CSecurityDesc:取得擁有者](#getowner)|從安全描述符檢索擁有者資訊。|
|[CSecurityDesc:GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|返回指向結構的`SECURITY_DESCRIPTOR`指標。|
|[CSecurityDesc:取得Sacl](#getsacl)|從安全描述符檢索系統存取控制列表 (SACL) 資訊。|
|[CSecurityDesc:isDacl自動繼承](#isdaclautoinherited)|確定是否將 DACL 配置為支援自動傳播。|
|[CSecurityDesc:isdacl已拖欠](#isdacldefaulted)|確定安全描述符是否配置了預設 DACL。|
|[CSecurityDesc:IsDacl存在](#isdaclpresent)|確定安全描述符是否包含 DACL。|
|[CSecurityDesc:IsDacl保護](#isdaclprotected)|確定是否配置了 DACL 以防止修改。|
|[CSecurityDesc:是集團違約](#isgroupdefaulted)|確定預設情況下是否設置了安全描述符的組安全識別碼 (SID)。|
|[CSecurityDesc:是擁有者違約](#isownerdefaulted)|確定預設情況下是否設置了安全描述符的所有者 SID。|
|[CSecurityDesc:issacl自動繼承](#issaclautoinherited)|確定是否將 SACL 配置為支援自動傳播。|
|[安全::已違約](#issacldefaulted)|確定安全描述符是否配置了預設 SACL。|
|[安全::Issacl存在](#issaclpresent)|確定安全描述符是否包含 SACL。|
|[安全::Issacl保護](#issaclprotected)|確定是否配置了 SACL 以防止修改。|
|[CSecurityDesc:是自我相對的](#isselfrelative)|確定安全性是否採用自相對格式。|
|[CSecurityDesc:使絕對](#makeabsolute)|呼叫此方法可將安全描述符轉換為絕對格式。|
|[CSecurityDesc:使自我相關](#makeselfrelative)|呼叫此方法可將安全描述符轉換為自相關格式。|
|[CSecurityDesc:設定控制](#setcontrol)|設定安全性描述元的控制位元。|
|[CSecurityDesc:SetDacl](#setdacl)|在 DACL 中設置資訊。 如果安全描述符中已存在 DACL,則替換它。|
|[CSecurityDesc:setGroup](#setgroup)|設定絕對格式安全描述符的主組資訊,替換已存在的任何主組資訊。|
|[CSecurityDesc::SetOwner](#setowner)|設置絕對格式安全描述符的所有者資訊,替換已存在的任何擁有者資訊。|
|[安全::SetSacl](#setsacl)|在 SACL 中設置資訊。 如果安全描述符中已存在SACL,則替換它。|
|[安全::到弦](#tostring)|將安全描述符轉換為字串格式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc::操作員SECURITY_DESCRIPTOR |](#operator_const_security_descriptor__star)|返回指向結構的`SECURITY_DESCRIPTOR`指標。|
|[CSecurityDesc::操作員 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

結構`SECURITY_DESCRIPTOR`包含與對象關聯的安全資訊。 應用程式使用此結構來設置和查詢物件的安全狀態。 另請參閱[AtlGet 安全性描述器](security-global-functions.md#atlgetsecuritydescriptor)。

應用程式不應直接修改`SECURITY_DESCRIPTOR`結構,而應使用提供的類方法。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc:CSecurityDesc

建構函式。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CSecurityDesc`分配給新`SECURITY_DESCRIPTOR``CSecurityDesc`物件的物件或結構。

### <a name="remarks"></a>備註

可以選擇`CSecurityDesc``SECURITY_DESCRIPTOR`使用結構或以前`CSecurityDesc`定義的物件創建該物件。

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc:*CSecurityDesc

解構函式。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>備註

析構函數釋放所有分配的資源。

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc:從弦

將字串格式的安全描述符轉換為有效的功能安全描述符。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>參數

*普斯特*<br/>
包含要轉換的[字串格式安全描述符](/windows/win32/SecAuthZ/security-descriptor-string-format)的 null 的字串的指標。

### <a name="return-value"></a>傳回值

成功時返回 true。 在發生故障時引發異常。

### <a name="remarks"></a>備註

可以使用[CSecurityDesc::toString](#tostring)創建字串。 將安全描述符轉換為字串可以更輕鬆地儲存和傳輸。

此方法調用[ConvertString 安全性描述](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)符。

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc:取得控制

從安全描述符檢索控制資訊。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>參數

*psdc*<br/>
指向接收安全`SECURITY_DESCRIPTOR_CONTROL`描述符控制資訊的結構的指標。

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,如果失敗,則為 false。

### <a name="remarks"></a>備註

此方法呼叫[取得安全性描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)。

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc:getDacl

從安全描述符檢索可自由存取控制列表 (DACL) 資訊。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
指向用於存儲`CDacl`安全描述符 DACL 副本的結構的指標。 如果存在可自由裁量 ACL,該方法將*pDacl*設置到安全描述符的可自由 ACL 位址。 如果不存在可自由裁量 ACL,則不存儲任何值。

*pb存在*<br/>
指向指示指定安全描述符中存在可自由裁量 ACL 的值的指標。 如果安全描述符包含可自由定義的 ACL,則此參數設置為 true。 如果安全描述符不包含可自由定義的 ACL,則此參數設置為 false。

*pbdefault*<br/>
如果安全描述符存在可自由 ACL,則`SECURITY_DESCRIPTOR_CONTROL`指向 結構中SE_DACL_DEFAULTED標誌的值的標誌。 如果此標誌為 true,則默認機制檢索可自由支配的 ACL;如果此標誌為 true,則為"可自由支配的 ACL"。"為 true。如果為 false,則使用者顯式指定可自由支配的 ACL。

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,如果失敗,則為 false。

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc:取得群組

從安全描述符檢索主組資訊。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向接收儲存在 CDacl 中的組副本的[CSid(](../../atl/reference/csid-class.md)安全識別符)的指標。

*pbdefault*<br/>
當方法返回時,指向標記的指標設置為`SECURITY_DESCRIPTOR_CONTROL`結構中SE_GROUP_DEFAULTED標誌的值。

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,如果失敗,則為 false。

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc:取得擁有者

從安全描述符檢索擁有者資訊。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向接收儲存在 CDacl 中的組副本的[CSid(](../../atl/reference/csid-class.md)安全識別符)的指標。

*pbdefault*<br/>
當方法返回時,指向標記的指標設置為`SECURITY_DESCRIPTOR_CONTROL`結構中SE_OWNER_DEFAULTED標誌的值。

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,如果失敗,則為 false。

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc:GetPSECURITY_DESCRIPTOR

返回指向結構的`SECURITY_DESCRIPTOR`指標。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>傳回值

返回指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)結構的指標。

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc:取得Sacl

從安全描述符檢索系統存取控制列表 (SACL) 資訊。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSacl*<br/>
指向用於存儲`CSacl`安全描述符 SACL 副本的結構的指標。 如果存在系統 ACL,該方法將*pSacl*設置到安全描述符的系統 ACL 的位址。 如果系統 ACL 不存在,則不存儲任何值。

*pb存在*<br/>
指向方法集的標誌的指標,以指示指定安全描述符中是否存在系統 ACL。 如果安全描述符包含系統 ACL,則此參數設置為 true。 如果安全描述符不包含系統 ACL,則此參數設置為 false。

*pbdefault*<br/>
如果安全描述符存在系統 ACL,則`SECURITY_DESCRIPTOR_CONTROL`指向 結構中SE_SACL_DEFAULTED標誌的值的標誌。

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,如果失敗,則為 false。

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc:isDacl自動繼承

確定是否將任意存取控制清單 (DACL) 設定為支援自動傳播。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含 DACL,則該 DACL 設定為支援將可繼承的訪問控制項目 (ACE) 自動傳播到現有子物件,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

系統在為物件及其現有子物件執行自動繼承演演算法時設置此位。

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc:isdacl已拖欠

確定安全性是否設定預設的可自由存取控制清單 (DACL)。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含預設 DACL,則返回 true,否則為 false。

### <a name="remarks"></a>備註

此標誌會影響系統對待 DACL 的方式,有關存取控制條目 (ACE) 繼承。 例如,如果物件的建立者未指定 DACL,則該物件將從創建者的訪問令牌接收預設 DACL。 如果未設置SE_DACL_PRESENT標誌,則系統將忽略此標誌。

此標誌用於確定如何計算物件上的最後 DACL,並且不會物理存儲在可保護物件的安全描述符控件中。

要設置此標誌,請使用[CSecurityDesc::setDacl](#setdacl)方法。

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc:IsDacl存在

確定安全性是否包含可自由存取控制清單 (DACL)。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含 DACL,則返回 true,否則為 false。

### <a name="remarks"></a>備註

如果未設定此標誌,或者此標誌已設置,並且 DACL 為 NULL,則安全描述符允許對所有人進行完全訪問。

此標誌用於保存調用方指定的安全資訊,直到安全描述符與可安全物件關聯。 一旦安全描述符與可安全對象關聯,SE_DACL_PRESENT標誌始終在安全描述符控件中設置。

要設置此標誌,請使用[CSecurityDesc::setDacl](#setdacl)方法。

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc:IsDacl保護

確定是否配置了可自由存取控制列表 (DACL) 以防止修改。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 DACL 設定為防止可繼承的存取控制項目 (ACE) 修改安全描述符,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

要設置此標誌,請使用[CSecurityDesc::setDacl](#setdacl)方法。

此方法支援可繼承 ACEs 的自動傳播。

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc:是集團違約

確定預設情況下是否設置了安全描述符的組安全識別碼 (SID)。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設機制(而不是安全描述符的原始提供程式)提供安全描述符的組 SID,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

要設置此標誌,請使用[CSecurityDesc::SetGroup](#setgroup)方法。

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc:是擁有者違約

確定預設情況下是否設置了安全描述符的所有者安全識別碼 (SID)。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設機制(而不是安全描述符的原始提供程式)提供安全描述符的所有者 SID,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

要設置此標誌,請使用[CSecurityDesc::SetOwner](#setowner)方法。

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc:issacl自動繼承

確定系統存取控制清單 (SACL) 是否設定為支援自動傳播。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含 SACL,則該 SACL 設置為支援將可繼承的訪問控制項目 (ACE) 自動傳播到現有子物件,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

系統在為物件及其現有子物件執行自動繼承演演算法時設置此位。

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>安全::已違約

確定安全性是否設定了預設系統存取控制清單 (SACL)。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含預設 SACL,則返回 true,否則為 false。

### <a name="remarks"></a>備註

此標誌會影響系統對待 SACL 的方式,有關存取控制條目 (ACE) 繼承。 如果未設置SE_SACL_PRESENT標誌,系統將忽略此標誌。

要設置此標誌,請使用[CSecurityDesc::setSacl](#setsacl)方法。

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>安全::Issacl存在

確定安全描述符是否包含系統存取控制列表 (SACL)。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符包含 SACL,則返回 true,否則為 false。

### <a name="remarks"></a>備註

要設置此標誌,請使用[CSecurityDesc::setSacl](#setsacl)方法。

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>安全::Issacl保護

確定是否配置了系統存取控制清單 (SACL) 以防止修改。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 SACL 設定為防止可繼承的存取控制條目 (ACE) 修改安全描述符,則返回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

要設置此標誌,請使用[CSecurityDesc::setSacl](#setsacl)方法。

此方法支援可繼承 ACEs 的自動傳播。

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc:是自我相對的

確定安全性是否採用自相對格式。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述符採用自相對格式,所有安全資訊都位於連續的記憶體塊中,則返回 true。 如果安全描述符為絕對格式,則返回 false。 有關詳細資訊,請參閱[絕對和自我相對安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc:使絕對

呼叫此方法可將安全描述符轉換為絕對格式。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,否則為 false。

### <a name="remarks"></a>備註

絕對格式的安全描述符包含指向它包含的資訊的指標,而不是資訊本身。 自相對格式的安全描述符包含連續記憶體區中的資訊。 在自相對安全描述符中`SECURITY_DESCRIPTOR`,結構始終啟動資訊,但安全描述符的其他元件可以按任何順序跟蹤結構。 與使用記憶體位址相比,自相對安全描述符的元件由安全描述符開頭的偏移量標識。 當安全描述符必須存儲在磁碟上或通過通訊協定傳輸時,此格式非常有用。 有關詳細資訊,請參閱[絕對和自我相對安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc:使自我相關

呼叫此方法可將安全描述符轉換為自相關格式。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功,則返回 true,否則為 false。

### <a name="remarks"></a>備註

絕對格式的安全描述符包含指向它包含的資訊的指標,而不是包含資訊本身。 自相對格式的安全描述符包含連續記憶體區中的資訊。 在自相對安全描述符中`SECURITY_DESCRIPTOR`,結構始終啟動資訊,但安全描述符的其他元件可以按任何順序跟蹤結構。 安全描述符的元件不是使用記憶體位址,而是通過安全描述符開頭的偏移量標識。 當安全描述符必須存儲在磁碟上或通過通訊協定傳輸時,此格式非常有用。 有關詳細資訊,請參閱[絕對和自我相對安全描述符](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)。

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::操作員 |

指派運算子。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`SECURITY_DESCRIPTOR`分配給`CSecurityDesc`對`CSecurityDesc`象的結構或物件。

### <a name="return-value"></a>傳回值

返回更新`CSecurityDesc`的物件。

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::操作員SECURITY_DESCRIPTOR |

將值投射到指向結構的`SECURITY_DESCRIPTOR`指標。

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc:設定控制

設定安全性描述元的控制位元。

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>參數

*控制興趣*<br/>
指出要設定之控制位元的 SECURITY_DESCRIPTOR_CONTROL 遮罩。 有關可以設定的旗標的清單,請參考[設定安全性描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

*控制位集*<br/>
SECURITY_DESCRIPTOR_CONTROL遮罩,*指示 由 ControlBits Ofery*遮罩指定的控制元件位的新值。 此參數可以是*為 ControlBits Ofery 參數*列出的標誌的組合。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

此方法呼叫[SetSecurity 描述器控制](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc:SetDacl

在自由存取控制清單 (DACL) 中設定資訊。 如果安全描述符中已存在 DACL,則替換它。

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*Dacl*<br/>
引用指定`CDacl`安全描述符的 DACL 的物件。 此參數不能為 NULL。 要在安全描述符中設置 NULL DACL,該方法的第一種形式應與設置為 false 的*b存在*一起使用。

*b目前*<br/>
指定指示安全描述符中存在 DACL 的標誌。 如果此參數為 true,則該方法`SECURITY_DESCRIPTOR_CONTROL`在結構中設置SE_DACL_PRESENT標誌,並使用*Dacl*和*bDefault 參數*中的值。 如果為 false,則方法清除SE_DACL_PRESENT標誌,並忽略*bDefault。*

*b 預設*<br/>
指定指示 DACL 源的標誌。 如果此標誌為 true,則某些預設機制已檢索 DACL。 如果為 false,則使用者已顯式指定 DACL。 這個方法將此值儲存在結構SE_DACL_DEFAULTED標誌中`SECURITY_DESCRIPTOR_CONTROL`。 如果未指定此參數,則清除SE_DACL_DEFAULTED標誌。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

空和不存在的 DACL 之間存在重要區別。 當 DACL 為空時,它不包含訪問控制條目,並且未顯式授予訪問許可權。 因此,隱式拒絕對對象的訪問。 另一方面,當物件沒有 DACL 時,則不向該物件分配任何保護,並且授予任何訪問請求。

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc:setGroup

設定絕對格式安全描述符的主組資訊,替換已存在的任何主組資訊。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*希*<br/>
對安全描述符的新主組的[CSid](../../atl/reference/csid-class.md)物件的引用。 此參數不能為 NULL。 安全描述符可以標記為沒有 DACL 或 SACL,但它必須有一個組和一個擁有者,即使它們是 NULL SID(這是具有特殊含義的內置 SID)。

*b 預設*<br/>
指示主組資訊是否派生自預設機制。 如果此值為 true,則它是默認資訊,該方法將此值存儲為結構`SECURITY_DESCRIPTOR_CONTROL`中 SE_GROUP_DEFAULTED標誌。 如果此參數為零,則清除SE_GROUP_DEFAULTED標誌。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

設置絕對格式安全描述符的所有者資訊。 它替換已經存在的任何擁有者資訊。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*希*<br/>
安全描述符的新主擁有者的[CSid](../../atl/reference/csid-class.md)物件。 此參數不能為 NULL。

*b 預設*<br/>
指示擁有者資訊是否派生自預設機制。 如果此值為 true,則為默認資訊。 該方法將此值存儲為`SECURITY_DESCRIPTOR_CONTROL`結構中SE_OWNER_DEFAULTED標誌。 如果此參數為零,則清除SE_OWNER_DEFAULTED標誌。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>安全::SetSacl

在系統存取控制清單 (SACL) 中設定資訊。 如果安全描述符中已存在SACL,則替換它。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*薩克拉*<br/>
指向指定安全`CSacl`描述符的 SACL 的物件的指標。 此參數不能為 NULL,並且必須是 CSacl 物件。 與 DSL 不同,NULL 和空 SACL 沒有區別,因為 SACL 物件不指定訪問許可權,只指定審核資訊。

*b 預設*<br/>
指定指示 SACL 源的標誌。 如果此標誌為 true,則某些預設機制已檢索 SACL。 如果為 false,則使用者已顯式指定 SACL。 這個方法將此值儲存在結構SE_SACL_DEFAULTED旗標`SECURITY_DESCRIPTOR_CONTROL`中 。 如果未指定此參數,則清除SE_SACL_DEFAULTED標誌。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

## <a name="csecuritydesctostring"></a><a name="tostring"></a>安全::到弦

將安全描述符轉換為字串格式。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>參數

*普斯特*<br/>
指向將接收[字串格式安全描述符](/windows/win32/SecAuthZ/security-descriptor-string-format)的 null 終止字串的指標。

*si*<br/>
指定SECURITY_INFORMATION位標誌的組合,以指示要包含在輸出字串中的安全描述符的元件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

一旦安全描述符採用字串格式,就可以更輕鬆地存儲或傳輸它。 使用`CSecurityDesc::FromString`方法將字串轉換回安全描述元。

*si*參數可以包含以下SECURITY_INFORMATION標誌:

|值|意義|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|包括擁有者。|
|GROUP_SECURITY_INFORMATION|包括主組。|
|DACL_SECURITY_INFORMATION|包括 DACL。|
|SACL_SECURITY_INFORMATION|包括SACL。|

如果 DACL 為 NULL,並且SE_DACL_PRESENT控制位在輸入安全描述符中設置,則該方法將失敗。

如果 DACL 為 NULL,並且SE_DACL_PRESENT控制位未在輸入安全描述符中設置,則生成的安全描述符字串沒有 D: 元件。 關於詳細資訊,請參閱[安全描述符字串格式](/windows/win32/SecAuthZ/security-descriptor-string-format)。

此方法調用[ConvertString 安全性描述](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)符。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
