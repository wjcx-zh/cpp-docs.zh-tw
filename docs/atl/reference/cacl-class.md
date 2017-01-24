---
title: "CAcl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAcl"
  - "ATL::CAcl"
  - "ATLSECURITY/CAcl"
  - "ATL.CAcl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAcl class"
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAcl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 `ACL` \(存取控制清單 \(SACL\)\) 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAcl  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CAcl::CAccessMaskArray](../Topic/CAcl::CAccessMaskArray.md)|陣列 `ACCESS_MASK`s。|  
|[CAcl::CAceFlagArray](../Topic/CAcl::CAceFlagArray.md)|陣列 `BYTE`s。|  
|[CAcl::CAceTypeArray](../Topic/CAcl::CAceTypeArray.md)|陣列 `BYTE`s。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAcl::CAcl](../Topic/CAcl::CAcl.md)|建構函式。|  
|[CAcl::~CAcl](../Topic/CAcl::~CAcl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAcl::GetAceCount](../Topic/CAcl::GetAceCount.md)|傳回存取控制項目 \(ACE\) \(ACE\) 物件數目。|  
|[CAcl::GetAclEntries](../Topic/CAcl::GetAclEntries.md)|從 `CAcl` 物件擷取存取控制清單 \(SACL\) \(ACL\) 輸入。|  
|[CAcl::GetAclEntry](../Topic/CAcl::GetAclEntry.md)|擷取所有相關項目的相關資訊。 `CAcl` 物件。|  
|[CAcl::GetLength](../Topic/CAcl::GetLength.md)|傳回 ACL 的長度。|  
|[CAcl::GetPACL](../Topic/CAcl::GetPACL.md)|傳回 PACL ACL \(如\) 的指標。|  
|[CAcl::IsEmpty](../Topic/CAcl::IsEmpty.md)|指定輸入測試 `CAcl` 物件。|  
|[CAcl::IsNull](../Topic/CAcl::IsNull.md)|傳回 `CAcl` 物件的狀態。|  
|[CAcl::RemoveAce](../Topic/CAcl::RemoveAce.md)|從移除特定物件 `CAcl` ACE \(存取控制項目\)。|  
|[CAcl::RemoveAces](../Topic/CAcl::RemoveAces.md)|從移除 `CAcl` 適用於特定 `CSid`的任何一個點 \(存取控制項目\)。|  
|[CAcl::SetEmpty](../Topic/CAcl::SetEmpty.md)|標記 `CAcl` 物件標記為空白。|  
|[CAcl::SetNull](../Topic/CAcl::SetNull.md)|標記 `CAcl` 物件成員 `NULL`。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAcl::operator const ACL \*](../Topic/CAcl::operator%20const%20ACL%20*.md)|要轉型為的 `ACL` 結構的 `CAcl` 物件。|  
|[CAcl::operator \=](../Topic/CAcl::operator%20=.md)|指派運算子。|  
  
## 備註  
 **ACL** 結構是 ACL \(存取控制清單 \(SACL\)\) 的標題。  ACL 包含零或多個 [ACE](http://msdn.microsoft.com/library/windows/desktop/aa374868) \(存取控制項目\) 循序清單。  在 ACL 的個別一點從 0 開始編號到 *n\-1*， *n* 是按數目的 ACL。  當編輯 ACL 時，應用程式就可以根據索引參考 ACL 中的存取控制項目 \(ACE\) \(ACE\)。  
  
 有兩個 ACL 類型:  
  
-   選擇性  
  
-   System  
  
 選擇性 ACL 是由物件的擁有人控制項或其他物件的 **WRITE\_DAC** 授與存取權限。  它指定存取特定使用者群組，並可對物件。  例如，檔案的擁有者可以使用使用者和群組可以與不可擁有檔案的 ACL 選擇性控制項。  
  
 物件也有系統層級安全性資訊產生關聯，以系統管理員所控制的系統 ACL 的形式。  系統 ACL 可允許系統管理員稽核嘗試對物件的存取。  
  
 如需的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872) 討論。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)