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
ms.openlocfilehash: a9e0eb01608edf29f99209dffc932630ad08807a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915716"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 類別

這個類別是`SECURITY_DESCRIPTOR`結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSecurityDesc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|建構函式。|
|[CSecurityDesc::~CSecurityDesc](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|將字串格式的安全描述項轉換成有效的功能安全描述項。|
|[CSecurityDesc::GetControl](#getcontrol)|從安全描述項抓取控制項資訊。|
|[CSecurityDesc::GetDacl](#getdacl)|從安全描述項中抓取任意存取控制清單 (DACL) 資訊。|
|[CSecurityDesc::GetGroup](#getgroup)|從安全描述項抓取主要群組資訊。|
|[CSecurityDesc::GetOwner](#getowner)|從安全描述項中抓取擁有者資訊。|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|傳回結構的`SECURITY_DESCRIPTOR`指標。|
|[CSecurityDesc::GetSacl](#getsacl)|從安全描述項抓取系統存取控制清單 (SACL) 資訊。|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|判斷 DACL 是否設定為支援自動傳播。|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|判斷安全描述項是否設定為使用預設的 DACL。|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|判斷安全描述項是否包含 DACL。|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|判斷 DACL 是否設定為防止修改。|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|判斷安全描述項的群組安全識別碼 (SID) 是否預設為設定。|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|判斷安全描述項的擁有者 SID 是否預設為設定。|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|判斷 SACL 是否設定為支援自動傳播。|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|判斷安全描述項是否設定為使用預設 SACL。|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|判斷安全描述項是否包含 SACL。|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|判斷 SACL 是否設定為防止修改。|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|判斷安全描述項是否為自我關聯格式。|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|呼叫這個方法, 將安全描述項轉換成絕對格式。|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|呼叫這個方法, 將安全描述項轉換成自我關聯的格式。|
|[CSecurityDesc::SetControl](#setcontrol)|設定安全性描述元的控制位元。|
|[CSecurityDesc::SetDacl](#setdacl)|在 DACL 中設定資訊。 如果 DACL 已經存在於安全描述項中, 就會被取代。|
|[CSecurityDesc::SetGroup](#setgroup)|設定絕對格式安全描述項的主要群組資訊, 並取代已存在的任何主要群組資訊。|
|[CSecurityDesc::SetOwner](#setowner)|設定絕對格式安全描述項的擁有者資訊, 並取代已存在的所有擁有者資訊。|
|[CSecurityDesc::SetSacl](#setsacl)|設定 SACL 中的資訊。 如果 SACL 已經存在於安全描述項中, 就會被取代。|
|[CSecurityDesc::ToString](#tostring)|將安全描述項轉換成字串格式。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|傳回結構的`SECURITY_DESCRIPTOR`指標。|
|[CSecurityDesc::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`SECURITY_DESCRIPTOR`結構包含與物件相關聯的安全性資訊。 應用程式會使用這個結構來設定及查詢物件的安全性狀態。 另請參閱[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。

應用程式不應直接`SECURITY_DESCRIPTOR`修改結構, 而應改用提供的類別方法。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

建構函式。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CSecurityDesc`指派給`SECURITY_DESCRIPTOR` 新`CSecurityDesc`物件的物件或結構。

### <a name="remarks"></a>備註

您`CSecurityDesc`可以選擇性地`SECURITY_DESCRIPTOR`使用結構或先前定義`CSecurityDesc`的物件來建立物件。

##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc

解構函式。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放所有配置的資源。

##  <a name="fromstring"></a>  CSecurityDesc::FromString

將字串格式的安全描述項轉換成有效的功能安全描述項。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>參數

*pstr*<br/>
以 null 結束的字串指標, 其中包含要轉換的[字串格式安全描述項](/windows/desktop/SecAuthZ/security-descriptor-string-format)。

### <a name="return-value"></a>傳回值

成功時傳回 true。 失敗時會擲回例外狀況。

### <a name="remarks"></a>備註

您可以使用[CSecurityDesc:: ToString](#tostring)來建立字串。 將安全描述項轉換成字串, 可讓您更輕鬆地儲存和傳輸。

這個方法會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora)。

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

從安全描述項抓取控制項資訊。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>參數

*psdc*<br/>
`SECURITY_DESCRIPTOR_CONTROL`結構的指標, 可接收安全描述項的控制項資訊。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 如果失敗, 則傳回 false。

### <a name="remarks"></a>備註

這個方法會呼叫[GetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)。

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

從安全描述項中抓取任意存取控制清單 (DACL) 資訊。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
`CDacl`結構的指標, 要在其中儲存安全描述項的 DACL 複本。 如果有任意的 ACL 存在, 方法就會將*pDacl*設定為安全描述項之任意 acl 的位址。 如果任意的 ACL 不存在, 則不會儲存任何值。

*pbPresent*<br/>
值的指標, 表示指定的安全描述項中是否存在任意的 ACL。 如果安全描述項包含任意的 ACL, 此參數會設定為 true。 如果安全描述項不包含任意的 ACL, 此參數會設定為 false。

*pbDefaulted*<br/>
旗標的指標, 如果安全描述項有任意 ACL 存在, 則`SECURITY_DESCRIPTOR_CONTROL`會設定為結構中 SE_DACL_DEFAULTED 旗標的值。 如果此旗標為 true, 則預設機制會抓取任意 ACL;如果為 false, 則表示使用者已明確指定任意 ACL。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 如果失敗, 則傳回 false。

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

從安全描述項抓取主要群組資訊。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid](../../atl/reference/csid-class.md) (安全識別碼) 的指標, 接收儲存在 CDacl 中的群組複本。

*pbDefaulted*<br/>
當方法傳回時, 設定為`SECURITY_DESCRIPTOR_CONTROL`結構中 SE_GROUP_DEFAULTED 旗標值的旗標指標。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 如果失敗, 則傳回 false。

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

從安全描述項中抓取擁有者資訊。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid](../../atl/reference/csid-class.md) (安全識別碼) 的指標, 接收儲存在 CDacl 中的群組複本。

*pbDefaulted*<br/>
當方法傳回時, 設定為`SECURITY_DESCRIPTOR_CONTROL`結構中 SE_OWNER_DEFAULTED 旗標值的旗標指標。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 如果失敗, 則傳回 false。

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

傳回結構的`SECURITY_DESCRIPTOR`指標。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>傳回值

傳回[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)結構的指標。

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

從安全描述項抓取系統存取控制清單 (SACL) 資訊。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSacl*<br/>
`CSacl`結構的指標, 用來儲存安全描述項的 SACL 複本。 如果系統 ACL 存在, 此方法會將*pSacl*設定為安全描述項系統 acl 的位址。 如果系統 ACL 不存在, 則不會儲存任何值。

*pbPresent*<br/>
方法所設定之旗標的指標, 表示指定的安全描述項中是否有系統 ACL。 如果安全描述項包含系統 ACL, 此參數會設定為 true。 如果安全描述項不包含系統 ACL, 此參數會設定為 false。

*pbDefaulted*<br/>
旗標的指標, 如果安全描述項有系統 ACL, 則會`SECURITY_DESCRIPTOR_CONTROL`設定為結構中 SE_SACL_DEFAULTED 旗標的值。

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 如果失敗, 則傳回 false。

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

決定是否將任意存取控制清單 (DACL) 設定為支援自動傳播。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含一個 DACL, 其設定為支援將可繼承的存取控制專案 (Ace) 自動傳播到現有的子物件, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

系統會在執行物件及其現有子物件的自動繼承演算法時設定此位。

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

判斷安全描述項是否已設定預設的任意存取控制清單 (DACL)。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含預設的 DACL, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

此旗標可能會影響系統處理 DACL 的方式, 與存取控制專案 (ACE) 繼承有關。 例如, 如果物件的建立者未指定 DACL, 物件會從建立者的存取權杖接收預設的 DACL。 如果未設定 SE_DACL_PRESENT 旗標, 系統會忽略此旗標。

這個旗標是用來決定如何計算物件的最後一個 DACL, 而不是實際儲存在安全物件的安全性描述項控制項中。

若要設定此旗標, 請使用[CSecurityDesc:: SetDacl](#setdacl)方法。

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

判斷安全描述項是否包含任意存取控制清單 (DACL)。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含 DACL, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

如果未設定此旗標, 或已設定此旗標, 而且 DACL 為 Null, 則安全描述項會允許所有人的完整存取權。

這個旗標是用來保存呼叫者所指定的安全性資訊, 直到安全描述項與安全物件相關聯為止。 一旦安全描述項與安全物件相關聯, 就一定會在安全描述項控制項中設定 SE_DACL_PRESENT 旗標。

若要設定此旗標, 請使用[CSecurityDesc:: SetDacl](#setdacl)方法。

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

判斷是否已設定任意存取控制清單 (DACL) 以防止修改。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 DACL 設定為防止可繼承的存取控制專案 (Ace) 修改安全描述項, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標, 請使用[CSecurityDesc:: SetDacl](#setdacl)方法。

這個方法支援自動傳播可繼承的 Ace。

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

判斷安全描述項的群組安全識別碼 (SID) 是否預設為設定。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設機制 (而不是安全描述項的原始提供者) 提供安全描述項的群組 SID, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標, 請使用[CSecurityDesc:: SetGroup](#setgroup)方法。

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

判斷是否預設設定安全描述項的擁有者安全識別碼 (SID)。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設機制 (而不是安全描述項的原始提供者) 提供安全描述項的擁有者 SID, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標, 請使用[CSecurityDesc:: SetOwner](#setowner)方法。

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

判斷系統存取控制清單 (SACL) 是否設定為支援自動傳播。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含 SACL, 其設定為支援將可繼承的存取控制專案 (Ace) 自動傳播到現有的子物件, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

系統會在執行物件及其現有子物件的自動繼承演算法時設定此位。

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

判斷安全描述項是否設定為使用預設的系統存取控制清單 (SACL)。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含預設 SACL, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

這個旗標可能會影響系統處理 SACL 的方式, 與存取控制專案 (ACE) 繼承有關。 如果未設定 SE_SACL_PRESENT 旗標, 系統會忽略此旗標。

若要設定此旗標, 請使用[CSecurityDesc:: SetSacl](#setsacl)方法。

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

判斷安全描述項是否包含系統存取控制清單 (SACL)。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項包含 SACL, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

若要設定此旗標, 請使用[CSecurityDesc:: SetSacl](#setsacl)方法。

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

判斷系統存取控制清單 (SACL) 是否設定為防止修改。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 SACL 已設定為防止可繼承的存取控制專案 (Ace) 修改安全描述項, 則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標, 請使用[CSecurityDesc:: SetSacl](#setsacl)方法。

這個方法支援自動傳播可繼承的 Ace。

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

判斷安全描述項是否為自我關聯格式。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>傳回值

如果安全描述項是獨立的格式, 而且所有安全性資訊都在連續的記憶體區塊中, 則傳回 true。 如果安全描述項是絕對格式, 則傳回 false。 如需詳細資訊, 請參閱[絕對和自我相關的安全描述項](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

呼叫這個方法, 將安全描述項轉換成絕對格式。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

絕對格式的安全描述項包含其所包含之資訊的指標, 而不是資訊本身。 自我相關格式的安全描述項包含連續記憶體區塊中的資訊。 在自我關聯的安全描述項中, `SECURITY_DESCRIPTOR`結構一律會啟動資訊, 但安全描述項的其他元件可依照任何順序追蹤結構。 與其使用記憶體位址, 自我關聯安全描述項的元件是由安全描述項開頭的位移所識別。 當安全描述項必須儲存在磁片上, 或透過通訊協定傳輸時, 此格式會很有用。 如需詳細資訊, 請參閱[絕對和自我相關的安全描述項](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

呼叫這個方法, 將安全描述項轉換成自我關聯的格式。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

絕對格式的安全描述項包含其所包含之資訊的指標, 而不是包含資訊本身。 自我相關格式的安全描述項包含連續記憶體區塊中的資訊。 在自我關聯的安全描述項中, `SECURITY_DESCRIPTOR`結構一律會啟動資訊, 但安全描述項的其他元件可依照任何順序追蹤結構。 安全描述項的元件不會使用記憶體位址, 而是由安全描述項開頭的位移來識別。 當安全描述項必須儲存在磁片上, 或透過通訊協定傳輸時, 此格式會很有用。 如需詳細資訊, 請參閱[絕對和自我相關的安全描述項](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="operator_eq"></a>CSecurityDesc:: operator =

指派運算子。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`SECURITY_DESCRIPTOR`指派給`CSecurityDesc` `CSecurityDesc`物件的結構或物件。

### <a name="return-value"></a>傳回值

傳回已更新`CSecurityDesc`的物件。

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

將值轉換成結構的`SECURITY_DESCRIPTOR`指標。

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

設定安全性描述元的控制位元。

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>參數

*ControlBitsOfInterest*<br/>
SECURITY_DESCRIPTOR_CONTROL mask, 表示要設定的控制項位。 如需可設定之旗標的清單, 請參閱[SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

*ControlBitsToSet*<br/>
SECURITY_DESCRIPTOR_CONTROL mask, 表示*ControlBitsOfInterest* mask 所指定之控制項位的新值。 這個參數可以是針對*ControlBitsOfInterest*參數所列出的旗標組合。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會呼叫[SetSecurityDescriptorControl](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)。

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

設定任意存取控制清單 (DACL) 中的資訊。 如果 DACL 已經存在於安全描述項中, 就會被取代。

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
`CDacl`物件的參考, 指定安全描述項的 DACL。 此參數不得為 Null。 若要在安全描述項中設定 Null DACL, 應該使用方法的第一個形式, 並將*bPresent*設為 false。

*bPresent*<br/>
指定表示安全描述項中是否存在 DACL 的旗標。 如果此參數為 true, 方法會在`SECURITY_DESCRIPTOR_CONTROL`結構中設定 SE_DACL_PRESENT 旗標, 並使用*DACL*和*bDefaulted*參數中的值。 如果為 false, 則方法會清除 SE_DACL_PRESENT 旗標, 並忽略*bDefaulted* 。

*bDefaulted*<br/>
指定表示 DACL 來源的旗標。 如果此旗標為 true, 則表示 DACL 已由某些預設機制抓取。 如果為 false, 則表示 DACL 已由使用者明確指定。 方法會將這個值儲存在`SECURITY_DESCRIPTOR_CONTROL`結構的 SE_DACL_DEFAULTED 旗標中。 如果未指定此參數, 則會清除 SE_DACL_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

空白和不存在的 DACL 之間有重要的差異。 當 DACL 是空的時, 它不會包含任何存取控制專案, 也不會明確授與存取權限。 因此, 會隱含拒絕對物件的存取。 另一方面, 當物件沒有 DACL 時, 就不會將任何保護指派給物件, 而且會授與任何存取要求。

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

設定絕對格式安全描述項的主要群組資訊, 並取代已存在的任何主要群組資訊。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*Sid*<br/>
安全描述項新主要群組的[CSid](../../atl/reference/csid-class.md)物件參考。 此參數不得為 Null。 安全描述項可以標示為不具備 DACL 或 SACL, 但必須擁有群組和擁有者, 即使是 Null SID (這是具有特殊意義的內建 SID)。

*bDefaulted*<br/>
指出主要群組資訊是否衍生自預設機制。 如果此值為 true, 則為預設資訊, 而方法會將這個值儲存為`SECURITY_DESCRIPTOR_CONTROL`結構中的 SE_GROUP_DEFAULTED 旗標。 如果此參數為零, 則會清除 SE_GROUP_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

設定絕對格式安全描述項的擁有者資訊。 它會取代任何已存在的擁有者資訊。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*Sid*<br/>
安全描述項新主要擁有者的[CSid](../../atl/reference/csid-class.md)物件。 此參數不得為 Null。

*bDefaulted*<br/>
指出擁有者資訊是否衍生自預設機制。 如果此值為 true, 則為預設資訊。 方法會將這個值儲存為`SECURITY_DESCRIPTOR_CONTROL`結構中的 SE_OWNER_DEFAULTED 旗標。 如果此參數為零, 則會清除 SE_OWNER_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

設定系統存取控制清單 (SACL) 中的資訊。 如果 SACL 已經存在於安全描述項中, 就會被取代。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*Sacl*<br/>
`CSacl`物件的指標, 指定安全描述項的 SACL。 這個參數不得為 Null, 而且必須是 CSacl 物件。 與 Dacl 不同的是, Null 和空白 SACL 之間沒有任何差異, 因為 SACL 物件不會指定存取權限, 只有審核資訊。

*bDefaulted*<br/>
指定表示 SACL 來源的旗標。 如果此旗標為 true, 則表示 SACL 已被部分預設機制抓取。 如果為 false, 則表示 SACL 已由使用者明確指定。 方法會將這個值儲存在`SECURITY_DESCRIPTOR_CONTROL`結構的 SE_SACL_DEFAULTED 旗標中。 如果未指定此參數, 則會清除 SE_SACL_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="tostring"></a>  CSecurityDesc::ToString

將安全描述項轉換成字串格式。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>參數

*pstr*<br/>
以 null 結束的字串指標, 將會接收[字串格式的安全描述項](/windows/desktop/SecAuthZ/security-descriptor-string-format)。

*si*<br/>
指定 SECURITY_INFORMATION 位旗標的組合, 以指示要包含在輸出字串中的安全描述項元件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

一旦安全描述項的格式為字串, 就可以更輕鬆地加以儲存或傳送。 `CSecurityDesc::FromString`使用方法, 將字串轉換回安全描述項。

*Si*參數可以包含下列 SECURITY_INFORMATION 旗標:

|值|意義|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|包含擁有者。|
|GROUP_SECURITY_INFORMATION|包含主要群組。|
|DACL_SECURITY_INFORMATION|包含 DACL。|
|SACL_SECURITY_INFORMATION|包含 SACL。|

如果 DACL 是 Null, 而且在輸入安全描述項中設定了 SE_DACL_PRESENT 控制項位, 方法就會失敗。

如果 DACL 為 Null, 且輸入安全描述項中未設定 SE_DACL_PRESENT 控制位, 則產生的安全描述項字串不會有 D: 元件。 如需詳細資訊, 請參閱[安全描述項字串格式](/windows/desktop/SecAuthZ/security-descriptor-string-format)。

這個方法會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora)。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
