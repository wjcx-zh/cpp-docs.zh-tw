---
title: "Adding Version Information for Another Language | Microsoft Docs"
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
  - "languages, version information"
  - "New Version Info Block"
  - "blocks, adding"
  - "resources [Visual Studio], adding version information"
  - "version information, adding for languages"
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Version Information for Another Language
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 加入另一種語言的版本資訊 \(新增資訊區塊\)  
  
1.  按兩下版本資訊資源，在[資源檢視](../windows/resource-view-window.md)中開啟它。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  以滑鼠右鍵在版本資訊表內按一下，然後從快顯功能表中選擇 \[新增版本資訊區塊\]。  
  
     這個命令會將額外的資訊區塊加入目前的版本資訊資源中，並在 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md) 中開啟其對應的屬性。  
  
3.  在 \[屬性\] 視窗中，為新的區塊選擇適當的語言和字元集。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Version Information Editor](../mfc/version-information-editor.md)   
 [版本資訊 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)