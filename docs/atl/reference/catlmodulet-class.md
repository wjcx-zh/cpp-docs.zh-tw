---
title: "CAtlModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlModuleT<T>"
  - "ATL.CAtlModuleT"
  - "ATL.CAtlModuleT<T>"
  - "ATL::CAtlModuleT"
  - "CAtlModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModuleT class"
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 ATL 模組。  
  
## 語法  
  
```  
  
      template <  
   class T   
>   
class ATL_NO_VTABLE CAtlModuleT :  
   public CAtlModule  
```  
  
#### 參數  
 `T`  
 從 `CAtlModuleT`衍生的類別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlModuleT::CAtlModuleT](../Topic/CAtlModuleT::CAtlModuleT.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlModuleT::InitLibId](../Topic/CAtlModuleT::InitLibId.md)|初始化包含目前模組的 GUID 的資料成員。|  
|[CAtlModuleT::RegisterAppId](../Topic/CAtlModuleT::RegisterAppId.md)|將 EXE 加入至登錄中。|  
|[CAtlModuleT::RegisterServer](../Topic/CAtlModuleT::RegisterServer.md)|將服務加入至登錄中。|  
|[CAtlModuleT::UnregisterAppId](../Topic/CAtlModuleT::UnregisterAppId.md)|從登錄移除 EXE。|  
|[CAtlModuleT::UnregisterServer](../Topic/CAtlModuleT::UnregisterServer.md)|從登錄中移除服務。|  
|[CAtlModuleT::UpdateRegistryAppId](../Topic/CAtlModuleT::UpdateRegistryAppId.md)|更新在登錄的 EXE 資訊。|  
  
## 備註  
 `CAtlModuleT`，衍生自 [CAtlModule](../../atl/reference/catlmodule-class.md)，實作一個可執行檔 \(EXE\) 或服務時 \(EXE\) ATL 模組。  可執行檔模組是區域，跨處理序 \(Out\-Of\-Process\) 伺服器，舵命令，而是在背景中執行的 Windows 應用程式，當 Windows 啟動時。  
  
 `CAtlModuleT` 進行初始化，註冊和取消註冊模組的支援。  
  
## 繼承階層架構  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CAtlModule Class](../../atl/reference/catlmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)