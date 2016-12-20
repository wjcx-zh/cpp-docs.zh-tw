---
title: "Registry and TypeLib Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegistryDataExchange function, 全域函式"
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registry and TypeLib Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式是在載入和註冊型別程式庫的支援。  
  
> [!IMPORTANT]
>  下表中列出的函式不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](../Topic/AtlRegisterTypeLib.md)|這個函式呼叫註冊型別程式庫。|  
|[AtlUnRegisterTypeLib](../Topic/AtlUnRegisterTypeLib.md)|這個函式呼叫註冊型別程式庫|  
|[AtlLoadTypeLib](../Topic/AtlLoadTypeLib.md)|這個函式呼叫載入型別程式庫。|  
|[AtlUpdateRegistryFromResourceD](../Topic/AtlUpdateRegistryFromResourceD.md)|這個函式呼叫更新所提供之資源的註冊。|  
|[RegistryDataExchange](../Topic/RegistryDataExchange.md)|這個函式呼叫讀取，或使用方法，寫入系統登錄。  呼叫 [註冊資料交換的巨集](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 在登錄中以產生用於儲存的這些功能的控制項。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](../Topic/AtlGetPerUserRegistration.md)|擷取應用程式是否已為 **HKEY\_CURRENT\_USER** \(**HKCU**\) 節點的登錄存取方向。|  
|[AtlSetPerUserRegistration](../Topic/AtlSetPerUserRegistration.md)|設定應用程式是否已為 **HKEY\_CURRENT\_USER** \(**HKCU**\) 節點的登錄存取方向。|  
  
## 請參閱  
 [函式](../../atl/reference/atl-functions.md)