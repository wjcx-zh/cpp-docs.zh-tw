---
title: "指定自訂建置工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets"
  - "VC.Project.VCCustomBuildTool.Outputs"
  - "VC.Project.VCCustomBuildTool.Command"
  - "VC.Project.VCCustomBuildTool.CommandLine"
  - "VC.Project.VCCustomBuildTool.AdditionalDependencies"
  - "VC.Project.VCCustomBuildTool.Message"
  - "VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets"
  - "VC.Project.VCCustomBuildTool.Description"
  - "VC.Project.VCCustomBuildTool.AdditionalInputs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建置工具 (C++), 指定"
  - "組建 (C++), 自訂建置工具"
  - "自訂建置工具 (C++), 指定"
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 指定自訂建置工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*自訂建置工具*可以為建置系統提供建置特定輸入檔所需的資訊。  自訂建置工具可指定要執行的命令、輸入檔的清單、由命令產生之輸出檔的清單，以及工具的選擇性描述。  
  
 如需自訂建置工具和自訂建置步驟的一般資訊，請參閱[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)。  
  
### 若要指定自訂建置工具  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../ide/working-with-project-properties.md)。  
  
2.  按一下 \[**組態屬性**\] 以啟用 \[**組態**\] 方塊。  在 \[**組態**\] 方塊中，選取您要指定自訂建置工具的組態。  
  
3.  在 \[**方案總管**\] 中，選取自訂建置工具的輸入檔。  
  
     如果 \[**自訂建置工具**\] 資料夾沒有出現，表示您選取之檔案的副檔名已和預設工具相關聯。  例如，.c 和 .cpp 檔案的預設工具為編譯器。  若要覆寫預設工具設定，請在 \[**一般**\] 資料夾之 \[**組態屬性**\] 節點的 \[**項目類型**\] 屬性中，按一下 \[**自訂建置工具**\]。  按一下 \[**套用**\] 時，便會顯示 \[**自訂建置工具**\] 節點。  
  
4.  在 \[**一般**\] 資料夾的 \[**自訂建置工具**\] 節點中，指定與自訂建置工具關聯的屬性：  
  
    -   在 \[**其他相依性**\] 中，指定除了正在定義其自訂建置工具以外的其他任何檔案 \(與自訂建置工具相關聯的檔案會隱含視為該工具的輸入\)。  自訂建置工具不一定要擁有其他輸入檔。  如果您有一個以上其他輸入，請以分號分隔它們。  
  
         如果 \[**其他相依性**\] 檔案的日期比輸入檔晚，就會執行自訂建置工具。  如果所有 \[**其他相依性**\] 檔案的日期都比輸入檔早，且輸入檔比 \[**輸出**\] 屬性檔早，那麼自訂建置工具就不會執行。  
  
         例如，假設您有一個自訂建置工具輸入時會使用 MyInput.x 而且會產生 MyInput.cpp，同時 MyInput.x 包含一個標頭檔 MyHeader.h。  那麼，您可以指定 MyHeader.h 做為 MyInput.x 的輸入相依性，如此一來，當 MyInput.cpp 對於 MyInput.x 或 MyHeader.h 已變為過時的時候，建置系統便會建置它。  
  
         輸入相依性也可以確保自訂建置工具可以按照您所需的順序執行。  在前面的範例中，假設 MyHeader.h 是某一個自訂建置工具的實際輸出。  由於 MyHeader.h 相依於 MyInput.x，所以建置系統會先建置 Myheader.h，然後才會在 MyInput.x 上執行自訂建置工具。  
  
    -   在 \[**命令列**\] 中指定命令，如同在命令提示字元中指定命令一般。  指定有效的命令或批次檔以及所有需要的輸入檔或輸出檔。  在批次檔名稱前面指定 **call** 批次命令，以確保所有的後續命令都會被執行。  
  
         多個輸入檔和輸出檔可利用 MSBuild 巨集以符號形式加以指定。  [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]以進一步了解如何指定檔案位置或檔案集合名稱，請參閱[建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)。  
  
         由於 MSBuild 會保留 '%' 字元，因此如果您指定環境變數，請將 **%** 逸出字元取代為 **%25** 十六進位逸出序列。  例如，將 **%WINDIR%** 取代為 **%25WINDIR%25**。  MSBuild 會在存取環境變數之前，將每個 **%25** 序列取代為 **%** 字元。  
  
    -   在 \[**描述**\] 中，輸入和此自訂建置工具相關的描述訊息。  當建置系統處理這個工具時，這個訊息會顯示在 \[**輸出**\] 視窗中。  
  
    -   在 \[**輸出**\] 裡，指定輸出檔的名稱。  這是個必要項；如果沒有這個屬性的值，自訂建置工具將不會執行。  如果自訂建置工具有一個以上輸出，請以分號分隔這些檔名。  
  
         輸出檔的名稱應該和在 \[**命令列**\] 屬性中指定的名稱相同。  專案建置系統將會尋找這個檔案並且檢查它的日期。  如果輸出檔比輸入檔新，或者找不到輸出檔，那麼自訂建置工具便會執行。  如果所有 \[**其他相依性**\] 檔案的日期都比輸入檔早，且輸入檔比 \[**輸出**\] 屬性中指定的檔案早，那麼自訂建置工具就不會執行。  
  
 如果您希望建置系統在自訂建置工具所產生的某個輸出檔上運作，必須以手動方式將它將入到專案。  自訂建置工具在建置過程中將會更新這個檔案。  
  
## 範例  
 假設您想要在專案中包括一個名為 parser.l 的檔案。  您想要由語彙分析來處理 parser.l，以產生一個主檔名 \(parser.c\) 相同的 .c 檔。  
  
 首先，您應該將 parser.l 和 parser.c 加入到專案。  如果這些檔案還不存在，您只需將這些檔案的參考加入。  接著，為 parser.l 建立自訂建置工具並且在 \[**命令**\] 屬性中輸入下列內容：  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 這個命令將會在 parser.l 上執行語彙分析並且輸出 parser.c 到專案目錄。  
  
 在 \[**輸出**\] 屬性中，輸入下列：  
  
```  
.\%(Filename).c  
```  
  
 當您建置專案時，建置系統會比較 parser.l 與 parser.c 的時間戳記。  如果 parser.l 比較新，或者 parser.c 不存在，建置系統便會執行 \[**命令列**\] 屬性的值讓 parser.c 成為目前最新的。  因為 parser.c 也已經加入到專案，所以建置系統接下來便會編譯 parser.c。  
  
## 請參閱  
 [建置命令和屬性的巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [疑難排解組建自訂](../ide/troubleshooting-build-customizations.md)