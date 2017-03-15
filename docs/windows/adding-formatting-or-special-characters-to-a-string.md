---
title: "Adding Formatting or Special Characters to a String | Microsoft Docs"
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
  - "special characters, adding to strings"
  - "ASCII characters, adding to strings"
  - "strings [C++], formatting"
  - "strings [C++], special characters"
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Adding Formatting or Special Characters to a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要將格式或特殊字元加入至字串  
  
1.  按兩下[資源檢視](../windows/resource-view-window.md)內的字串資料表圖示來開啟字串資料表。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  選取要修改的字串。  
  
3.  在[屬性視窗](../Topic/Properties%20Window.md)中，將下表所列出的任何一個標準逸出序列 \(Escape Sequence\) 加入至 \[標題\] 方塊中的文字，並按下 **ENTER**。  
  
    |若要得到|請輸入|  
    |----------|---------|  
    |新行|\\n|  
    |歸位字元|\\r|  
    |Tab|\\t|  
    |反斜線 \(\\\)|\\\\|  
    |ASCII 字元|\\ddd \(八進位標記\)|  
    |警示 \(鈴響\)|\\a|  
  
> [!NOTE]
>  字串編輯器並不支援完整的逸出 ASCI 字元集。  您只能使用以上所列出的字元。  
  
 如需將資源加入至 Managed 專案的詳細資訊 \(以 Common Language Runtime 為目標\)，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [String Editor](../mfc/string-editor.md)   
 [字串](_win32_Strings)   
 [關於字串](_win32_About_Strings_cpp)