---
title: "Changing the Properties of Multiple Accelerator Keys | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "keyboard shortcuts [C++], property changing"
  - "accelerator tables [C++], changing properties"
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Properties of Multiple Accelerator Keys
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要變更多個快速鍵屬性  
  
1.  按兩下[資源檢視](../windows/resource-view-window.md)內的快速鍵對應表圖示來開啟快速鍵對應表。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在按下每個快速鍵時，按住 **CTRL** 鍵以選取您要變更的快速鍵。  
  
3.  移至[屬性視窗](../Topic/Properties%20Window.md)，並輸入您希望所有選取快速鍵能共用的值。  
  
    > [!NOTE]
    >  \[屬性\] 視窗內的每個輔助按鍵值都會顯示成布林 \(Boolean\) 屬性。  如果您變更 \[屬性\] 視窗內的[輔助按鍵](../windows/accelerator-modifier-property.md)值，則快速鍵對應表會將新的輔助按鍵加入任何之前設定的輔助按鍵中。  因此，如果您設定了任何輔助按鍵值，就需要為所有的輔助按鍵來進行設定，以確定每個快速鍵都是共用相同的 \[輔助按鍵\] 設定。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Editing Accelerator Tables](../windows/editing-accelerator-tables.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)