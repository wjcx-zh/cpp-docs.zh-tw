---
title: "Security Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ACL object global functions"
  - "security IDs [C++]"
  - "SIDs [C++], modifying SID objects"
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Security Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式會修改 SID 和 ACL 物件的支援。  
  
> [!IMPORTANT]
>  下表中列出的函式不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
|||  
|-|-|  
|[AtlGetDacl](../Topic/AtlGetDacl.md)|呼叫這個函式會擷取指定物件的 Discretionary 存取控制清單 \(DACL\) \(DACL\) 資訊。|  
|[AtlSetDacl](../Topic/AtlSetDacl.md)|呼叫這個函式會將指定物件的 Discretionary 存取控制清單 \(DACL\) \(DACL\) 資訊。|  
|[AtlGetGroupSid](../Topic/AtlGetGroupSid.md)|呼叫這個函式會擷取物件的群組安全識別項 \(Locale Identifier \(SID\)。|  
|[AtlSetGroupSid](../Topic/AtlSetGroupSid.md)|呼叫這個函式會設定物件的群組安全識別項 \(Locale Identifier \(SID\)。|  
|[AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md)|呼叫這個函式會擷取物件的擁有人 Security Identifier \(SID\)。|  
|[AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md)|呼叫這個函式會設定物件的擁有人 Security Identifier \(SID\)。|  
|[AtlGetSacl](../Topic/AtlGetSacl.md)|呼叫這個函式會擷取指定物件的系統存取控制清單 \(SACL\) \(SACL\) 資訊。|  
|[AtlSetSacl](../Topic/AtlSetSacl.md)|呼叫這個函式會將指定物件的系統存取控制清單 \(SACL\) \(SACL\) 資訊。|  
|[AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md)|呼叫這個函式會擷取指定物件的安全性描述元。|  
  
## 請參閱  
 [函式](../../atl/reference/atl-functions.md)