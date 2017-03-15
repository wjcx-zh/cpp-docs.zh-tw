---
title: "疑難排解組建自訂 | Microsoft Docs"
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
  - "建置事件 [C++], 疑難排解"
  - "建置步驟 [C++], 疑難排解"
  - "組建 [C++], 建置事件"
  - "組建 [C++], 疑難排解"
  - "自訂建置步驟 [C++], 疑難排解"
  - "事件 [C++], 組建"
  - "疑難排解 [C++], 組建"
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 疑難排解組建自訂
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您的自訂建置步驟或事件行為有問題，有幾種方式可以讓您試著去了解是什麼地方出了問題。  
  
-   請確定自訂建置步驟產生的檔案是否與宣告為輸出的檔案相符。  
  
-   如果自訂建置步驟產生的任一檔案是其他建置步驟 \(自訂或其他\) 的輸入或相依性，請確定這些檔案是否已加入至您的專案。  並確定消耗那些檔案的工具會在自訂建置步驟之後執行。  
  
-   若要顯示自訂建置步驟的實際執行情形，請加入 `@echo on` 做為第一個命令。  建置專案時，會將建置事件與建置步驟會置於暫時的 .bat 檔案中。  因此，您可以在建置事件或建置步驟命令中加入錯誤檢查。  
  
-   檢查中繼檔案目錄中的建置記錄，看看實際上執行的是什麼。  路徑和建置記錄檔的名稱是以 **MSBuild** 巨集運算式 **$\(IntDir\)\\$\(MSBuildProjectName\).log** 表示。  
  
-   修改專案設定以收集超過建置記錄檔中預設的資訊量。  按一下 \[**選項**\] 功能表上的 \[**工具**\]。  在 \[**選項**\] 對話方塊中，按一下 \[**專案和方案**\] 節點，然後按一下 \[**建置並執行**\] 節點。  接著，按一下 \[**MSBuild 專案中建立記錄檔詳細等級**\] 方塊中的 \[**詳細**\]。  
  
-   驗證您所使用的任何檔名或目錄巨集的值。  您可以個別回應巨集，或者您可以將 `copy %0 command.bat` 加到自訂建置步驟的開頭，它會將自訂建置步驟的命令複製到 command.bat 並展開所有巨集。  
  
-   分別執行自訂建置步驟和建置事件來檢查它們的行為。  
  
## 請參閱  
 [了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)