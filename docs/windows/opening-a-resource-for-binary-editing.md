---
title: "Opening a Resource for Binary Editing | Microsoft Docs"
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
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary data, editing"
  - "resources [Visual Studio], opening for binary editing"
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Opening a Resource for Binary Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 開啟 Windows 桌面資源進行二進位編輯  
  
1.  在 \[資源檢視\][](../windows/resource-view-window.md "Resource View Window") 中，選取您要編輯的特定資源檔。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  以滑鼠右鍵按一下資源，然後從捷徑功能表按一下 \[開啟二進位資料\]。  
  
    > [!NOTE]
    >  如果您使用 \[資源檢視\][](../windows/resource-view-window.md "Resource View Window") 視窗開啟含 Visual Studio 無法辨識之格式的資源 \(例如 RCDATA 或自訂資源\)，此資源會自動以二進位編輯器開啟。  
  
### 開啟 Managed 資源進行二進位編輯  
  
1.  在方案總管中，選取您要編輯的特定資源檔。  
  
2.  以滑鼠右鍵按一下資源，然後從捷徑功能表選擇 \[開啟方式\]。  
  
3.  在 \[開啟方式\] 對話方塊中，選擇 \[二進位編輯器\]。  
  
    > [!NOTE]
    >  您可以使用[影像編輯器](../mfc/image-editor-for-icons.md)和[二進位編輯器](../mfc/binary-editor.md)處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
    > [!NOTE]
    >  如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*應用程式中的資源*。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 ![二進位編輯器](../mfc/media/vcbinaryeditor2.png "vcBinaryEditor2")  
二進位編輯器中所顯示之對話方塊的二進位資料  
  
 二進位編輯器中只會表示特定 ASCII 值 \(0x20 到 0x7E\)。 擴充字元會在二進位編輯器的 \[ASCII 值\] 區段 \(右窗格\) 中顯示為句號。 「可列印」字元是 ASCII 值 32 到 126。  
  
> [!NOTE]
>  如果您想要針對已在其他編輯器視窗中編輯的資源使用二進位編輯器，請先關閉其他編輯器視窗。  
  
 **需求**  
  
 無  
  
## 請參閱  
 [Binary Editor](../mfc/binary-editor.md)