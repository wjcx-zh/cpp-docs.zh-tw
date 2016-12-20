---
title: "CTokenPrivileges Class | Microsoft Docs"
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
  - "ATL::CTokenPrivileges"
  - "CTokenPrivileges"
  - "ATL.CTokenPrivileges"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenPrivileges class"
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTokenPrivileges Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 **TOKEN\_PRIVILEGES** 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CTokenPrivileges  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTokenPrivileges::CTokenPrivileges](../Topic/CTokenPrivileges::CTokenPrivileges.md)|建構函式。|  
|[CTokenPrivileges::~CTokenPrivileges](../Topic/CTokenPrivileges::~CTokenPrivileges.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTokenPrivileges::Add](../Topic/CTokenPrivileges::Add.md)|將一或多個權限 `CTokenPrivileges` 物件。|  
|[CTokenPrivileges::Delete](../Topic/CTokenPrivileges::Delete.md)|刪除 `CTokenPrivileges` 物件的一個使用權限。|  
|[CTokenPrivileges::DeleteAll](../Topic/CTokenPrivileges::DeleteAll.md)|刪除 `CTokenPrivileges` 物件的所有權限。|  
|[CTokenPrivileges::GetCount](../Topic/CTokenPrivileges::GetCount.md)|傳回使用權限項目數目 `CTokenPrivileges` 物件的。|  
|[CTokenPrivileges::GetDisplayNames](../Topic/CTokenPrivileges::GetDisplayNames.md)|擷取顯示名稱在 `CTokenPrivileges` 物件中所包含的權限。|  
|[CTokenPrivileges::GetLength](../Topic/CTokenPrivileges::GetLength.md)|在要求中傳回位元組緩衝區大小物件所 **TOKEN\_PRIVILEGES** 結構表示由 `CTokenPrivileges` 物件。|  
|[CTokenPrivileges::GetLuidsAndAttributes](../Topic/CTokenPrivileges::GetLuidsAndAttributes.md)|從 `CTokenPrivileges` 物件擷取當地的唯一識別項 \(LUIDs\) 和屬性旗標。|  
|[CTokenPrivileges::GetNamesAndAttributes](../Topic/CTokenPrivileges::GetNamesAndAttributes.md)|從物件擷取 `CTokenPrivileges` 權限名稱和屬性旗標。|  
|[CTokenPrivileges::GetPTOKEN\_PRIVILEGES](../Topic/CTokenPrivileges::GetPTOKEN_PRIVILEGES.md)|傳回指向 **TOKEN\_PRIVILEGES** 結構。|  
|[CTokenPrivileges::LookupPrivilege](../Topic/CTokenPrivileges::LookupPrivilege.md)|擷取屬性與給定之權限的名稱。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CTokenPrivileges::operator const TOKEN\_PRIVILEGES \*](../Topic/CTokenPrivileges::operator%20const%20TOKEN_PRIVILEGES%20*.md)|將值轉型為指標 **TOKEN\_PRIVILEGES** 結構。|  
|[CTokenPrivileges::operator \=](../Topic/CTokenPrivileges::operator%20=.md)|指派運算子。|  
  
## 備註  
 [存取語彙基元](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述處理序或執行緒的安全性內容的物件和配置給每一位使用者都會記錄在 Windows NT 或 Windows 2000 系統上。  
  
 存取語彙基元是用來描述各種安全性授權給每一位使用者。  這些權限包括呼叫當地的唯一識別項 \([LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)\) 和描述項字串的 64 位元數字。  
  
 `CTokenPrivileges` 類別是 [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 結構的包裝函式和包含 0 個或更多權限。  使用提供的類別方法，授權，可加入、刪除或查詢。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [TOKEN\_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID\_AND\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)