---
title: "Accessing Version Information from Within Your Program | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerQueryValue"
  - "version information, accessing from within programs"
  - "GetFileVersionInfo"
  - "version information"
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Accessing Version Information from Within Your Program
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 存取程式內的版本資訊  
  
1.  如果您想要存取程式內的版本資訊，請使用 [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) 函式和 [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) 函式。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本資訊 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)