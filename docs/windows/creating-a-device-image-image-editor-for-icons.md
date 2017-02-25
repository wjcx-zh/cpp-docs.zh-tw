---
title: "Creating a Device Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "icons [C++], creating"
  - "display devices"
  - "display devices, creating image"
  - "images [C++], creating for display devices"
  - "icons [C++], inserting"
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Creating a Device Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立新的圖示或游標資源時，影像編輯器會先以特定的樣式建立影像 \(圖示為 32 × 32、16 色，游標為 32 × 32、單色\)。  然後您可依所需，針對不同的顯示裝置，將不同的大小和樣式的影像加入至初始圖示或游標並編輯每一個附加的影像。  您也可以對現有影像類型或是在圖形程式建立的點陣圖，執行剪貼動作來編輯影像。  如需 Windows 所使用之圖示大小的詳細資訊，請參閱 Windows SDK 文件中的[圖示](_win32_Icons_cpp)。  
  
 當您在[影像編輯器](../mfc/image-editor-for-icons.md)中開啟圖示或游標資源時，依預設，會開啟與目前的顯示裝置最相符的影像。  
  
### 若要建立新的圖示或游標  
  
1.  在[資源檢視](../windows/resource-view-window.md)中，以滑鼠右鍵按一下您的 .rc 檔，然後從捷徑功能表中選擇 \[**插入資源**\]   \(如果您的 .rc 檔中已經有現有的影像資源 \(例如游標\)，則只要以滑鼠右鍵按一下 \[**游標**\] 資料夾，然後從捷徑功能表中選取 \[**插入游標**\] 即可\)。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入資源對話方塊](../windows/add-resource-dialog-box.md)中，選取 \[**圖示**\] 或 \[**游標**\]，然後按一下 \[**新增**\]。  這會針對圖示建立含 32 × 32、16 色圖示的圖示資源。  針對游標則會建立 32 × 32、單色 \(2 色\) 影像。  
  
     如果 \[**插入資源**\] 對話方塊中的影像資源類型旁邊出現一個加號 \(**\+**\)，表示有工具列範本可以使用。  按一下加號展開範本清單，選取範本，然後按一下 \[**新增**\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 None  
  
## 請參閱  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)