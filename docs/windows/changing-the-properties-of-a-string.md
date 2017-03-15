---
title: "Changing the Properties of a String | Microsoft Docs"
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
  - "resource identifiers, string properties"
  - "string tables, changing strings"
  - "strings [C++], properties"
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Changing the Properties of a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要變更字串或其識別項  
  
1.  按兩下[資源檢視](../windows/resource-view-window.md)內的字串資料表圖示來開啟字串資料表。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  選取想要編輯的字串，然後按兩下 \[ID\]、\[值\] 或 \[標題\] 欄位。  現在您可以：  
  
    -   從 \[ID 下拉式清單\] 選取一個 \[ID\]，或就地直接地輸入 ID。  
  
    -   在 \[值\] 欄位內輸入不同值。  
  
    -   在 \[標題\] 欄位內輸入編輯文字。  
  
        > [!NOTE]
        >  您也可在[屬性視窗](../Topic/Properties%20Window.md)內編輯字串屬性。  
  
 如需將資源加入至 Managed 專案的詳細資訊 \(以 Common Language Runtime 為目標\)，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [String Editor](../mfc/string-editor.md)   
 [字串](_win32_Strings)   
 [關於字串](_win32_About_Strings_cpp)