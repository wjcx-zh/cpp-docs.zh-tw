---
title: "CSecurityAttributes Class | Microsoft Docs"
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
  - "ATL.CSecurityAttributes"
  - "ATL::CSecurityAttributes"
  - "CSecurityAttributes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSecurityAttributes class"
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSecurityAttributes Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是安全屬性架構的小型包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CSecurityAttributes : public SECURITY_ATTRIBUTES  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSecurityAttributes::CSecurityAttributes](../Topic/CSecurityAttributes::CSecurityAttributes.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSecurityAttributes::Set](../Topic/CSecurityAttributes::Set.md)|呼叫這個方法會設定 `CSecurityAttributes` 物件的屬性。|  
  
## 備註  
 **SECURITY\_ATTRIBUTES** 結構包含可用來建立物件的 [安全性描述元。](http://msdn.microsoft.com/library/windows/desktop/aa379561) 並指定要擷取的處理這個結構是否為可繼承的。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 繼承階層架構  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [security descriptor](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)