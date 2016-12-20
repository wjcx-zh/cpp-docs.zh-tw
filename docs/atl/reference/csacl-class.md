---
title: "CSacl Class | Microsoft Docs"
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
  - "ATL.CSacl"
  - "ATL::CSacl"
  - "CSacl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSacl class"
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSacl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 SACL \(系統存取控制清單 \(SACL\)\) 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CSacl : public CAcl  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSacl::CSacl](../Topic/CSacl::CSacl.md)|建構函式。|  
|[CSacl::~CSacl](../Topic/CSacl::~CSacl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSacl::AddAuditAce](../Topic/CSacl::AddAuditAce.md)|將稽核存取控制項目 \(ACE\) 加入 `CSacl` \(ACE\) 物件。|  
|[CSacl::GetAceCount](../Topic/CSacl::GetAceCount.md)|傳回存取控制項目 \(ACE\) \(ACEs\) 的數目。 `CSacl` 物件的。|  
|[CSacl::RemoveAce](../Topic/CSacl::RemoveAce.md)|從移除特定物件 **CSacl** ACE \(存取控制項目\)。|  
|[CSacl::RemoveAllAces](../Topic/CSacl::RemoveAllAces.md)|移除在 `CSacl` 物件中所包含的任何一個點。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSacl::operator \=](../Topic/CSacl::operator%20=.md)|指派運算子。|  
  
## 備註  
 指定 SACL 包含存取嘗試的型別會在網域控制站的安全性事件記錄檔的稽核記錄的存取控制項目 \(ACE\) \(ACEs\)。  請注意 SACL 在嘗試存取時發生的網域控制站只會產生記錄項目，而不是包含物件的複本之每個網域控制站。  
  
 要設定或擷取物件中的安全性描述元的 SACL，在要求之執行緒的 Access Token 必須啟用 SE\_SECURITY\_NAME 權限。  具有這個使用權限依預設會授權系統管理員群組，，且可以授與其他使用者或群組。  具有這個使用權限授與任何不需要的:在這個使用權限定義的作業可以在上執行之前，在安全性存取語彙基元必須啟用這個使用權限才能正常運作。  這個模型可讓權限、特定的作業系統才會啟用，則會將它們停用時不再需要。  請參閱 [AtlGetSacl](../Topic/AtlGetSacl.md) 和 [AtlSetSacl](../Topic/AtlSetSacl.md) 進行 SE\_SECURITY\_NAME 的範例。  
  
 使用提供的類別方法，將物件從 **SACL** 移除，建立和刪除一個點。  請參閱 [AtlGetSacl](../Topic/AtlGetSacl.md) 和 [AtlSetSacl](../Topic/AtlSetSacl.md)。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 繼承階層架構  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [CAcl Class](../../atl/reference/cacl-class.md)   
 [ACLs](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [ACEs](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)