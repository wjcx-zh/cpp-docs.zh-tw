---
title: "BSCMAKE 選項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCBscMakeTool.OutputFile"
  - "VC.Project.VCBscMakeTool.SuppressStartupBanner"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/v BSCMAKE 選項"
  - "Iu BSCMAKE 選項"
  - "瀏覽資訊檔 (.bsc)，內容"
  - "/Er BSCMAKE 選項"
  - "NOLOGO BSCMAKE 選項"
  - "/s BSCMAKE 選項"
  - "/Ei BSCMAKE 選項"
  - "/o BSCMAKE 選項"
  - "/NOLOGO BSCMAKE 選項"
  - "/Iu BSCMAKE 選項"
  - "s BSCMAKE 選項 (/s)"
  - "/Em BSCMAKE 選項"
  - "Em BSCMAKE 選項"
  - "Es BSCMAKE 選項"
  - "檔案 [c + +]，BSCMAKE"
  - "Er BSCMAKE 選項"
  - "BSCMAKE，控制檔案的選項"
  - "控制 BSCMAKE 選項"
  - "El BSCMAKE 選項"
  - "/El BSCMAKE 選項"
  - "/Es BSCMAKE 選項"
  - "Ei BSCMAKE 選項"
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# BSCMAKE 選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節說明用來控制 BSCMAKE 的選項。  有許多選項可以透過排除或包含某些資訊的方式來控制瀏覽資訊檔的內容。  排除選項可以加快 BSCMAKE 的執行速度，也可以產生較小的 .bsc 檔。  選項名稱是區分大小寫的 \(除了 **\/HELP** 及 **\/NOLOGO** 以外\)。  
  
 從 Visual Studio 開發環境內只能使用 **\/NOLOGO** 和 **\/o**。如需存取專案屬性頁的詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
 \/Ei \( `filename`...\)  
 從瀏覽資訊檔中排除指定的包含檔的內容。  若要指定多個檔案時，請以空格分隔名稱，並將清單置於括號內。  如果只指定一個 `filename`，則不需要使用括號。  當 **\/Ei** 和 **\/Es** 選項一起使用時，可以排除未被 **\/Es** 排除的檔案。  
  
 \/El  
 排除區域符號。  預設情況是包含區域符號。  如需區域符號的詳細資訊，請參閱[建立 .sbr 檔](../../build/reference/creating-an-dot-sbr-file.md)。  
  
 \/Em  
 排除巨集主體中的符號。  使用 **\/Em**，只在瀏覽資訊檔中包含巨集名稱。  預設情況是同時包含巨集名稱和巨集展開 \(Macro Expansion\) 的結果。  
  
 \/Er \( `symbol`...\)  
 從瀏覽資訊檔中排除指定的符號。  若要指定多個符號名稱，請以空格分隔名稱，並將清單置於括號內。  如果只指定一個 `symbol`，則不需要使用括號。  
  
 \/Es  
 從瀏覽資訊檔中排除以絕對路徑指定的包含檔，或是以 INCLUDE 環境變數所指定之絕對路徑中的每一個包含檔 \(通常這些都是系統包含檔，其中包含許多可能在瀏覽資訊檔中並不需要的資訊\)。這個選項不會排除沒有指定路徑的檔案、以相對路徑指定的檔案或是 INCLUDE 中相對路徑下所找到的檔案。  您可以和 **\/Es** 一起使用 **\/Ei** 選項來排除 **\/Es** 未排除的檔案。  如果您只希望排除某些 **\/Es** 排除的檔案，請使用 **\/Ei** \(而不是 **\/Es**\) 並列出所要排除的檔案。  
  
 \/errorreport:\[none &#124; prompt &#124; queue &#124; send\]  
 允許您傳送有關 bscmake.exe 中內部錯誤的資訊給 Microsoft。  
  
 如需 **\/errorreport** 的詳細資訊，請參閱 [\/errorReport \(回報編譯器內部錯誤\)](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 \/HELP  
 顯示 BSCMAKE 命令列語法的摘要。  
  
 \/Iu  
 包含未參考的符號。  預設情況下，BSCMAKE 不會記錄任何已定義但未被參考的符號。  如果 .sbr 檔已經封裝，則這個選項不會影響輸入檔案，因為編譯器已經移除了未被參考的符號。  
  
 \/n  
 強制執行非累加建置。  使用 **\/n** 可以強制執行瀏覽資訊檔的完整建置，不論 .bsc 檔是否存在，並可防止 .sbr 檔被截斷。  請參閱 [BSCMAKE 如何建置 .bsc 檔](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md)。  
  
 \/NOLOGO  
 隱藏 BSCMAKE 的著作權訊息。  
  
 \/o `filename`  
 指定瀏覽資訊檔的名稱。  預設情況下，BSCMAKE 會給予瀏覽資訊檔第一個 .sbr 檔的主檔名和 .bsc 副檔名。  
  
 \/S \( `filename`...\)  
 告訴 BSCMAKE 第一次遇到指定的包含檔時要加以處理，其他時候則排除。  當檔案 \(例如 .c 或 .cpp 原始程式檔的標頭檔或 .h 檔\) 被包含於多個原始程式檔中，但是每一次都不會被前置處理器指示詞 \(Preprocessing Directive\) 改變時，使用這個選項可節省處理時間。  當檔案被對建立之瀏覽資訊檔而言不重要的方法變更時，您可能也會希望使用這個選項。  若要指定多個檔案時，請以空格分隔名稱，並將清單置於括號內。  如果只指定一個 `filename`，則不需要使用括號。  當您希望每一次檔案被包含時都加以排除，請使用 **\/Ei** 或 **\/Es** 選項。  
  
 \/v  
 提供詳細輸出，包含每一個處理的 .sbr 檔名稱以及與完整 BSCMAKE 執行相關的資訊。  
  
 \/?  
 顯示 BSCMAKE 命令列語法的簡短摘要。  
  
 下列命令列告訴 BSCMAKE 從三個 .sbr 檔執行 MAIN.bsc 的完整建置。  它也告訴 BSCMAKE 排除重複的 TOOLBOX.h 執行個體 \(Instance\)：  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## 請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)