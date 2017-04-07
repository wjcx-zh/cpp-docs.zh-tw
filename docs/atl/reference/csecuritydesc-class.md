---
title: "CSecurityDesc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 334081ba67c3b034c4b8170b095fcd77d712dda6
ms.lasthandoff: 04/04/2017

---
# <a name="csecuritydesc-class"></a>CSecurityDesc 類別
這個類別是包裝函式**SECURITY_DESCRIPTOR**結構。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSecurityDesc
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|建構函式。|  
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSecurityDesc::FromString](#fromstring)|將字串格式的安全性描述元轉換成有效、 功能安全性描述元。|  
|[Csecuritydesc:: Getcontrol](#getcontrol)|擷取控制資訊的安全性描述元。|  
|[CSecurityDesc::GetDacl](#getdacl)|擷取的安全性描述元的判別存取控制清單 (DACL) 資訊。|  
|[CSecurityDesc::GetGroup](#getgroup)|擷取的安全性描述元主要群組資訊。|  
|[CSecurityDesc::GetOwner](#getowner)|擷取的安全性描述元擁有者資訊。|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|將指標傳回至**SECURITY_DESCRIPTOR**結構。|  
|[CSecurityDesc::GetSacl](#getsacl)|擷取的安全性描述元的系統存取控制清單 (SACL) 資訊。|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|決定是否 DACL 設定為支援自動傳播。|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|決定是否已有預設的 DACL 的安全性描述元。|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|判斷安全性描述元是否包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|決定是否 DACL 設定為防止進行修改。|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|決定是否預設已設定的安全性描述元群組安全性識別碼 (SID)。|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|決定是否預設已設定的安全性描述元擁有者 SID。|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|決定是否 SACL 設定為支援自動傳播。|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|決定是否安全性描述元會設定預設 SACL。|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|判斷安全性描述元是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|決定是否 SACL 會設定為防止進行修改。|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|決定是否自我相關格式的安全性描述元。|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|呼叫此方法以將安全性描述元轉換成絕對的格式。|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|呼叫此方法以將安全性描述元轉換成自我關聯的格式。|  
|[CSecurityDesc::SetControl](#setcontrol)|設定安全性描述元的控制位元。|  
|[Csecuritydesc:: Setdacl](#setdacl)|DACL 中設定。 如果 DACL 中已有的安全性描述元，它會取代它。|  
|[Csecuritydesc:: Setgroup](#setgroup)|設定絕對格式安全性描述元，以取代任何現有的主要群組資訊的主要群組資訊。|  
|[Csecuritydesc:: Setowner](#setowner)|設定絕對格式安全性描述元，以取代任何現有的擁有者資訊的擁有者資訊。|  
|[Csecuritydesc:: Setsacl](#setsacl)|設定的 SACL 中的資訊。 如果已經存在的安全性描述元中 SACL，則會取代它。|  
|[CSecurityDesc::ToString](#tostring)|將安全性描述元轉換成字串格式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|將指標傳回至**SECURITY_DESCRIPTOR**結構。|  
|[CSecurityDesc::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 **SECURITY_DESCRIPTOR**結構包含與物件相關聯的安全性資訊。 應用程式會使用此結構來設定和查詢物件的安全性狀態。 另請參閱[AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)。  
  
 應用程式不應修改**SECURITY_DESCRIPTOR**結構直接，並改為應該使用類別提供的方法。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 建構函式。  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CSecurityDesc`物件或**SECURITY_DESCRIPTOR**結構，以指派給新`CSecurityDesc`物件。  
  
### <a name="remarks"></a>備註  
 `CSecurityDesc`物件可以選擇性地建立使用**SECURITY_DESCRIPTOR**結構或先前已定義`CSecurityDesc`物件。  
  
##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 解構函式。  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放所有配置的資源。  
  
##  <a name="fromstring"></a>CSecurityDesc::FromString  
 將字串格式的安全性描述元轉換成有效、 功能安全性描述元。  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 以 null 終止的字串，其中包含指標[字串格式的安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379570)轉換。  
  
### <a name="return-value"></a>傳回值  
 成功則傳回 true。 在失敗時擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 字串可由使用[CSecurityDesc::ToString](#tostring)。 將安全性描述元轉換成字串，可以更輕鬆地儲存及傳輸。  
  
 這個方法僅可與 Windows 2000 和更新版本因為它會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
##  <a name="getcontrol"></a>Csecuritydesc:: Getcontrol  
 擷取控制資訊的安全性描述元。  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>參數  
 *psdc*  
 指標**SECURITY_DESCRIPTOR_CONTROL**接收的安全性描述元控制資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 如果失敗，則傳回 true。  
  
### <a name="remarks"></a>備註  
 這個方法僅有意義，當使用 Windows 2000 或更新版本，因為它會呼叫[GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647)。  
  
##  <a name="getdacl"></a>CSecurityDesc::GetDacl  
 擷取的安全性描述元的判別存取控制清單 (DACL) 資訊。  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pDacl`  
 指標`CDacl`結構用來儲存一份 DACL 的安全性描述元。 如果判別**ACL**存在，方法會設定`pDacl`位址的安全性描述元的判別**ACL**。 如果判別**ACL**不存在，會儲存任何值。  
  
 `pbPresent`  
 指標值，指出是否存在判別**ACL**中指定的安全性描述元。 如果安全性描述元包含判別**ACL**，此參數設為 true。 如果安全性描述元不包含判別**ACL**，此參數設為 false。  
  
 `pbDefaulted`  
 指標的旗標設為 SE_DACL_DEFAULTED 旗標的值**SECURITY_DESCRIPTOR_CONTROL**結構如果判別**ACL**存在的安全性描述元。 如果這個旗標為 true，判別**ACL**擷取預設機制; 如果為 false，判別**ACL**已由使用者明確地指定。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 如果失敗，則傳回 true。  
  
##  <a name="getgroup"></a>CSecurityDesc::GetGroup  
 擷取的安全性描述元主要群組資訊。  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼） 接收 CDacl 中儲存群組的複本。  
  
 `pbDefaulted`  
 指標的旗標設為 SE_GROUP_DEFAULTED 旗標的值**SECURITY_DESCRIPTOR_CONTROL**結構方法傳回時。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 如果失敗，則傳回 true。  
  
##  <a name="getowner"></a>CSecurityDesc::GetOwner  
 擷取的安全性描述元擁有者資訊。  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼） 接收 CDacl 中儲存群組的複本。  
  
 `pbDefaulted`  
 指標的旗標設為 SE_OWNER_DEFAULTED 旗標的值**SECURITY_DESCRIPTOR_CONTROL**結構方法傳回時。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 如果失敗，則傳回 true。  
  
##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 將指標傳回至**SECURITY_DESCRIPTOR**結構。  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)結構。  
  
##  <a name="getsacl"></a>CSecurityDesc::GetSacl  
 擷取的安全性描述元的系統存取控制清單 (SACL) 資訊。  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSacl`  
 指標`CSacl`要儲存副本的安全性描述元 SACL 的結構。 如果系統**ACL**存在，方法會設定`pSacl`系統的安全性描述元的位址**ACL**。 如果系統**ACL**不存在，會儲存任何值。  
  
 `pbPresent`  
 方法會設定指出系統是否存在的旗標的指標**ACL**中指定的安全性描述元。 如果安全性描述元包含在系統**ACL**，此參數設為 true。 如果安全性描述元不包含系統**ACL**，此參數設為 false。  
  
 `pbDefaulted`  
 指標的旗標設為 SE_SACL_DEFAULTED 旗標的值**SECURITY_DESCRIPTOR_CONTROL**結構如果系統**ACL**存在的安全性描述元。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 如果失敗，則傳回 true。  
  
##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 決定是否判別存取控制清單 (DACL) 已設定為支援自動傳播。  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含設定來支援自動傳播繼承的存取控制項目 (Ace) 至現有的子物件的 DACL，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 執行自動繼承演算法物件和其現有的子物件時，系統就會設定此位元。  
  
##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 決定是否使用預設的判別存取控制清單 (DACL) 設定的安全性描述元。  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含預設的 DACL，false 否則會傳回 true。  
  
### <a name="remarks"></a>備註  
 這個旗標可能會影響系統如何處理 DACL，相對於存取控制項目 (ACE) 繼承。 例如，如果物件的建立者未指定 DACL，物件會接收預設 DACL 從建立者的存取權杖。 如果未設定 SE_DACL_PRESENT 旗標，系統會忽略此旗標。  
  
 這個旗標用來判斷最終 DACL 物件上的計算方式，並不會儲存實際在安全性實體物件的安全性描述元控制。  
  
 若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 判斷安全性描述元是否包含判別存取控制清單 (DACL)。  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含 DACL，false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 如果未設定此旗標，或如果在設定此旗標且 DACL 是 NULL，安全性描述元可讓所有人的完整存取權。  
  
 這個旗標用來保存安全性資訊的安全性描述元相關聯的安全性實體物件之前，呼叫端所指定。 一旦安全性實體物件相關聯的安全性描述元，SE_DACL_PRESENT 旗標一定會設定安全性描述元控制項中。  
  
 若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
##  <a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected  
 決定是否判別存取控制清單 (DACL) 為了避免修改設定。  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果 DACL 設定為防止修改繼承的存取控制項目 (Ace) 的安全性描述元，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[csecuritydesc:: Setdacl](#setdacl)方法。  
  
 這個方法僅有意義的 Windows 2000 或更新版本中，只有 Windows 2000 支援自動傳播繼承 Ace。  
  
##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 決定是否預設已設定的安全性描述元群組安全性識別碼 (SID)。  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元，群組 SID，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[csecuritydesc:: Setgroup](#setgroup)方法。  
  
##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 決定是否預設已設定的安全性描述元擁有者安全性識別碼 (SID)。  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元擁有者 SID，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[csecuritydesc:: Setowner](#setowner)方法。  
  
##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 決定系統存取控制清單 (SACL) 是否已設定為支援自動傳播。  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含設定來支援自動傳播繼承的存取控制項目 (Ace) 至現有的子物件的 SACL，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 執行自動繼承演算法物件和其現有的子物件時，系統就會設定此位元。  
  
##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 決定是否使用預設系統存取控制清單 (SACL) 設定的安全性描述元。  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含預設的 SACL，false 否則會傳回 true。  
  
### <a name="remarks"></a>備註  
 這個旗標可能會影響系統如何處理 SACL，相對於存取控制項目 (ACE) 繼承。 如果未設定 SE_SACL_PRESENT 旗標，系統會忽略此旗標。  
  
 若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 判斷安全性描述元是否包含系統存取控制清單 (SACL)。  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含 SACL，false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 決定系統存取控制清單 (SACL) 是否設定為防止進行修改。  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果 SACL 設定為防止修改繼承的存取控制項目 (Ace) 的安全性描述元，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[csecuritydesc:: Setsacl](#setsacl)方法。  
  
 這個方法僅有意義的 Windows 2000 或更新版本中，只有 Windows 2000 支援自動傳播繼承 Ace。  
  
##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 決定是否自我相關格式的安全性描述元。  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元是自我關聯的格式與連續的記憶體區塊中的所有安全性資訊，則傳回 true。 如果安全性描述元是絕對格式，就會傳回 false。 如需詳細資訊，請參閱[Absolute 和 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 呼叫此方法以將安全性描述元轉換成絕對的格式。  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 絕對格式的安全性描述元包含指向它所包含的資訊，而不是本身的資訊。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中**SECURITY_DESCRIPTOR**結構永遠啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用的記憶體位址，自我關聯的安全性描述元的元件會識別的安全性描述元開頭的位移。 當必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元，則此格式會很有用。 如需詳細資訊，請參閱[Absolute 和 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 呼叫此方法以將安全性描述元轉換成自我關聯的格式。  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為 false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 絕對格式的安全性描述元包含指向它所包含的資訊，而不是包含本身的資訊。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中**SECURITY_DESCRIPTOR**結構永遠啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用的記憶體位址，從安全性描述元開頭的位移所識別的安全性描述元的元件。 當必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元，則此格式會很有用。 如需詳細資訊，請參閱[Absolute 和 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="operator_eq"></a>CSecurityDesc::operator =  
 指派運算子。  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 **SECURITY_DESCRIPTOR**結構或`CSecurityDesc`要指派給物件`CSecurityDesc`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CSecurityDesc`物件。  
  
##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 將值轉換為指標**SECURITY_DESCRIPTOR**結構。  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="setcontrol"></a>CSecurityDesc::SetControl  
 設定安全性描述元的控制位元。  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>參數  
 `ControlBitsOfInterest`  
 A **SECURITY_DESCRIPTOR_CONTROL**遮罩，表示若要設定的控制位元。 可以設定之旗標的清單，請參閱[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
 `ControlBitsToSet`  
 `SECURITY_DESCRIPTOR_CONTROL` 遮罩，表示 `ControlBitsOfInterest` 遮罩所指定控制位元的新值。 此參數可以是針對 `ControlBitsOfInterest` 參數所列出旗標的組合。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法是使用僅限 Windows 2000 和更新版本，因為它會呼叫[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
##  <a name="setdacl"></a>Csecuritydesc:: Setdacl  
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
 *Dacl*  
 若要參考`CDacl`物件，指定的安全性描述元的 DACL。 此參數不得為 NULL。 若要設定安全性描述元中的 NULL DACL，第一種形式的方法應搭配`bPresent`設為 false。  
  
 `bPresent`  
 指定旗標，指出 DACL 的安全性描述元中的目前狀態。 如果此參數為 true，則方法會設定 SE_DACL_PRESENT 旗標**SECURITY_DESCRIPTOR_CONTROL**結構，並使用中的值*Dacl*和`bDefaulted`參數。 如果為 false，方法會清除 SE_DACL_PRESENT 旗標和`bDefaulted`會被忽略。  
  
 `bDefaulted`  
 指定旗標，表示來源的 DACL。 如果這個旗標為 true，已藉由某種預設機制擷取 DACL。 如果為 false，DACL 已明確指定的使用者。 方法會將此值存放至 SE_DACL_DEFAULTED 旗標為**SECURITY_DESCRIPTOR_CONTROL**結構。 如果沒有指定這個參數，則會清除 SE_DACL_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 沒有一項重要差異空之間不存在的 DACL。 DACL 是空的它包含沒有任何存取控制項目，並沒有存取權限已明確授與。 如此一來，會隱含拒絕物件的存取權。 當物件具有沒有 DACL 時，相反地，沒有保護指派給物件，並授與任何存取要求。  
  
##  <a name="setgroup"></a>Csecuritydesc:: Setgroup  
 設定絕對格式安全性描述元，以取代任何現有的主要群組資訊的主要群組資訊。  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `Sid`  
 若要參考[CSid](../../atl/reference/csid-class.md)新的主要群組的安全性描述元物件。 此參數不得為 NULL。 安全性描述元可以標示為不具有 DACL 或 SACL，但是它必須有一個群組和擁有者，即使這些是 NULL 的 SID （這是具有特殊意義的內建 SID）。  
  
 `bDefaulted`  
 表示主要群組資訊是否衍生自預設機制。 如果這個值為 true，它是預設的資訊，而且方法會將此值儲存為 SE_GROUP_DEFAULTED 旗標**SECURITY_DESCRIPTOR_CONTROL**結構。 如果此參數為零，則會清除 SE_GROUP_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="setowner"></a>Csecuritydesc:: Setowner  
 設定絕對格式的安全性描述元的擁有者資訊。 它會取代任何現有的擁有者資訊。  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `Sid`  
 [CSid](../../atl/reference/csid-class.md)安全性描述元的新主要擁有者的物件。 此參數不得為 NULL。  
  
 `bDefaulted`  
 指出是否要將擁有者資訊衍生自預設機制。 如果此值為 true，則預設資訊。 方法會將此值儲存為 SE_OWNER_DEFAULTED 旗標**SECURITY_DESCRIPTOR_CONTROL**結構。 如果此參數為零，則會清除 SE_OWNER_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="setsacl"></a>Csecuritydesc:: Setsacl  
 設定系統存取控制清單 (SACL) 中的資訊。 如果已經存在的安全性描述元中 SACL，則會取代它。  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *Sacl*  
 指標`CSacl`指定 SACL 的安全性描述元物件。 這個參數不可以是 NULL，且必須是 CSacl 物件。 不同於 Dacl，沒有無差異 NULL 和空的 SACL，因為 SACL 物件未指定存取權限，只有稽核資訊。  
  
 `bDefaulted`  
 指定旗標，指出 SACL 的來源。 如果這個旗標為 true，已藉由某種預設機制擷取 SACL。 如果為 false，SACL 已明確指定的使用者。 方法會將此值存放至 SE_SACL_DEFAULTED 旗標為**SECURITY_DESCRIPTOR_CONTROL**結構。 如果沒有指定這個參數，則會清除 SE_SACL_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="tostring"></a>CSecurityDesc::ToString  
 將安全性描述元轉換成字串格式。  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 以 null 終止的字串將會接收指標[字串格式的安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379570)。  
  
 `si`  
 指定 SECURITY_INFORMATION 位元旗標，表示要包含在輸出字串中的安全性描述元元件的組合。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 字串格式的安全性描述元之後，可以更輕鬆地儲存或傳輸。 使用`CSecurityDesc::FromString`方法，將字串轉換回的安全性描述元。  
  
 `si`參數可以包含下列 SECURITY_INFORMATION 旗標︰  
  
|值|意義|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|包含擁有者。|  
|GROUP_SECURITY_INFORMATION|包含的主要群組。|  
|DACL_SECURITY_INFORMATION|包含 DACL。|  
|SACL_SECURITY_INFORMATION|包含 SACL。|  
  
 如果 DACL 受到 NULL SE_DACL_PRESENT 控制位元設定輸入的安全性描述元中，方法就會失敗。  
  
 如果 DACL 受到 NULL 輸入的安全性描述元中未設定 SE_DACL_PRESENT 控制位元，產生的安全性描述元字串中沒有 d︰ 元件。 請參閱[安全性描述元字串格式](http://msdn.microsoft.com/library/windows/desktop/aa379570)以取得詳細資料。  
  
 這個方法僅可與 Windows 2000 和更新版本，因為它會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)

