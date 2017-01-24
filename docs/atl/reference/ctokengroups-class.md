---
title: "CTokenGroups Class | Microsoft Docs"
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
  - "ATL::CTokenGroups"
  - "ATL.CTokenGroups"
  - "CTokenGroups"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTokenGroups class"
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTokenGroups Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 **TOKEN\_GROUPS** 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CTokenGroups  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTokenGroups::CTokenGroups](../Topic/CTokenGroups::CTokenGroups.md)|建構函式。|  
|[CTokenGroups::~CTokenGroups](../Topic/CTokenGroups::~CTokenGroups.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTokenGroups::Add](../Topic/CTokenGroups::Add.md)|將 `CSid` 或現有的 **TOKEN\_GROUPS** 結構至 `CTokenGroups` 物件。|  
|[CTokenGroups::Delete](../Topic/CTokenGroups::Delete.md)|刪除 `CSid` 及其相關屬性從 `CTokenGroups` 物件。|  
|[CTokenGroups::DeleteAll](../Topic/CTokenGroups::DeleteAll.md)|刪除所有 `CSid` 物件及其關聯的屬性從 `CTokenGroups` 物件。|  
|[CTokenGroups::GetCount](../Topic/CTokenGroups::GetCount.md)|傳回數目。 **CTokenGroups** 物件和相關聯的屬性所包含的 `CSid` 物件。|  
|[CTokenGroups::GetLength](../Topic/CTokenGroups::GetLength.md)|傳回 `CTokenGroups` 物件的大小。|  
|[CTokenGroups::GetPTOKEN\_GROUPS](../Topic/CTokenGroups::GetPTOKEN_GROUPS.md)|擷取指標 **TOKEN\_GROUPS** 結構。|  
|[CTokenGroups::GetSidsAndAttributes](../Topic/CTokenGroups::GetSidsAndAttributes.md)|擷取屬於 `CTokenGroups` 物件的 `CSid` 物件和屬性。|  
|[CTokenGroups::LookupSid](../Topic/CTokenGroups::LookupSid.md)|擷取與屬性關聯的 `CSid` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CTokenGroups::operator const TOKEN\_GROUPS \*](../Topic/CTokenGroups::operator%20const%20TOKEN_GROUPS%20*.md)|將物件轉換成指標的 `CTokenGroups` 物件 **TOKEN\_GROUPS** 結構。|  
|[CTokenGroups::operator \=](../Topic/CTokenGroups::operator%20=.md)|指派運算子。|  
  
## 備註  
 [存取語彙基元](http://msdn.microsoft.com/library/windows/desktop/aa374909) 是描述處理序或執行緒的安全性內容的物件和配置給每一位使用者都會記錄在 Windows NT 或 Windows 2000 系統上。  
  
 **CTokenGroups** 類別是 [TOKEN\_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624) 結構的包裝函式，其中包含有關群組安全識別項 \(SID\) \(SIDs\) 的資訊在存取語彙基元。  
  
 如需存取控制模型會在  視窗，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860) 。  
  
## 需求  
 **Header:** atlsecurity.h  
  
## 請參閱  
 [安全性範例](../../top/visual-cpp-samples.md)   
 [CSid Class](../../atl/reference/csid-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)