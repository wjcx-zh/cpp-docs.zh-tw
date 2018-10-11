---
title: CSecurityDesc 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3df63cbed5fcb17b01450435aa2d991ca3e0c5a8
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083914"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 類別

這個類別是包裝函式`SECURITY_DESCRIPTOR`結構。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|將字串格式的安全性描述元轉換成有效、 功能安全性描述元。|
|[CSecurityDesc::GetControl](#getcontrol)|擷取控制從安全性描述元的資訊。|
|[CSecurityDesc::GetDacl](#getdacl)|擷取安全性描述元中 discretionary 存取控制清單 (DACL) 資訊。|
|[CSecurityDesc::GetGroup](#getgroup)|擷取安全性描述元主要群組資訊。|
|[CSecurityDesc::GetOwner](#getowner)|擷取安全性描述元擁有者資訊。|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|將指標傳回至`SECURITY_DESCRIPTOR`結構。|
|[CSecurityDesc::GetSacl](#getsacl)|擷取安全性描述元的系統存取控制清單 (SACL) 資訊。|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|決定是否 DACL 已設定為支援自動傳播。|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|決定是否已使用預設 DACL 的安全性描述元。|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|判斷安全性描述元是否包含 DACL。|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|決定是否 DACL 設定為防止修改。|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|決定是否預設已設定的安全性描述元的群組安全性識別碼 (SID)。|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|決定是否預設已設定的安全性描述元擁有者 SID。|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|決定是否 SACL 已設定為支援自動傳播。|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|決定是否安全性描述元會設定預設的 SACL。|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|判斷安全性描述元是否包含 SACL。|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|決定是否 SACL 設定為防止修改。|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|決定是否在自我相關格式的安全性描述元。|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|呼叫這個方法來將安全性描述元轉換為絕對的格式。|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|呼叫這個方法來將安全性描述元轉換成自我相關格式。|
|[CSecurityDesc::SetControl](#setcontrol)|設定安全性描述元的控制位元。|
|[CSecurityDesc::SetDacl](#setdacl)|設定在 DACL 中的資訊。 如果 DACL 中已有的安全性描述元，它會取代它。|
|[CSecurityDesc::SetGroup](#setgroup)|設定主要群組的資訊的絕對格式的安全性描述元，取代任何已存在的主要群組資訊。|
|[CSecurityDesc::SetOwner](#setowner)|設定擁有者的資訊的絕對格式的安全性描述元，取代任何已存在的擁有者資訊。|
|[CSecurityDesc::SetSacl](#setsacl)|設定 SACL 中的資訊。 如果 SACL 中已有的安全性描述元，它會取代它。|
|[CSecurityDesc::ToString](#tostring)|將安全性描述元轉換成字串格式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|將指標傳回至`SECURITY_DESCRIPTOR`結構。|
|[CSecurityDesc::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`SECURITY_DESCRIPTOR`結構包含與物件相關聯的安全性資訊。 應用程式會使用此結構，來設定和查詢物件的安全性狀態。 另請參閱[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。

應用程式不應該修改`SECURITY_DESCRIPTOR`結構直接，並改為應該使用類別提供的方法。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

建構函式。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`CSecurityDesc`物件或`SECURITY_DESCRIPTOR`若要指派給新的結構`CSecurityDesc`物件。

### <a name="remarks"></a>備註

`CSecurityDesc`物件可以選擇性地使用來建立`SECURITY_DESCRIPTOR`結構或先前定義`CSecurityDesc`物件。

##  <a name="dtor"></a>  CSecurityDesc::~CSecurityDesc

解構函式。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>備註

解構函式會釋放所有配置的資源。

##  <a name="fromstring"></a>  CSecurityDesc::FromString

將字串格式的安全性描述元轉換成有效、 功能安全性描述元。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>參數

*pstr*<br/>
以 null 終止的字串，其中包含的指標[字串格式的安全性描述元](/windows/desktop/SecAuthZ/security-descriptor-string-format)轉換。

### <a name="return-value"></a>傳回值

如果成功則傳回 true。 在失敗時擲回例外狀況。

### <a name="remarks"></a>備註

可以使用建立的字串[CSecurityDesc::ToString](#tostring)。 將安全性描述元轉換成字串，可讓您更輕鬆地儲存和傳輸。

這個方法會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora)。

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

擷取控制從安全性描述元的資訊。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>參數

*psdc*<br/>
指標`SECURITY_DESCRIPTOR_CONTROL`接收的安全性描述元控制資訊的結構。

### <a name="return-value"></a>傳回值

如果方法成功，false 失敗時傳回 true。

### <a name="remarks"></a>備註

這個方法會呼叫[GetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa446647)。

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

擷取安全性描述元中 discretionary 存取控制清單 (DACL) 資訊。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
指標`CDacl`結構用來儲存一份安全性描述元的 DACL。 如果存在判別 ACL，方法會設定*pDacl*安全性描述元的判別 ACL 的位址。 如果判別 ACL 不存在，則會不儲存任何值。

*pbPresent*<br/>
值，指出指定的安全性描述元中的判別 ACL 的目前狀態的指標。 如果安全性描述元包含判別 ACL，此參數會設定為 true。 如果安全性描述元不包含判別 ACL，此參數設為 false。

*pbDefaulted*<br/>
為 SE_DACL_DEFAULTED 旗標值的一組旗標指標`SECURITY_DESCRIPTOR_CONTROL`結構判別 ACL 有的安全性描述元。 如果這個旗標為 true，判別 ACL 已擷取由預設機制;如果為 false，使用者已明確指定判別 ACL。

### <a name="return-value"></a>傳回值

如果方法成功，false 失敗時傳回 true。

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

擷取安全性描述元主要群組資訊。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼），會收到一份 CDacl 中儲存的群組。

*pbDefaulted*<br/>
為 SE_GROUP_DEFAULTED 旗標值的一組旗標指標`SECURITY_DESCRIPTOR_CONTROL`結構方法傳回時。

### <a name="return-value"></a>傳回值

如果方法成功，false 失敗時傳回 true。

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

擷取安全性描述元擁有者資訊。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼），會收到一份 CDacl 中儲存的群組。

*pbDefaulted*<br/>
為 SE_OWNER_DEFAULTED 旗標值的一組旗標指標`SECURITY_DESCRIPTOR_CONTROL`結構方法傳回時。

### <a name="return-value"></a>傳回值

如果方法成功，false 失敗時傳回 true。

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

將指標傳回至`SECURITY_DESCRIPTOR`結構。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>傳回值

將指標傳回至[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)結構。

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

擷取安全性描述元的系統存取控制清單 (SACL) 資訊。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSacl*<br/>
指標`CSacl`結構用來儲存一份安全性描述元的 SACL。 如果系統 ACL 存在，方法會設定*pSacl*安全性描述元的系統 ACL 的位址。 如果系統 ACL 不存在，則會不儲存任何值。

*pbPresent*<br/>
方法的旗標的指標將設定為表示指定的安全性描述元中的系統 ACL 存在。 如果安全性描述元包含系統 ACL，此參數會設定為 true。 如果安全性描述元不包含系統 ACL，此參數設為 false。

*pbDefaulted*<br/>
為 SE_SACL_DEFAULTED 旗標值的一組旗標指標`SECURITY_DESCRIPTOR_CONTROL`結構的安全性描述元的系統 ACL 有。

### <a name="return-value"></a>傳回值

如果方法成功，false 失敗時傳回 true。

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

決定是否判別存取控制清單 (DACL) 已設定為支援自動傳播。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含設定為支援自動傳播繼承的存取控制項目 (Ace) 至現有的子物件 DACL，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

執行自動繼承演算法的物件和其現有的子物件時，系統就會設定此位元。

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

決定是否已使用預設的判別存取控制清單 (DACL) 的安全性描述元。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含預設 DACL，false 否則，傳回 true。

### <a name="remarks"></a>備註

這個旗標可能會影響系統的 DACL，相對於存取控制項目 (ACE) 繼承的處理方式。 例如，如果物件的建立者未指定 DACL，物件會接收預設 DACL 從建立者的存取權杖。 如果未設定 SE_DACL_PRESENT 旗標，系統就會忽略此旗標。

這個旗標用來判斷要如何計算最終的 DACL 物件上，並不會儲存實際在安全性實體物件的安全性描述元控制。

若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

判斷安全性描述元是否包含判別存取控制清單 (DACL)。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含 DACL，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

如果未設定此旗標，或如果在設定這個旗標，而 DACL 是 NULL，安全性描述元可讓所有人都能完整存取。

這個旗標用來保存的安全性描述元相關聯的安全性實體物件之前，呼叫端所指定的安全性資訊。 安全性實體物件相關聯的安全性描述元之後，SE_DACL_PRESENT 旗標一定會設定安全性描述元控制中。

若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

決定是否判別存取控制清單 (DACL) 設定為防止修改。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 DACL 設定為可繼承的存取控制項目 (Ace) 正在修改時，防止安全性描述元，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。

這個方法支援自動傳播繼承的 Ace。

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

決定是否預設已設定的安全性描述元的群組安全性識別碼 (SID)。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元，群組 SID，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標，使用[csecuritydesc:: Setgroup](#setgroup)方法。

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

決定是否預設已設定的安全性描述元擁有者安全性識別碼 (SID)。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元擁有者 SID，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標，使用[csecuritydesc:: Setowner](#setowner)方法。

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

決定系統存取控制清單 (SACL) 是否設定為支援自動傳播。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含設定為支援自動傳播繼承的存取控制項目 (Ace) 至現有的子物件的 SACL，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

執行自動繼承演算法的物件和其現有的子物件時，系統就會設定此位元。

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

決定是否已使用預設系統存取控制清單 (SACL) 安全性描述元。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含預設 SACL，false 否則，傳回 true。

### <a name="remarks"></a>備註

這個旗標可能會影響系統的 SACL，相對於存取控制項目 (ACE) 繼承的處理方式。 如果未設定 SE_SACL_PRESENT 旗標，系統就會忽略此旗標。

若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

判斷安全性描述元是否包含系統存取控制清單 (SACL)。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元包含 SACL，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

決定系統存取控制清單 (SACL) 是否設定為防止修改。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>傳回值

如果 SACL 設定為可繼承的存取控制項目 (Ace) 正在修改時，防止安全性描述元，則傳回 true。 否則會傳回 False。

### <a name="remarks"></a>備註

若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。

這個方法支援自動傳播繼承的 Ace。

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

決定是否在自我相關格式的安全性描述元。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>傳回值

如果安全性描述元與連續的記憶體區塊中的所有安全性資訊處於自我相關格式，則傳回 true。 如果安全性描述元是絕對格式，就會傳回 false。 如需詳細資訊，請參閱 < [Absolute 和 Self-Relative 安全性描述元](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

呼叫這個方法來將安全性描述元轉換為絕對的格式。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

絕對格式的安全性描述元包含它所包含的資訊，而不是本身的資訊的指標。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中`SECURITY_DESCRIPTOR`結構永遠啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用記憶體位址，從安全性描述元開頭的位移被識別自我關聯的安全性描述元的元件。 必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元時，此格式會很有用。 如需詳細資訊，請參閱 < [Absolute 和 Self-Relative 安全性描述元](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

呼叫這個方法來將安全性描述元轉換成自我相關格式。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>傳回值

如果方法成功，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

絕對格式的安全性描述元包含它所包含的資訊，而不是包含本身的資訊的指標。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中`SECURITY_DESCRIPTOR`結構永遠啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用記憶體位址，從安全性描述元開頭的位移所識別的安全性描述元的元件。 必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元時，此格式會很有用。 如需詳細資訊，請參閱 < [Absolute 和 Self-Relative 安全性描述元](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors)。

##  <a name="operator_eq"></a>  CSecurityDesc::operator =

指派運算子。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`SECURITY_DESCRIPTOR`結構或`CSecurityDesc`物件指派給`CSecurityDesc`物件。

### <a name="return-value"></a>傳回值

傳回已更新`CSecurityDesc`物件。

##  <a name="operator_const_security_descriptor__star"></a>  CSecurityDesc::operator const SECURITY_DESCRIPTOR *

將指標值轉換`SECURITY_DESCRIPTOR`結構。

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
SECURITY_DESCRIPTOR_CONTROL 遮罩，指出若要設定的控制位元。 如需可設定之旗標的清單，請參閱 < [SetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa379582)。

*ControlBitsToSet*<br/>
SECURITY_DESCRIPTOR_CONTROL 遮罩，表示新的值，指定控制位元*ControlBitsOfInterest*遮罩。 這個參數可以是針對列出的旗標的組合*ControlBitsOfInterest*參數。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會呼叫[SetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa379582)。

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

判別存取控制清單 (DACL) 中設定資訊。 如果 DACL 中已有的安全性描述元，它會取代它。

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
若要參考`CDacl`物件，指定安全性描述元的 DACL。 這個參數必須不是 NULL。 若要設定安全性描述元中的 NULL DACL，第一種形式的方法應該搭配*bPresent*設為 false。

*bPresent*<br/>
指定旗標，指出安全性描述元中 DACL 的目前狀態。 如果此參數為 true，則方法會設定 SE_DACL_PRESENT 旗標中`SECURITY_DESCRIPTOR_CONTROL`結構，並使用中的值*Dacl*並*bDefaulted*參數。 如果為 false，方法會清除 SE_DACL_PRESENT 旗標，並*bDefaulted*會被忽略。

*bDefaulted*<br/>
指定旗標，指出 DACL 的來源。 如果這個旗標為 true，DACL 已擷取的一些預設的機制。 如果為 false，DACL 已明確指定的使用者。 方法會將此值儲存在 SE_DACL_DEFAULTED 旗標的`SECURITY_DESCRIPTOR_CONTROL`結構。 如果未指定此參數，則會清除 SE_DACL_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

沒有空白且不存在的 DACL 的重要差異。 DACL 是空的它不包含存取控制項目，並沒有存取權限已明確授與。 如此一來，會隱含拒絕物件的存取權。 當物件有沒有 DACL 時，相反地，沒有保護指派給物件，並授與任何存取要求。

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

設定主要群組的資訊的絕對格式的安全性描述元，取代任何已存在的主要群組資訊。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*sid*<br/>
若要參考[CSid](../../atl/reference/csid-class.md)物件安全性描述元的新主要群組。 這個參數必須不是 NULL。 安全性描述元可以標示為沒有 DACL 或 SACL，但它必須擁有群組和擁有者，這些甚至會 NULL SID （這是具有特殊意義的內建 SID）。

*bDefaulted*<br/>
表示主要群組資訊是否衍生自預設機制。 如果此值為 true，它是預設的詳細資訊，方法會將此值儲存為 SE_GROUP_DEFAULTED 旗標`SECURITY_DESCRIPTOR_CONTROL`結構。 如果此參數為零，則會清除 SE_GROUP_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

設定絕對格式的安全性描述元的擁有者資訊。 它會取代任何已存在的擁有者資訊。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*sid*<br/>
[CSid](../../atl/reference/csid-class.md)安全性描述元的新主要擁有者的物件。 這個參數必須不是 NULL。

*bDefaulted*<br/>
指出是否要將擁有者資訊衍生自預設機制。 如果此值為 true，則預設資訊。 方法會將此值儲存為 SE_OWNER_DEFAULTED 旗標`SECURITY_DESCRIPTOR_CONTROL`結構。 如果此參數為零，則會清除 SE_OWNER_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

設定系統存取控制清單 (SACL) 中的資訊。 如果 SACL 中已有的安全性描述元，它會取代它。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>參數

*Sacl*<br/>
指標`CSacl`物件，指定安全性描述元的 SACL。 這個參數不可以是 NULL，且必須是 CSacl 物件。 不同於 Dacl，並無差別 NULL 和空的 SACL，之間，SACL 物件未指定存取權限，只有稽核資訊。

*bDefaulted*<br/>
指定旗標，指出 SACL 的來源。 如果這個旗標為 true，SACL 已擷取的一些預設的機制。 如果為 false，SACL 已明確指定的使用者。 方法會將此值儲存在 SE_SACL_DEFAULTED 旗標的`SECURITY_DESCRIPTOR_CONTROL`結構。 如果未指定此參數，則會清除 SE_SACL_DEFAULTED 旗標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

##  <a name="tostring"></a>  CSecurityDesc::ToString

將安全性描述元轉換成字串格式。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>參數

*pstr*<br/>
將會收到的 null 終止字串的指標[字串格式的安全性描述元](/windows/desktop/SecAuthZ/security-descriptor-string-format)。

*si*<br/>
指定 SECURITY_INFORMATION 位元旗標，表示要包含在輸出字串中的安全性描述元的元件組合。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

字串格式的安全性描述元之後，它可以更輕鬆地儲存或傳輸。 使用`CSecurityDesc::FromString`方法將字串轉換回的安全性描述元。

*Si*參數可以包含下列 SECURITY_INFORMATION 旗標：

|值|意義|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|包含擁有者。|
|GROUP_SECURITY_INFORMATION|包含的主要群組。|
|DACL_SECURITY_INFORMATION|包含的 DACL。|
|SACL_SECURITY_INFORMATION|包括 SACL。|

如果 DACL 受到 NULL 輸入的安全性描述元中設定 SE_DACL_PRESENT 控制位元，方法就會失敗。

如果 DACL 受到 NULL 輸入的安全性描述元中未設定 SE_DACL_PRESENT 控制位元，產生的安全性描述元字串，並沒有 d： 元件。 請參閱[安全性描述元字串格式](/windows/desktop/SecAuthZ/security-descriptor-string-format)如需詳細資訊。

這個方法會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora)。

## <a name="see-also"></a>另請參閱

[安全性範例](../../visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
