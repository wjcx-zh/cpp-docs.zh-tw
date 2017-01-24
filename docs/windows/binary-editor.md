---
title: "Binary Editor | Microsoft Docs"
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
  - "vc.editors.binary.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors, Binary"
  - "resources [Visual Studio], editing"
  - "resource editors, Binary editor"
  - "Binary editor"
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Binary Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!WARNING]
>  二進位編輯器在 Express 版中無法使用的。  
  
 二進位編輯器允許您在二進位層級，以十六進位或 ASCII 格式編輯任何資源。 您也可以使用 [&#91;尋找命令&#93;](../Topic/Find%20Command.md) 搜尋 ASCII 字串或十六進位位元組。 請只有在需要檢視或對 Visual Studio 環境不支援的自訂資源或資源類型進行細微變更時，才使用二進位編輯器。  
  
 若要開啟二進位編輯器，首先從主功能表選取 \[**檔案 &#124; 新增 &#124; 檔案**\]，選取您要編輯的檔案，然後按一下 \[**開啟**\] 按鈕旁的下拉箭號，然後選取 \[**開啟方式 &#124; 二進位編輯器**\]。  
  
> [!CAUTION]
>  在二進位編輯器中編輯諸如對話方塊、影像或功能表等資源，是很危險的事。 不正確的編輯可能會損毀資源，讓它在原生編輯器中無法讀取。  
  
> [!TIP]
>  使用二進位編輯器時，在許多情況下您可以按一下滑鼠右鍵，顯示資源特定命令的快顯功能表。 可用的命令取決於游標所指項目。 例如，如果在指向含有所選十六進位值的二進位編輯器時按一下，快顯功能表就會顯示 \[剪下\]、\[複製\] 和 \[貼上\] 命令。  
  
 使用二進位編輯器，您可以：  
  
-   [開啟資源進行二進位編輯](../mfc/opening-a-resource-for-binary-editing.md)  
  
-   [編輯二進位資料](../mfc/editing-binary-data.md)  
  
-   [尋找二進位資料](../mfc/finding-binary-data.md)  
  
-   [建立新的自訂或資料資源](../mfc/creating-a-new-custom-or-data-resource.md)  
  
## Managed 資源  
 您可以使用影像編輯器和[二進位編輯器](../mfc/image-editor-for-icons.md)處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*應用程式中的資源*。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 無  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)