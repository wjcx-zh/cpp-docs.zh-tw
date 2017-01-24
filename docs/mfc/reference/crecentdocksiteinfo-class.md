---
title: "CRecentDockSiteInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecentDockSiteInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecentDockSiteInfo class"
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRecentDockSiteInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CRecentDockSiteInfo` 類別是協助程式類別，會儲存 [CPane Class](../../mfc/reference/cpane-class.md)的最近狀態資訊。  
  
## 語法  
  
```  
class CRecentDockSiteInfo : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRecentDockSiteInfo::CleanUp](../Topic/CRecentDockSiteInfo::CleanUp.md)||  
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](../Topic/CRecentDockSiteInfo::GetRecentDefaultPaneDivider.md)||  
|[CRecentDockSiteInfo::GetRecentDockedPercent](../Topic/CRecentDockSiteInfo::GetRecentDockedPercent.md)||  
|[CRecentDockSiteInfo::GetRecentDockedRect](../Topic/CRecentDockSiteInfo::GetRecentDockedRect.md)||  
|[CRecentDockSiteInfo::GetRecentListOfPanes](../Topic/CRecentDockSiteInfo::GetRecentListOfPanes.md)||  
|[CRecentDockSiteInfo::GetRecentPaneContainer](../Topic/CRecentDockSiteInfo::GetRecentPaneContainer.md)||  
|[CRecentDockSiteInfo::GetRecentTabContainer](../Topic/CRecentDockSiteInfo::GetRecentTabContainer.md)||  
|[CRecentDockSiteInfo::Init](../Topic/CRecentDockSiteInfo::Init.md)||  
|[CRecentDockSiteInfo::IsRecentLeftPane](../Topic/CRecentDockSiteInfo::IsRecentLeftPane.md)||  
|[CRecentDockSiteInfo::operator \=](../Topic/CRecentDockSiteInfo::operator%20=.md)||  
|[CRecentDockSiteInfo::SaveListOfRecentPanes](../Topic/CRecentDockSiteInfo::SaveListOfRecentPanes.md)||  
|[CRecentDockSiteInfo::SetInfo](../Topic/CRecentDockSiteInfo::SetInfo.md)||  
|[CRecentDockSiteInfo::StoreDockInfo](../Topic/CRecentDockSiteInfo::StoreDockInfo.md)||  
  
## 備註  
 `CRecentDockSiteInfo` 類別是資料管理類別。  它會追蹤 `CPane` 在停駐和浮動之間轉換時的最後狀態。  當使用者按兩下浮動可停駐窗格時，它會變成停駐。  按兩下停駐窗格會使其返回至先前的位置、大小及狀態。  同樣地，重新停駐窗格時，它會返回至其先前的停駐位置。  這個資料類別可以使其成行。  由於此類別的成員會儲存停駐窗格的狀態資訊，所以它們不應該由您的應用程式直接修改。  
  
 每次建立窗格式就會建立 `CRecentDockSiteInfo` 物件。  每個 `CPane` 物件具有成員變數，[CPane::m\_recentDockInfo](../Topic/CPane::m_recentDockInfo.md)，以儲存此資訊。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)  
  
## 需求  
 **標頭：**afxrecentDockSiteInfo.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)