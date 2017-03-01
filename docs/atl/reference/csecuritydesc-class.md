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
- ATL::CSecurityDesc
- ATL.CSecurityDesc
- CSecurityDesc
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6dbd586ee3ee07d3c567fa0aae46446397dfb62b
ms.lasthandoff: 02/24/2017

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
|[CSecurityDesc::GetControl](#getcontrol)|擷取控制從安全性描述元的資訊。|  
|[CSecurityDesc::GetDacl](#getdacl)|擷取安全性描述元的判別存取控制清單 (DACL) 資訊。|  
|[CSecurityDesc::GetGroup](#getgroup)|擷取安全性描述元中的主要群組資訊。|  
|[CSecurityDesc::GetOwner](#getowner)|擷取安全性描述元擁有者資訊。|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|傳回的指標**SECURITY_DESCRIPTOR**結構。|  
|[CSecurityDesc::GetSacl](#getsacl)|擷取安全性描述元的系統存取控制清單 (SACL) 資訊。|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|決定是否 DACL 已設定為支援自動傳播。|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|決定是否已使用預設的 DACL 的安全性描述元。|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|判斷安全性描述元是否包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|決定是否 DACL 設定成避免修改。|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|決定是否預設已設定的安全性描述元群組安全性識別碼 (SID)。|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|決定是否預設已設定的安全性描述元擁有者 SID。|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|決定是否 SACL 設定為支援自動傳播。|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|判斷安全性描述元是否設定預設的 SACL。|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|判斷安全性描述元是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|決定是否設定成以防止修改的 SACL。|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|決定是否自我相關格式的安全性描述元。|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|呼叫這個方法來將安全性描述元轉換成絕對格式。|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|呼叫這個方法來將安全性描述元轉換成自我關聯的格式。|  
|[CSecurityDesc::SetControl](#setcontrol)|設定安全性描述元的控制位元。|  
|[CSecurityDesc::SetDacl](#setdacl)|設定 DACL 中的資訊。 如果已經存在的安全性描述元中 DACL，則會取代它。|  
|[CSecurityDesc::SetGroup](#setgroup)|設定絕對格式安全性描述元，以取代任何現有的主要群組資訊的主要群組資訊。|  
|[CSecurityDesc::SetOwner](#setowner)|設定絕對格式安全性描述元，以取代任何已存在的擁有者資訊的擁有者資訊。|  
|[CSecurityDesc::SetSacl](#setsacl)|設定的 SACL 中的資訊。 如果已經存在的安全性描述元中 SACL，它會取代它。|  
|[CSecurityDesc::ToString](#tostring)|將安全性描述元轉換成字串格式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|傳回的指標**SECURITY_DESCRIPTOR**結構。|  
|[CSecurityDesc::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 **SECURITY_DESCRIPTOR**結構包含與物件相關聯的安全性資訊。 應用程式會使用此結構來設定和查詢物件的安全性狀態。 另請參閱[AtlGetSecurityDescriptor](http://msdn.microsoft.com/library/233578b8-dcc5-4f51-8e62-7cdcc2ff6b11)。  
  
 應用程式不應該修改**SECURITY_DESCRIPTOR**結構直接，而應該使用類別提供的方法。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="a-namecsecuritydesca--csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 建構函式。  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CSecurityDesc`物件或**SECURITY_DESCRIPTOR**結構以指派給新`CSecurityDesc`物件。  
  
### <a name="remarks"></a>備註  
 `CSecurityDesc`物件可以選擇性地建立使用**SECURITY_DESCRIPTOR**結構或先前定義`CSecurityDesc`物件。  
  
##  <a name="a-namedtora--csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 解構函式。  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放所有配置的資源。  
  
##  <a name="a-namefromstringa--csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::FromString  
 將字串格式的安全性描述元轉換成有效、 功能安全性描述元。  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 以 null 終止的字串，其中包含指標[字串格式的安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379570)轉換。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true。 失敗時擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 可以使用建立的字串[CSecurityDesc::ToString](#tostring)。 將安全性描述元轉換成字串，可讓您更輕鬆地儲存和傳輸。  
  
 這個方法只適用於 Windows 2000 和更新版本因為它會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
##  <a name="a-namegetcontrola--csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::GetControl  
 擷取控制從安全性描述元的資訊。  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>參數  
 *psdc*  
 指標**SECURITY_DESCRIPTOR_CONTROL**接收的安全性描述元控制資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 失敗時傳回 true。  
  
### <a name="remarks"></a>備註  
 這個方法才有意義，當使用 Windows 2000 或更新版本，因為它會呼叫[GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647)。  
  
##  <a name="a-namegetdacla--csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl  
 擷取安全性描述元的判別存取控制清單 (DACL) 資訊。  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pDacl`  
 指標`CDacl`結構，用來儲存一份 DACL 的安全性描述元。 如果判別**ACL**存在，方法會設定`pDacl`位址的安全性描述元的判別**ACL**。 如果判別**ACL**不存在，會儲存任何值。  
  
 `pbPresent`  
 指標值，指出是否存在判別**ACL**中指定的安全性描述元。 如果安全性描述元包含判別**ACL**，此參數設為 true。 如果沒有判別安全性描述元**ACL**，此參數設定為 false。  
  
 `pbDefaulted`  
 中的 SE_DACL_DEFAULTED 旗標值的一組旗標指標**SECURITY_DESCRIPTOR_CONTROL**結構如果判別**ACL**存在的安全性描述元。 如果這個旗標為 true，判別**ACL**所擷取預設的機制; 如果為 false，判別**ACL**已由使用者明確指定。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 失敗時傳回 true。  
  
##  <a name="a-namegetgroupa--csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::GetGroup  
 擷取安全性描述元中的主要群組資訊。  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼），會收到一份儲存 CDacl 中的群組。  
  
 `pbDefaulted`  
 中的 SE_GROUP_DEFAULTED 旗標值的一組旗標指標**SECURITY_DESCRIPTOR_CONTROL**結構方法傳回時。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 失敗時傳回 true。  
  
##  <a name="a-namegetownera--csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::GetOwner  
 擷取安全性描述元擁有者資訊。  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid](../../atl/reference/csid-class.md) （安全性識別碼），會收到一份儲存 CDacl 中的群組。  
  
 `pbDefaulted`  
 中的 SE_OWNER_DEFAULTED 旗標值的一組旗標指標**SECURITY_DESCRIPTOR_CONTROL**結構方法傳回時。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 失敗時傳回 true。  
  
##  <a name="a-namegetpsecuritydescriptora--csecuritydescgetpsecuritydescriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 傳回的指標**SECURITY_DESCRIPTOR**結構。  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的指標[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)結構。  
  
##  <a name="a-namegetsacla--csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl  
 擷取安全性描述元的系統存取控制清單 (SACL) 資訊。  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSacl`  
 指標`CSacl`結構，用來儲存一份安全性描述元的 SACL。 如果系統**ACL**存在，方法會設定`pSacl`的安全性描述元的系統位址**ACL**。 如果系統**ACL**不存在，會儲存任何值。  
  
 `pbPresent`  
 這個方法會設定指出系統的目前狀態的旗標的指標**ACL**中指定的安全性描述元。 如果安全性描述元包含系統**ACL**，此參數設為 true。 如果安全性描述元不包含系統**ACL**，此參數設定為 false。  
  
 `pbDefaulted`  
 中的 SE_SACL_DEFAULTED 旗標值的一組旗標指標**SECURITY_DESCRIPTOR_CONTROL**結構，如果系統**ACL**存在的安全性描述元。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 失敗時傳回 true。  
  
##  <a name="a-nameisdaclautoinheriteda--csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 決定是否判別存取控制清單 (DACL) 設定為支援自動傳播。  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含 DACL，這設定為支援自動傳播到現有的子物件的可繼承的存取控制項目 (Ace)，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 它會執行自動繼承演算法的物件和其現有的子物件時，系統會設定這個位元。  
  
##  <a name="a-nameisdacldefaulteda--csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 決定是否設定成以預設的判別存取控制清單 (DACL) 的安全性描述元。  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含預設的 DACL，false 否則會傳回 true。  
  
### <a name="remarks"></a>備註  
 這個旗標可能會影響系統如何處理 DACL，相對於存取控制項目 (ACE) 繼承。 例如，如果物件的建立者未指定 DACL，物件會接收預設 DACL 來自建立者的存取權杖。 如果未設定 SE_DACL_PRESENT 旗標，系統會忽略此旗標。  
  
 這個旗標用來判斷物件的最終 DACL 的計算方式，而且不會儲存實際在安全性實體物件的安全性描述元控制。  
  
 若要設定此旗標，使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
##  <a name="a-nameisdaclpresenta--csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 判斷安全性描述元是否包含判別存取控制清單 (DACL)。  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含 DACL，false 否則傳回 true。  
  
### <a name="remarks"></a>備註  
 如果未設定此旗標，或如果設定此旗標，而 DACL 是 NULL，安全性描述元可讓所有人都能完整存取權。  
  
 這個旗標用來保存的安全性描述元的安全性實體物件相關聯之前，呼叫端所指定的安全性資訊。 一旦與安全性實體物件相關聯的安全性描述元，SE_DACL_PRESENT 旗標一定會設定安全性描述元控制項中。  
  
 若要設定此旗標，使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
##  <a name="a-nameisdaclprotecteda--csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected  
 決定是否判別存取控制清單 (DACL) 為了避免修改設定。  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果 DACL 設定為防止修改由繼承的存取控制項目 (Ace) 的安全性描述元，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[CSecurityDesc::SetDacl](#setdacl)方法。  
  
 這個方法才有意義的 Windows 2000 或更新版本中，只有 Windows 2000 支援自動傳播的可繼承的 Ace。  
  
##  <a name="a-nameisgroupdefaulteda--csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 決定是否預設已設定的安全性描述元群組安全性識別碼 (SID)。  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元，群組 SID，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[CSecurityDesc::SetGroup](#setgroup)方法。  
  
##  <a name="a-nameisownerdefaulteda--csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 決定是否預設已設定的安全性描述元擁有者安全性識別碼 (SID)。  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果預設的機制，而不是原始的提供者的安全性描述元，提供的安全性描述元擁有者 SID，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[CSecurityDesc::SetOwner](#setowner)方法。  
  
##  <a name="a-nameissaclautoinheriteda--csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 決定系統存取控制清單 (SACL) 是否設定為支援自動傳播。  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含某個設定以支援自動傳播到現有的子物件的可繼承的存取控制項目 (Ace)，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 它會執行自動繼承演算法的物件和其現有的子物件時，系統會設定這個位元。  
  
##  <a name="a-nameissacldefaulteda--csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 決定是否設定成以預設的系統存取控制清單 (SACL) 的安全性描述元。  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含預設的 SACL，false 否則會傳回 true。  
  
### <a name="remarks"></a>備註  
 這個旗標可能會影響系統如何處理 SACL，相對於存取控制項目 (ACE) 繼承。 如果未設定 SE_SACL_PRESENT 旗標，系統會忽略此旗標。  
  
 若要設定此旗標，使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
##  <a name="a-nameissaclpresenta--csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 判斷安全性描述元是否包含系統存取控制清單 (SACL)。  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元包含 SACL，false 否則傳回 true。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
##  <a name="a-nameissaclprotecteda--csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 決定是否設定成以防止修改的系統存取控制清單 (SACL)。  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果 SACL 設定為防止修改由繼承的存取控制項目 (Ace) 的安全性描述元，則傳回 true。 否則會傳回 False。  
  
### <a name="remarks"></a>備註  
 若要設定此旗標，使用[CSecurityDesc::SetSacl](#setsacl)方法。  
  
 這個方法才有意義的 Windows 2000 或更新版本中，只有 Windows 2000 支援自動傳播的可繼承的 Ace。  
  
##  <a name="a-nameisselfrelativea--csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 決定是否自我相關格式的安全性描述元。  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果安全性描述元中自我相關格式與連續的記憶體區塊中的所有安全性資訊，則傳回 true。 如果安全性描述元是絕對格式，就會傳回 false。 如需詳細資訊，請參閱[絕對及 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="a-namemakeabsolutea--csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 呼叫這個方法來將安全性描述元轉換成絕對格式。  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 否則傳回 true。  
  
### <a name="remarks"></a>備註  
 絕對格式的安全性描述元包含它所包含的資訊，而不是本身的資訊的指標。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中**SECURITY_DESCRIPTOR**結構永遠會啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用的記憶體位址，自我關聯的安全性描述元的元件會識別的安全性描述元開頭的位移。 必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元時，此格式會很有用。 如需詳細資訊，請參閱[絕對及 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="a-namemakeselfrelativea--csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 呼叫這個方法來將安全性描述元轉換成自我關聯的格式。  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，false 否則傳回 true。  
  
### <a name="remarks"></a>備註  
 絕對格式的安全性描述元包含它所包含的資訊，而不是包含資訊本身的指標。 自我相關格式的安全性描述元包含連續的記憶體區塊中的資訊。 自我關聯的安全性描述元中**SECURITY_DESCRIPTOR**結構永遠會啟動的詳細資訊，但安全性描述元的其他元件可以依照任何順序中的結構。 而不是使用的記憶體位址，從安全性描述元開頭的位移被識別元件的安全性描述元。 必須儲存在磁碟上或透過通訊協定傳輸的安全性描述元時，此格式會很有用。 如需詳細資訊，請參閱[絕對及 Self-Relative 安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa374807)。  
  
##  <a name="a-nameoperatoreqa--csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::operator =  
 指派運算子。  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 **SECURITY_DESCRIPTOR**結構或`CSecurityDesc`物件指派給`CSecurityDesc`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CSecurityDesc`物件。  
  
##  <a name="a-nameoperatorconstsecuritydescriptorstara--csecuritydescoperator-const-securitydescriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 將指標值轉換**SECURITY_DESCRIPTOR**結構。  
  
```  
operator const SECURITY_DESCRIPTOR *() const throw();
```  
  
##  <a name="a-namesetcontrola--csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::SetControl  
 設定安全性描述元的控制位元。  
  
```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```  
  
### <a name="parameters"></a>參數  
 `ControlBitsOfInterest`  
 A **SECURITY_DESCRIPTOR_CONTROL**指出若要設定之控制位元遮罩。 如需可設定的旗標的清單，請參閱[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
 `ControlBitsToSe`t  
 `SECURITY_DESCRIPTOR_CONTROL` 遮罩，表示 `ControlBitsOfInterest` 遮罩所指定控制位元的新值。 此參數可以是針對 `ControlBitsOfInterest` 參數所列出旗標的組合。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法，便可以只在 Windows 2000 及更新版本，它會呼叫[SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx)。  
  
##  <a name="a-namesetdacla--csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl  
 判別存取控制清單 (DACL) 中設定資訊。 如果已經存在的安全性描述元中 DACL，則會取代它。  
  
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
 若要參考`CDacl`物件，指定的 DACL 的安全性描述元。 此參數不得為 NULL。 若要設定安全性描述元中的 NULL DACL，第一種形式的方法必須搭配`bPresent`設為 false。  
  
 `bPresent`  
 指定旗標，表示 DACL 的安全性描述元中的目前狀態。 如果此參數為 true，則方法會設定 SE_DACL_PRESENT 旗標**SECURITY_DESCRIPTOR_CONTROL**結構，並使用中的值*Dacl*和`bDefaulted`參數。 如果為 false，方法會清除 SE_DACL_PRESENT 旗標和`bDefaulted`會被忽略。  
  
 `bDefaulted`  
 指定旗標，表示來源的 DACL。 如果這個旗標為 true，DACL 已擷取的一些預設的機制。 如果為 false，DACL 已明確指定的使用者。 方法會將此值儲存在 SE_DACL_DEFAULTED 旗標為**SECURITY_DESCRIPTOR_CONTROL**結構。 如果未指定此參數，則會清除 SE_DACL_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 沒有空白並不存在的 DACL 的重要差異。 DACL 是空的當它包含沒有存取控制的項目，並沒有存取權限已明確授與。 如此一來，會隱含拒絕物件的存取權。 當物件有沒有 DACL 時，相反地，沒有任何保護指派給物件，並授與存取權的任何要求。  
  
##  <a name="a-namesetgroupa--csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup  
 設定絕對格式安全性描述元，以取代任何現有的主要群組資訊的主要群組資訊。  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `Sid`  
 若要參考[CSid](../../atl/reference/csid-class.md)的安全性描述元的新主要群組的物件。 此參數不得為 NULL。 安全性描述元可以標示為不具有 DACL 或 SACL，但是它必須擁有群組和擁有者，這些甚至會 NULL SID （這是具有特殊意義的內建 SID）。  
  
 `bDefaulted`  
 表示主要群組資訊是否衍生自預設機制。 如果此值為 true，它是預設的詳細資訊，而且方法會將這個值儲存為 SE_GROUP_DEFAULTED 旗標**SECURITY_DESCRIPTOR_CONTROL**結構。 如果此參數為零，則會清除 SE_GROUP_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namesetownera--csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner  
 設定絕對格式安全性描述元的擁有者資訊。 它會取代任何現有的擁有者資訊。  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `Sid`  
 [CSid](../../atl/reference/csid-class.md)安全性描述元的新主要擁有者的物件。 此參數不得為 NULL。  
  
 `bDefaulted`  
 指出是否要將擁有者資訊衍生自預設機制。 如果此值為 true，則預設資訊。 方法會將這個值儲存為 SE_OWNER_DEFAULTED 旗標**SECURITY_DESCRIPTOR_CONTROL**結構。 如果此參數為零，則會清除 SE_OWNER_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namesetsacla--csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl  
 設定系統存取控制清單 (SACL) 中的資訊。 如果已經存在的安全性描述元中 SACL，它會取代它。  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *Sacl*  
 指標`CSacl`物件，指定的安全性描述元的 SACL。 這個參數不可以是 NULL，，而且必須是 CSacl 物件。 不同於 Dacl，並無差別之間 NULL 和空的 SACL，如 SACL 物件未指定存取權限，只稽核資訊。  
  
 `bDefaulted`  
 指定旗標，表示 SACL 的來源。 如果這個旗標為 true，SACL 已擷取的一些預設的機制。 如果為 false，SACL 已明確指定的使用者。 方法會將此值儲存在 SE_SACL_DEFAULTED 旗標為**SECURITY_DESCRIPTOR_CONTROL**結構。 如果未指定此參數，則會清除 SE_SACL_DEFAULTED 旗標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-nametostringa--csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString  
 將安全性描述元轉換成字串格式。  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 以 null 終止的字串可接收指標[字串格式的安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379570)。  
  
 `si`  
 指定 SECURITY_INFORMATION 位元旗標，表示要包含在輸出字串中的安全性描述元元件的組合。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 字串格式的安全性描述元之後，它可以更輕鬆地儲存或傳輸。 使用`CSecurityDesc::FromString`方法，將字串轉換成安全性描述元。  
  
 `si`參數可以包含下列 SECURITY_INFORMATION 旗標︰  
  
|值|意義|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|包含擁有者。|  
|GROUP_SECURITY_INFORMATION|包含主要群組。|  
|DACL_SECURITY_INFORMATION|包括 DACL。|  
|SACL_SECURITY_INFORMATION|包括 SACL。|  
  
 DACL 是 NULL，且 SE_DACL_PRESENT 控制位元設定在輸入的安全性描述元，如果方法失敗。  
  
 DACL 是 NULL，且 SE_DACL_PRESENT 控制位元未設定輸入的安全性描述元中，如果產生的安全性描述元字串中沒有 d︰ 元件。 請參閱[安全性描述元字串格式](http://msdn.microsoft.com/library/windows/desktop/aa379570)如需詳細資訊。  
  
 這個方法只適用於 Windows 2000 和更新版本中，因為它會呼叫[ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401)。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)

