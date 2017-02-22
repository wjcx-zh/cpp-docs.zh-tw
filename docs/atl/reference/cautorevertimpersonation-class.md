---
title: "CAutoRevertImpersonation Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoRevertImpersonation"
  - "CAutoRevertImpersonation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoRevertImpersonation class"
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CAutoRevertImpersonation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會在超出範圍時，這個類別會還原至 nonimpersonating 狀態的 [CAccessToken](../../atl/reference/caccesstoken-class.md) 物件。  
  
## 語法  
  
```  
  
class CAutoRevertImpersonation  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::CAutoRevertImpersonation.md)|建構 `CAutoRevertImpersonation` 物件|  
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::~CAutoRevertImpersonation.md)|終結物件並還原存取語彙基元模擬。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAutoRevertImpersonation::Attach](../Topic/CAutoRevertImpersonation::Attach.md)|Automation 存取語彙基元模擬還原信號。|  
|[CAutoRevertImpersonation::Detach](../Topic/CAutoRevertImpersonation::Detach.md)|取消自動被模擬。|  
|[CAutoRevertImpersonation::GetAccessToken](../Topic/CAutoRevertImpersonation::GetAccessToken.md)|擷取存取語彙基元目前這個物件相關聯的。|  
  
## 備註  
 [存取語彙基元](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述處理序或執行緒的安全性內容的物件和配置給每一位使用者都會記錄在 Windows NT 或 Windows 2000 系統上。  這些存取語彙基元可以用 `CAccessToken` 類別表示。  
  
 模擬存取語彙基元有時候是必要的。  這個類別是為了方便使用，不過，它不會實作存取語彙基元模擬;它只有在執行自動還原信號至 nonimpersonated 狀態。  這是因為，語彙基元存取模擬可以執行幾種不同的方式。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [ATLSecurity 範例](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)