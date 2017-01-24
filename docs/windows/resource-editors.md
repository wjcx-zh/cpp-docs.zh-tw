---
title: "Resource Editors | Microsoft Docs"
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
  - "vs.editors.resource"
  - "vc.resvw.resource.editors"
  - "vs.resvw.resource.editors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors [C++], resource"
  - "editors [C++]"
  - "resource editors"
  - "Windows [C++], application resource editing"
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resource Editors
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資源編輯器是建立或修改 Visual Studio 專案所含資源的特殊環境。 Visual Studio 資源編輯器會共用技術和介面，協助您快速輕鬆地建立及修改應用程式資源。 資源編輯器可讓您[在適當的編輯器中檢視和編輯資源](../mfc/viewing-and-editing-resources-in-a-resource-editor.md)以及[預覽資源](../mfc/previewing-resources.md)。  
  
 當您建立或開啟資源時，適當的編輯器會自動開啟。  
  
 **注意**：因為 Managed 專案不使用資源指令碼檔案，因此您必須從**方案總管**開啟資源。 您可以使用[影像編輯器](../mfc/image-editor-for-icons.md)和[二進位編輯器](../mfc/binary-editor.md)處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*應用程式中的資源*。如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
|使用...|編輯...|  
|-----------|-----------|  
|[快速鍵編輯器](../mfc/accelerator-editor.md)|Visual C\+\+ 專案中的快速鍵對應表。|  
|[二進位編輯器](../mfc/binary-editor.md)|Visual C\+\+、Visual Basic 或 Visual C\# 專案的二進位資料資訊和自訂資源。|  
|[對話方塊編輯器](../mfc/dialog-editor.md)|Visual C\+\+ 專案中的對話方塊。|  
|[HTML 設計工具](../Topic/HTML%20Designer.md)|在 \[設計\] 檢視和 \[HTML\] 檢視的 HTML 頁面。 警告：您不能變更 EXE 或 DLL 中的 HTML 網頁，因為您執行的變更不會匯回 EXE 或 DLL。|  
|[影像編輯器](../mfc/image-editor-for-icons.md)|Visual C\+\+、Visual Basic 或 Visual C\# 專案的點陣圖、圖示、游標和其他影像檔。|  
|[功能表編輯器](../mfc/menu-editor.md)|Visual C\+\+ 專案中的功能表資源。|  
|[功能區編輯器](../mfc/ribbon-designer-mfc.md)|MFC 專案中的功能區資源。|  
|[字串編輯器](../mfc/string-editor.md)|Visual C\+\+ 專案中的字串資料表。|  
|[工具列編輯器](../mfc/toolbar-editor.md)|Visual C\+\+ 專案中的工具列資源。 工具列編輯器是影像編輯器的一部分。|  
|[版本資訊編輯器](../mfc/version-information-editor.md)|Visual C\+\+ 專案中的版本資訊。|  
  
## 需求  
 無  
  
## 請參閱  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [功能表與其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)