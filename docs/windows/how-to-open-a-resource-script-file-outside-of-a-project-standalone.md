---
title: "How to: Open a Resource Script File Outside of a Project (Standalone) | Microsoft Docs"
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
  - "vc.editors.resource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - ".rc files, viewing resources"
  - "resource script files, viewing resources"
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Open a Resource Script File Outside of a Project (Standalone)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以檢視 .rc 檔中的資源，而不需要開啟一個專案。  .rc 檔會在文件視窗中開啟，相對於在 \[[資源檢視](../windows/resource-view-window.md)\] 視窗中開啟 \(如同在專案內開啟檔案\)。  
  
> [!NOTE]
>  這是一項重要的差異，因為某些命令只有在獨立開啟檔案時 \(在專案外\)，才可供使用。  例如，在專案外開啟檔案時，您只可以使用不同的格式或不同的檔案名稱形式儲存檔案 \(在專案內開啟檔案時，\[**另存新檔**\] 命令便無法使用\)。  
  
### 開啟專案外部的 .rc 檔案  
  
1.  從 \[**檔案**\] 功能表，選擇 \[**開啟**\]，然後按一下 \[**檔案**\]。  
  
2.  在 \[**開啟檔案**\] 對話方塊中，巡覽至您要檢視的資源指令碼檔，反白顯示檔案，然後按一下 \[**開啟**\]。  
  
    > [!NOTE]
    >  如果您先開啟專案 \(\[**檔案**\]、\[**開啟**\]、\[**專案**\]\)，將無法使用一些命令。  「獨立」開啟檔案表示開啟檔案而不先載入專案。  
  
 若要開啟並檢視文字格式的資源檔，請參閱[編輯資源指令碼  \(.rc\) 檔](../windows/how-to-open-a-resource-script-file-in-text-format.md)。  
  
#### 開啟專案外的多個 .rc 檔  
  
1.  開啟兩個獨立資源檔案。  例如，開啟 Source1.rc 和 Source2.rc。  
  
    1.  從 \[**檔案**\] 功能表，選擇 \[**開啟**\]，然後按一下 \[**檔案**\]。  
  
    2.  在 \[**開啟檔案**\] 對話方塊中，巡覽至您要開啟的第一個資源指令碼檔 \(Source1.rc\)，反白顯示檔案，然後按一下 \[**開啟**\]。  
  
    3.  重複先前的步驟來開啟第二個 .rc 檔 \(Source2.rc\)。  
  
         .rc 檔現在會在個別的文件視窗中開啟。  
  
2.  開啟兩個 .rc 檔時，並排顯示視窗，以讓您同時檢視：  
  
    -   從 \[**視窗**\] 功能表，選擇 \[**新增水平索引標籤群組**\] 或 \[**新增垂直索引標籤群組**\]。  
  
         \-或\-  
  
    -   以滑鼠右鍵按一下其中一個 .rc 檔，然後從捷徑功能表選擇 \[**新增水平索引標籤群組**\] 或 \[**新增垂直索引標籤群組**\]。  
  
> [!NOTE]
>  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)