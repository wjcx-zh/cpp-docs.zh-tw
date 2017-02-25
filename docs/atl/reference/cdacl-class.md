---
title: "CDacl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDacl"
  - "CDacl"
  - "ATL.CDacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDacl class"
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CDacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 DACL \(Discretionary 存取控制清單 \(DACL\)\) 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CDacl : public CAcl  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDacl::CDacl](../Topic/CDacl::CDacl.md)|建構函式。|  
|[CDacl::~CDacl](../Topic/CDacl::~CDacl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDacl::AddAllowedAce](../Topic/CDacl::AddAllowedAce.md)|加入允許的 ACE \(存取控制項目\) 加入 `CDacl` 物件。|  
|[CDacl::AddDeniedAce](../Topic/CDacl::AddDeniedAce.md)|將拒絕的 ACE 至 `CDacl` 物件。|  
|[CDacl::GetAceCount](../Topic/CDacl::GetAceCount.md)|傳回一個點 \(存取控制項目\) 的數目。 `CDacl` 物件。|  
|[CDacl::RemoveAce](../Topic/CDacl::RemoveAce.md)|從移除特定物件 `CDacl` ACE \(存取控制項目\)。|  
|[CDacl::RemoveAllAces](../Topic/CDacl::RemoveAllAces.md)|移除在 `CDacl` 物件中所包含的任何一個點。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CDacl::operator \=](../Topic/CDacl::operator%20=.md)|指派運算子。|  
  
## 備註  
 物件的安全性描述元可包含 DACL。  DACL 包含識別使用者和群組可以存取物件的零或多個點 \(存取控制項目\)。  如果 DACL 是空的 \(也就是包含零的 ACE\)，不會明確授與存取權，因此，存取隱含拒絕。  不過，在中，如果物件的安全性描述元沒有 DACL，物件未受到保護，而且每個人都可以存取完整。  
  
 要擷取的物件之 DACL，您必須是物件的擁有人或存取物件的 READ\_CONTROL。  若要變更物件的 DACL，您必須可以存取物件的 WRITE\_DAC 存取。  
  
 使用類別提供的方法建立，加入、移除，，，然後從 `CDacl` 刪除 ACE 的物件。  請參閱 [AtlGetDacl](../Topic/AtlGetDacl.md) 和 [AtlSetDacl](../Topic/AtlSetDacl.md)。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 繼承階層架構  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)