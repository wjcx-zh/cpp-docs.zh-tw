---
title: "CSecurityDesc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSecurityDesc"
  - "ATL.CSecurityDesc"
  - "CSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSecurityDesc class"
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 **SECURITY\_DESCRIPTOR** 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CSecurityDesc  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSecurityDesc::CSecurityDesc](../Topic/CSecurityDesc::CSecurityDesc.md)|建構函式。|  
|[CSecurityDesc::~CSecurityDesc](../Topic/CSecurityDesc::~CSecurityDesc.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSecurityDesc::FromString](../Topic/CSecurityDesc::FromString.md)|將字串轉換為安全性描述元格式輸入有效的功能，安全性描述元。|  
|[CSecurityDesc::GetControl](../Topic/CSecurityDesc::GetControl.md)|從安全性描述元擷取控制項資訊。|  
|[CSecurityDesc::GetDacl](../Topic/CSecurityDesc::GetDacl.md)|從安全性描述元擷取 Discretionary 存取控制清單 \(DACL\) \(DACL\) 資訊。|  
|[CSecurityDesc::GetGroup](../Topic/CSecurityDesc::GetGroup.md)|從安全性描述元擷取主要群組資訊。|  
|[CSecurityDesc::GetOwner](../Topic/CSecurityDesc::GetOwner.md)|從安全性描述元擷取擁有者 informaton。|  
|[CSecurityDesc::GetPSECURITY\_DESCRIPTOR](../Topic/CSecurityDesc::GetPSECURITY_DESCRIPTOR.md)|傳回指向 **SECURITY\_DESCRIPTOR** 結構。|  
|[CSecurityDesc::GetSacl](../Topic/CSecurityDesc::GetSacl.md)|從安全性描述元擷取系統存取控制清單 \(SACL\) \(SACL\) 資訊。|  
|[CSecurityDesc::IsDaclAutoInherited](../Topic/CSecurityDesc::IsDaclAutoInherited.md)|判斷是否已設定 DACL 支援自動傳用。|  
|[CSecurityDesc::IsDaclDefaulted](../Topic/CSecurityDesc::IsDaclDefaulted.md)|決定安全性描述元是否已設定為使用預設的 DACL。|  
|[CSecurityDesc::IsDaclPresent](../Topic/CSecurityDesc::IsDaclPresent.md)|決定安全性描述元是否包含 DACL。|  
|[CSecurityDesc::IsDaclProtected](../Topic/CSecurityDesc::IsDaclProtected.md)|判斷是否已設定 DACL 防止修改。|  
|[CSecurityDesc::IsGroupDefaulted](../Topic/CSecurityDesc::IsGroupDefaulted.md)|決定安全性描述元的群組安全識別項 \(Locale Identifier \(SID\) 預設是否設定為。|  
|[CSecurityDesc::IsOwnerDefaulted](../Topic/CSecurityDesc::IsOwnerDefaulted.md)|決定安全性描述元的擁有人的 SID 預設是否設定為。|  
|[CSecurityDesc::IsSaclAutoInherited](../Topic/CSecurityDesc::IsSaclAutoInherited.md)|判斷是否將 SACL 支援自動傳用。|  
|[CSecurityDesc::IsSaclDefaulted](../Topic/CSecurityDesc::IsSaclDefaulted.md)|決定安全性描述元是否搭配預設 SACL。|  
|[CSecurityDesc::IsSaclPresent](../Topic/CSecurityDesc::IsSaclPresent.md)|決定安全性描述元是否包含 SACL。|  
|[CSecurityDesc::IsSaclProtected](../Topic/CSecurityDesc::IsSaclProtected.md)|判斷是否將 SACL 防止修改。|  
|[CSecurityDesc::IsSelfRelative](../Topic/CSecurityDesc::IsSelfRelative.md)|決定安全性描述元是否在自我相關格式。|  
|[CSecurityDesc::MakeAbsolute](../Topic/CSecurityDesc::MakeAbsolute.md)|呼叫這個方法轉換為安全性描述元加入至絕對格式。|  
|[CSecurityDesc::MakeSelfRelative](../Topic/CSecurityDesc::MakeSelfRelative.md)|呼叫這個方法會轉換為安全性描述元自我相關格式。|  
|[CSecurityDesc::SetControl](../Topic/CSecurityDesc::SetControl.md)|設定安全性描述元的控制項欄位。|  
|[CSecurityDesc::SetDacl](../Topic/CSecurityDesc::SetDacl.md)|設定在 DACL 中的資訊。  如果 DACL 已在安全性描述元，它已經被取代。|  
|[CSecurityDesc::SetGroup](../Topic/CSecurityDesc::SetGroup.md)|設定絕對格式安全性描述元的主要群組資訊，已經取代所有主要群組資訊存在。|  
|[CSecurityDesc::SetOwner](../Topic/CSecurityDesc::SetOwner.md)|設定絕對格式安全性描述元的擁有人資訊，已經取代所有擁有者資訊存在。|  
|[CSecurityDesc::SetSacl](../Topic/CSecurityDesc::SetSacl.md)|設定在 SACL 中的資訊。  如果 SACL 已在安全性描述元，它已經被取代。|  
|[CSecurityDesc::ToString](../Topic/CSecurityDesc::ToString.md)|轉換安全性描述元的字串格式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSecurityDesc::operator const SECURITY\_DESCRIPTOR \*](../Topic/CSecurityDesc::operator%20const%20SECURITY_DESCRIPTOR%20*.md)|傳回指向 **SECURITY\_DESCRIPTOR** 結構。|  
|[CSecurityDesc::operator \=](../Topic/CSecurityDesc::operator%20=.md)|指派運算子。|  
  
## 備註  
 **SECURITY\_DESCRIPTOR** 結構包含安全性資訊相關聯的物件。  應用程式使用此結構來設定和查詢物件的安全性狀態。  請參閱 [AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md)。  
  
 應用程式不能直接修改 **SECURITY\_DESCRIPTOR** 結構和應該使用提供的類別方法。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)