---
title: "CSid Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSid"
  - "ATL::CSid"
  - "ATL.CSid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSid class"
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSid Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 `SID` \(Security Identifier\) 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CSid  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CSid::CSidArray](../Topic/CSid::CSidArray.md)|`CSid` 物件的陣列。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSid::CSid](../Topic/CSid::CSid.md)|建構函式。|  
|[CSid::~CSid](../Topic/CSid::~CSid.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSid::AccountName](../Topic/CSid::AccountName.md)|傳回這個帳戶的名稱與 `CSid` 物件。|  
|[CSid::Domain](../Topic/CSid::Domain.md)|傳回網域名稱與 `CSid` 物件。|  
|[CSid::EqualPrefix](../Topic/CSid::EqualPrefix.md)|用於相等測試 `SID` \(Security Identifier\) 前置詞。|  
|[CSid::GetLength](../Topic/CSid::GetLength.md)|傳回 `CSid` 物件的長度。|  
|[CSid::GetPSID](../Topic/CSid::GetPSID.md)|傳回指向 `SID` 結構。|  
|[CSid::GetPSID\_IDENTIFIER\_AUTHORITY](../Topic/CSid::GetPSID_IDENTIFIER_AUTHORITY.md)|傳回指向 **SID\_IDENTIFIER\_AUTHORITY** 結構。|  
|[CSid::GetSubAuthority](../Topic/CSid::GetSubAuthority.md)|傳回在 **SID** 結構的指定 subauthority。|  
|[CSid::GetSubAuthorityCount](../Topic/CSid::GetSubAuthorityCount.md)|傳回 subauthority 計數。|  
|[CSid::IsValid](../Topic/CSid::IsValid.md)|的有效性測試 `CSid` 物件。|  
|[CSid::LoadAccount](../Topic/CSid::LoadAccount.md)|更新 `CSid` 物件指定的帳戶名稱和網域或現有 `SID` 結構。|  
|[CSid::Sid](../Topic/CSid::Sid.md)|傳回 ID 字串。|  
|[CSid::SidNameUse](../Topic/CSid::SidNameUse.md)|傳回 `CSid` 物件狀態的描述。|  
  
### 運算子  
  
|||  
|-|-|  
|[\=運算子](../Topic/CSid::operator%20=.md)|指派運算子。|  
|[運算子 const SID \*](../Topic/CSid::operator%20const%20SID%20*.md)|將物件轉換成指標的 `CSid` 物件 `SID` 結構。|  
  
### 全域運算子  
  
|||  
|-|-|  
|[運算子\=\=](../Topic/CSid::operator%20==.md)|測試是否相等的兩個安全性描述元物件|  
|[運算子\! \=](../Topic/CSid::operator%20!=.md)|測試兩個不相等的安全性描述元物件|  
|[運算子\<](../Topic/CSid::operator%20%3C.md)|比較兩個安全性描述元物件的相對值。|  
|[運算子\>](../Topic/CSid::operator%20%3E.md)|比較兩個安全性描述元物件的相對值。|  
|[運算子\<\=](../Topic/CSid::operator%20%3C=.md)|比較兩個安全性描述元物件的相對值。|  
|[運算子\>\=](../Topic/CSid::operator%20%3E=.md)|比較兩個安全性描述元物件的相對值。|  
  
## 備註  
 `SID` 結構是一可變長度的結構唯一識別使用者或群組。  
  
 應用程式在包裝函式類別不應該直接修改 `SID` 結構，，而是使用提供的方法。  請參閱 [AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md)、 [AtlSetGroupSid](../Topic/AtlSetGroupSid.md)、 [AtlGetGroupSid](../Topic/AtlGetGroupSid.md)和 [AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md)。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [Operators Alphabetical Reference](../../atl/reference/atl-operators.md)