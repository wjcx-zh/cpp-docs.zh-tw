---
title: "How to: Include Resources at Compile Time | Microsoft Docs"
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
  - "vs.resvw.resource.including"
  - "vc.resvw.resource.including"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compiling source code, including resources"
  - "comments [C++], compiled files"
  - "resources [Visual Studio], including at compile time"
  - "projects [C++], including resources"
  - "#include directive"
  - "include directive (#include)"
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Include Resources at Compile Time
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常可簡單且容易使用一個資源指令碼 \(.rc\) 檔中所有資源的預設排列方式。  不過，您可以在編譯時將其他檔案中的資源新增至目前的專案，方法是在 [&#91;資源包含&#93; 對話方塊](../windows/resource-includes-dialog-box.md)的 **\[編譯時期指示詞\]** 方塊中列出它們。  
  
 有幾個原因會在主要.rc 檔以外的檔案中放置資源：  
  
-   為了將註解新增至儲存 .rc 檔時不會刪除的資源陳述式。  
  
     資源編輯器不會直接讀取.rc 或 resource.h 檔。  資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。  此檔案是一個編譯步驟，只會儲存符號資料。  如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 \(例如註解\)。  每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 \(例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔\)。  資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。  
  
-   為了包含已開發及測試、而且不需要進一步修改的資源。  \(資源編輯器無法編輯不含 .rc 副檔名的任何加入的檔案。\)  
  
-   為了包含數個不同的專案正在使用的資源，或屬於原始程式碼版本控制系統的資源，因而必須存在中央位置，讓修改影響所有專案。  
  
-   為了包含自訂格式的資源 \(例如 RCDATA 資源\)。  RCDATA 資源可能會有特殊需求。  例如，您無法將運算式做為 nameID 欄位的值。  如需詳細資訊，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 文件。  
  
 如果現有的.rc 檔中有符合其中任何條件的區段，您應該將該區段置於一或多個個別.rc 檔，並使用 [&#91;資源包含&#93; 對話方塊](../windows/resource-includes-dialog-box.md)將其納入您的專案中。  新專案的 \\res 子目錄中建立的 *Projectname*.rc2 檔適用此工作。  
  
### 在編譯時期，於專案中包含資源  
  
1.  將資源放在包含唯一檔案名稱的資源指令碼檔案。  請勿使用 *projectname*.rc，因為這是用於主要資源指令碼檔案的檔案名稱。  
  
2.  在 \[[資源檢視](../windows/resource-view-window.md)\] 中，以滑鼠右鍵按一下 .rc 檔，然後從快顯功能表選擇 \[**資源包含**\]。  
  
3.  在 \[**編譯時期指示詞**\] 方塊中，加入 [\#include](../preprocessor/hash-include-directive-c-cpp.md) 編譯器指示詞，在開發環境中的主要資源檔內包含新的資源檔。  
  
     以這種方式包含的檔案中資源，都會在編譯時期成為可執行檔的一部分。  當您在專案的主要 .rc 檔上工作時，無法直接編輯或修改它們。  您需要個別開啟包含的 .rc 檔。  資源編輯器無法編輯不含 .rc 副檔名的任何加入的檔案。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)