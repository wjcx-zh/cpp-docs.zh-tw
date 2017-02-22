---
title: "CAtlComModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlComModule"
  - "CAtlComModule"
  - "ATL::CAtlComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlComModule class"
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 COM 伺服器模組。  
  
## 語法  
  
```  
  
   class CAtlComModule :  
public _ATL_COM_MODULE  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlComModule::CAtlComModule](../Topic/CAtlComModule::CAtlComModule.md)|建構函式。|  
|[CAtlComModule::~CAtlComModule](../Topic/CAtlComModule::~CAtlComModule.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlComModule::RegisterServer](../Topic/CAtlComModule::RegisterServer.md)|呼叫這個方法會更新每個物件的系統登錄物件中對應。|  
|[CAtlComModule::RegisterTypeLib](../Topic/CAtlComModule::RegisterTypeLib.md)|呼叫這個方法會註冊型別程式庫。|  
|[CAtlComModule::UnregisterServer](../Topic/CAtlComModule::UnregisterServer.md)|呼叫這個方法移除註冊物件中對應的每個物件。|  
|[CAtlComModule::UnRegisterTypeLib](../Topic/CAtlComModule::UnRegisterTypeLib.md)|呼叫這個方法移除註冊型別程式庫。|  
  
## 備註  
 `CAtlComModule` 實作 COM 伺服器模組，允許用戶端存取模組的元件。  
  
 這個類別是用來取代舊版的 ATL [CComModule](../../atl/reference/ccommodule-class.md) 過時的類別。  如需的詳細資訊請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。  
  
## 繼承階層架構  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)  
  
 `CAtlComModule`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)