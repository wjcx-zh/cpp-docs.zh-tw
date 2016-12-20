---
title: "Resource Files (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "resources [Visual Studio]"
  - ".rc files"
  - "resource files"
  - "resource script files"
  - "resource script files, Win-32 based applications"
  - "resource script files, files updated when editing resources"
  - "resources [Visual Studio], types of resource files"
  - "rct files"
  - "resources [C++]"
  - "rc files"
  - "resource files, types of"
  - ".rct files"
  - "resource script files, unsupported types"
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resource Files (Visual Studio)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  這份資料適用於 Windows 桌面應用程式。 如需 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式資源的相關資訊，請參閱[定義應用程式資源](http://msdn.microsoft.com/zh-tw/476ea844-632c-4467-9ce3-966be1350dd4)。  
>   
>  如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從**方案總管**開啟資源。 您可以使用[影像編輯器](../mfc/image-editor-for-icons.md)和[二進位編輯器](../mfc/binary-editor.md)處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器不支援編輯內嵌的資源。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：當地語系化 Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 「資源檔案」一詞表示多種檔案類型，包括：  
  
-   程式的資源指令碼 \(.rc\) 檔。  
  
-   資源範本 \(.rct\) 檔。  
  
-   以獨立檔案形態存在的個別資源，例如 .rc 檔案提及的點陣圖、圖示或游標檔。  
  
-   開發環境產生的標頭檔，例如 .rc 檔案提及的 Resource.h。  
  
 資源也可以在[其他檔案類型](../windows/editable-file-types-for-resources.md)中找到，例如 .exe、.dll 和 .res 檔。 您可以使用專案內的以及不屬於目前專案的資源和資源檔。 您也可以使用不在 Visual studio 開發環境中建立的資源檔。 例如，您可以：  
  
-   使用巢狀和條件限定的資源檔案。  
  
-   更新現有的資源，或將它們轉換成 Visual C\+\+ 格式。  
  
-   從目前的資源檔匯入或匯出圖形資源。  
  
-   包含開發環境無法修改的共用或唯讀識別項 \(符號\)。  
  
-   在可執行檔 \(.exe\) 檔案中，包含於目前專案期間不需要編輯 \(或您不想要編輯\) 的資源，例如數個專案間共用的資源。  
  
-   包含開發環境不支援的類型。  
  
 本節涵蓋：  
  
-   [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)  
  
-   [建立新專案](../windows/how-to-create-a-resource.md)  
  
-   [檢視資源指令碼檔案的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [以文字格式開啟資源指令碼檔](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [複製資源](../windows/how-to-copy-resources.md)  
  
-   [使用資源範本 \(.rct\)](../windows/how-to-use-resource-templates.md)  
  
-   [匯入及匯出資源](../windows/how-to-import-and-export-resources.md)  
  
-   [可編輯的資源檔類型](../windows/editable-file-types-for-resources.md)  
  
-   [受資源編輯影響的檔案](../windows/files-affected-by-resource-editing.md)  
  
## 需求  
 Win32  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [功能表與其他資源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)