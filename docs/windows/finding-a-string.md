---
title: "Finding a String | Microsoft Docs"
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
  - "strings [C++], searching"
  - "strings [C++]"
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Finding a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可在字串資料表內搜尋一個或多個字串，並配合 \[檔案中尋找\] 命令 \(\[編輯\] 功能表\) 使用[規則運算式](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)，找出符合某模式的所有字串。  
  
### 若要在字串資料表內尋找字串  
  
1.  按兩下[資源檢視](../windows/resource-view-window.md)內的字串資料表圖示來開啟字串資料表。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[編輯\] 功能表中按一下 \[尋找和取代\]，然後選擇 \[尋找\]。  
  
3.  在 \[尋找目標\] 方塊中，從下拉式清單選取先前的搜尋字串，或輸入您要尋找的字串之標題文字或資源識別項。  
  
4.  選取任何 \[尋找\] 選項。  
  
5.  按一下 \[**找下一個**\]。  
  
    > [!TIP]
    >  若要在搜尋檔案時使用規則運算式，請使用 \[檔案中尋找\] 命令。  輸入一個符合某模式的規則運算式，或按一下 \[尋找目標\] 方塊右邊的按鈕，顯示規則搜尋運算式的清單。  當您從此清單中選取了一個運算式之後，它會替代成 \[尋找目標\] 方塊內的搜尋文字。  如果您在使用規則運算式，請確定已經選取 \[使用：規則運算式\] 核取方塊。  
  
 如需將資源加入至 Managed 專案的詳細資訊 \(以 Common Language Runtime 為目標\)，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [String Editor](../mfc/string-editor.md)   
 [字串](_win32_Strings)   
 [關於字串](_win32_About_Strings_cpp)