---
title: "無法還原某些預設檔案關聯。 注意：您必須是這部電腦的系統管理員或進階使用者，才能變更檔案關聯。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法還原某些預設檔案關聯。 注意：您必須是這部電腦的系統管理員或進階使用者，才能變更檔案關聯。
當使用 devenv 命令列參數 \/AssociateFiles，但目前使用者權限不允許存取登錄的 HKEY\_CLASSES\_ROOT 區段時，就會發生此錯誤。 當您在 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 上執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 時，必須以系統管理員的身分執行 devenv，才能使用 \/AssociateFiles \(devenv.exe\) 參數。  
  
### 更正這個錯誤  
  
-   變更為管理認證，然後再試一次。  
  
## 請參閱  
 [User Rights and Visual Studio](http://msdn.microsoft.com/zh-tw/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Devenv 命令列參數](../Topic/Devenv%20Command%20Line%20Switches.md)