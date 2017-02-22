---
title: "Viewing and Editing Resources in a Resource Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resourceview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - "Resource View pane"
  - "layouts, previewing resource"
  - "code, viewing resources"
  - "resource editors, viewing resources"
  - ".rc files, viewing resources"
  - "resources [Visual Studio], editing"
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Viewing and Editing Resources in a Resource Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個資源類型都有一個專門處理該資源類型的資源編輯器。  您可透過相關的編輯器，對資源重新排列、重新調整其大小、加入控制項和功能，或是修改其各個部分。  您也可採[文字格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)和[二進位格式](../mfc/opening-a-resource-for-binary-editing.md)來編輯資源。  
  
 有些資源類型為個別的檔案，您可採用不同的方式來匯入和使用；這些類型包括了點陣圖、圖示、游標、工具列和 html 檔。  這類資源擁有檔案名稱以及[資源識別項](../mfc/symbols-resource-identifiers.md)。  其他類型，例如 Win 32 專案中的對話方塊、功能表和字串資料表，僅做為資源指令碼檔 \(.rc\) 或資源範本檔 \(.rct\) 的一部分。  
  
> [!NOTE]
>  資源的屬性可使用[屬性視窗](../windows/changing-the-properties-of-a-resource.md)修改。  
  
## Win32 資源  
 您可在[資源檢視](../windows/resource-view-window.md)窗格內存取 Win32 資源。  
  
#### 若要在資源編輯器內檢視 Win32 資源  
  
1.  選取 \[檢視\] 功能表的 \[資源檢視\]。  
  
2.  如果 \[資源檢視\] 視窗並非最上層的視窗，請按 \[資源檢視\] 索引標籤將它顯示在最上面。  
  
3.  從 \[資源檢視\] 中，展開想要檢視其中資源的專案資料夾。  例如，如果您想要檢視對話方塊資源，可展開 \[對話方塊\] 資料夾。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
4.  按兩下資源，例如 IDD\_ABOUTBOX。  
  
     該資源會於適當的編輯器內開啟。  例如，若處理的是對話方塊資源，會於對話方塊編輯器內開啟。  
  
     您也可以[在 .rc \(資源指令碼\) 檔內檢視資源，而不需開啟專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
#### 若要刪除現有的 Win 32 資源  
  
1.  在 \[資源檢視\] 中展開某個資源類型的節點。  
  
2.  在您要刪除的資源上，按一下滑鼠右鍵，並於快速鍵功能表上選擇 \[刪除\]。  
  
    > [!NOTE]
    >  當您將 .rc 檔開啟於專案以外的文件視窗時，可使用同一快速鍵功能表命令刪除資源。  
  
## Managed 專案中的資源  
 由於 Managed 專案不使用資源指令碼檔，因此您必須從**方案總管**開啟資源。  您可以使用[影像編輯器](../mfc/image-editor-for-icons.md)和[二進位編輯器](../mfc/binary-editor.md)來使用 Managed 專案中的資源檔。  您想要編輯的任何 Managed 資源皆必須為連結的資源。  Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
#### 若要在資源編輯器內檢視 Managed 資源  
  
1.  在 \[方案總管\] 中，以滑鼠按兩下某個資源 \(如 Bitmap1.bmp\)。  
  
     該資源會於適當的編輯器內開啟。  
  
#### 若要刪除現有的 Managed 資源  
  
1.  在 \[方案總管\] 中，對想要刪除的資源按一下滑鼠右鍵，並於快速鍵功能表上選擇 \[刪除\]。  
  
### 需求  
 None  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)