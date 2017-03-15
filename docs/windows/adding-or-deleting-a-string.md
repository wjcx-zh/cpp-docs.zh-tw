---
title: "Adding or Deleting a String | Microsoft Docs"
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
  - "vc.editors.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], adding to string tables"
  - "string tables, deleting strings"
  - "strings [C++], deleting in string tables"
  - "string tables, adding strings"
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding or Deleting a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用字串編輯器，迅速地將新的項目插入至字串資料表中。  新的字串將放在字串資料表最後面，並被指定下一個可用的識別項。  接著可依照需要在[屬性視窗](../Topic/Properties%20Window.md)內編輯 ID、值或標題屬性。  
  
 字串編輯器會確認您沒有在使用這個已經在使用的 ID。  如果選取了一個已經在使用的 ID，字串編輯器將會通知您，並接著指定泛型的唯一 ID，例如 IDS\_STRING58113。  
  
### 若要加入字串資料表項目  
  
1.  按兩下[資源檢視](../windows/resource-view-window.md)內的字串資料表圖示來開啟字串資料表。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在字串資料表內按一下滑鼠右鍵，然後從捷徑功能表選擇 \[新增字串\]。  
  
3.  在**字串**編輯器中，從 \[ID\] 下拉式清單選取一個 **ID**，或就地直接輸入 ID。  
  
4.  依照需要編輯 \[值\]。  
  
5.  輸入 \[標題\] 的項目。  
  
    > [!NOTE]
    >  Windows 字串資料表內不允許 Null 字串出現。  如果您在字串資料表內建立了一個 Null 字串，您將會收到要求您「請輸入此資料表項目的字串」的訊息。  
  
### 若要刪除字串資料表項目  
  
1.  選取想要刪除的項目  
  
2.  在 \[**編輯**\] 功能表上，按一下 \[**刪除**\]。  
  
 \-或\-  
  
-   在想要刪除的字串上，按一下滑鼠右鍵，並於捷徑功能表上選擇 \[刪除\]。  
  
 \-或\-  
  
-   按下 **DELETE** 鍵。  
  
 如需將資源加入至 Managed 專案的詳細資訊 \(以 Common Language Runtime 為目標\)，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [String Editor](../mfc/string-editor.md)   
 [字串](_win32_Strings)   
 [關於字串](_win32_About_Strings_cpp)