---
title: "How to: Create a Resource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toolbars [C++], resources"
  - "resource toolbars"
  - "resources [Visual Studio], creating"
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Create a Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  資源檢視在 Express 版中不受支援。  
  
### 在資源檢視中建立新的資源  
  
1.  在[資源檢視](../windows/resource-view-window.md)中將焦點設在 .rc 檔，按一下 \[**編輯**\] 功能表並選擇 \[**加入資源**\] \(或以滑鼠右鍵按一下資源檢視中的 .rc 檔，再從捷徑功能表中選擇 \[**加入資源**\]\)。  
  
     **附註** 如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。  
  
### 在方案總管中建立新的資源  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案資料夾並選擇 \[**加入**\]，然後在捷徑功能表上按一下 \[**加入資源**\]。  
  
     如果您的專案中還沒有 .rc 檔，這個步驟會建立一個 .rc 檔。 接著，您可以重複此步驟，將特定資源類型加入至新的 .rc 檔。  
  
2.  在[加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。  
  
### 在類別檢視中建立新的資源  
  
1.  在 \[[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)\] 中，以滑鼠右鍵按一下類別並選擇 \[**加入**\]，然後從捷徑功能表按一下 \[**加入資源**\]。  
  
2.  在[加入資源對話方塊](../windows/add-resource-dialog-box.md)中，選擇您想要加入至專案的資源類型。  
  
### 從專案功能表建立新的資源  
  
1.  從 \[**專案**\] 功能表中，選擇 \[**加入資源**\]。  
  
 當您建立新的資源時，Visual C\+\+ 會指派唯一名稱給它，例如 IDD\_Dialog1。 您可以在相關聯的資源編輯器中或在 \[[屬性視窗](../Topic/Properties%20Window.md)\] 中編輯資源的屬性，以自訂此資源 ID。  
  
 您可以將資源建立為新的預設資源 \(不以範本為基礎的資源\)，或建立為模仿[範本](../windows/how-to-use-resource-templates.md)的資源。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)   
 [加入資源對話方塊](../windows/add-resource-dialog-box.md)