---
title: "CPrivateObjectSecurityDesc Class | Microsoft Docs"
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
  - "ATL.CPrivateObjectSecurityDesc"
  - "ATL::CPrivateObjectSecurityDesc"
  - "CPrivateObjectSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrivateObjectSecurityDesc class"
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrivateObjectSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示私用物件安全性描述元物件。  
  
## 語法  
  
```  
  
class CPrivateObjectSecurityDesc : public CSecurityDesc  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc.md)|建構函式。|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](../Topic/CPrivateObjectSecurityDesc::ConvertToAutoInherit.md)|呼叫這個方法轉換為安全性描述元和它的存取控制清單 \(ACL\) \(ACLs\) 為支援可繼承的存取控制項目 \(ACE\) \(ACEs\) 會自動傳用的格式。|  
|[CPrivateObjectSecurityDesc::Create](../Topic/CPrivateObjectSecurityDesc::Create.md)|呼叫這個方法會配置並初始化呼叫資源管理員建立的私用物件的自我相關安全性描述元。|  
|[CPrivateObjectSecurityDesc::Get](../Topic/CPrivateObjectSecurityDesc::Get.md)|呼叫這個方法會從私用物件的安全性描述元中擷取資訊。|  
|[CPrivateObjectSecurityDesc::Set](../Topic/CPrivateObjectSecurityDesc::Set.md)|呼叫這個方法來修改私用物件的安全性描述元。|  
  
### 運算子  
  
|||  
|-|-|  
|[\=運算子](../Topic/CPrivateObjectSecurityDesc::operator%20=.md)|指派運算子。|  
  
## 備註  
 這個類別是衍生自， [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，用於建立及管理私用物件的安全性描述元的方法。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 繼承階層架構  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc Class](../../atl/reference/csecuritydesc-class.md)