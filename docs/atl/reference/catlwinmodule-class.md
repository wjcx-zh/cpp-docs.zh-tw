---
title: "CAtlWinModule Class | Microsoft Docs"
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
  - "ATL::CAtlWinModule"
  - "ATL.CAtlWinModule"
  - "CAtlWinModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlWinModule class"
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlWinModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供 ATL Windowing 元件的支援。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAtlWinModule : public _ATL_WIN_MODULE  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlWinModule::CAtlWinModule](../Topic/CAtlWinModule::CAtlWinModule.md)|建構函式。|  
|[CAtlWinModule::~CAtlWinModule](../Topic/CAtlWinModule::~CAtlWinModule.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlWinModule::AddCreateWndData](../Topic/CAtlWinModule::AddCreateWndData.md)|將資料物件。|  
|[CAtlWinModule::ExtractCreateWndData](../Topic/CAtlWinModule::ExtractCreateWndData.md)|傳回指向視窗模組資料物件。|  
  
## 備註  
 這個類別是特別針對需要 Windowing 功能的所有 ATL 類別的支援。  
  
## 繼承階層架構  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)  
  
 `CAtlWinModule`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)