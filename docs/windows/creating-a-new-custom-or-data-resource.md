---
title: "Creating a New Custom or Data Resource | Microsoft Docs"
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
  - "custom resources [C++]"
  - "data resources [C++]"
  - "resources [Visual Studio], creating"
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a New Custom or Data Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立新的自訂或資料資源，方法是將資源放在使用一般資源指令碼 \(.rc\) 檔語法的個別檔案中，然後以滑鼠右鍵按一下方案總管中的專案，再按一下捷徑功能表中的 \[資源包含\] 來包含該檔案。  
  
### 建立新的自訂或資料資源  
  
1.  [建立 .rc 檔](../windows/how-to-create-a-resource-script-file.md)，其中包含自訂或資料資源。  
  
     您可以在 .rc 檔中，將自訂資料輸入為以 Null 結尾並加上引號的字串，或是十進位、十六進位或八進位格式的整數。  
  
2.  在**方案總管**中，以滑鼠右鍵按一下專案的 .rc 檔，然後按一下捷徑功能表中的 \[資源包含\]。  
  
3.  在 \[編譯時期指示詞\] 方塊中輸入 **\#include** 陳述式，為包含您的自訂資源的檔案命名。 例如：  
  
    ```  
    #include mydata.rc  
    ```  
  
     請確定您輸入的語法和拼字正確。 \[編譯時期指示詞\] 方塊的內容會完全依照您的輸入插入資源指令碼檔。  
  
4.  按一下 \[確定\] 記錄您的變更。  
  
 另一種建立自訂資源的方式是匯入外部檔案作為自訂資源。 如需詳細資訊，請參閱[匯入及匯出資源](../windows/how-to-import-and-export-resources.md)。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Binary Editor](../mfc/binary-editor.md)