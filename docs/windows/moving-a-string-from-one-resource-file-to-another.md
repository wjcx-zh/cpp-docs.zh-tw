---
title: "Moving a String from One Resource File to Another | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "strings [C++], moving between files"
  - "resource script files, moving strings"
  - "string editing, moving strings between resources"
  - "String editor, moving strings between files"
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Moving a String from One Resource File to Another
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要將字串從資源指令碼檔移至另一個資源檔  
  
1.  開啟這兩個 .rc 檔的字串資料表   \(如需詳細資訊，請參閱[檢視專案外的資源指令碼檔的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)\)。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在想要移動的字串按一下滑鼠右鍵，並在捷徑功能表內選擇 \[剪下\]。  
  
3.  將游標放到目標的 \[字串編輯器\] 視窗內。  
  
4.  在想要移入字串的 .rc 檔按一下滑鼠右鍵，然後選擇捷徑功能表的 \[貼上\]。  
  
    > [!NOTE]
    >  如果移動字串的 **ID** 或值和目的檔的現有 **ID** 或值有衝突，移動字串的 **ID** 或值將會變更。  如果某字串已存在相同的 **ID**，則移動字串的 **ID** 將會變更。  如果某字串已存在相同的**值**，移動字串的**值**將會變更。  
  
 如需將資源加入至 Managed 專案的詳細資訊 \(以 Common Language Runtime 為目標\)，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [String Editor](../mfc/string-editor.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [自訂視窗版面配置](../Topic/Customizing%20window%20layouts%20in%20Visual%20Studio.md)   
 [字串](_win32_Strings)   
 [關於字串](_win32_About_Strings_cpp)