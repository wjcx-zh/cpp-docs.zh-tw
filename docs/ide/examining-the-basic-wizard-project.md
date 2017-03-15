---
title: "檢查基本精靈專案 | Microsoft Docs"
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
  - "自訂精靈, 建立的檔案"
  - "自訂精靈, 精靈專案"
ms.assetid: c6423e3c-ddb0-43e0-b8e5-9e3a98a7908c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 檢查基本精靈專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在使用[自訂精靈](../ide/creating-a-custom-wizard.md)建立基本專案之後，請檢查自訂精靈為您建立的檔案。  
  
1.  在**方案總管**中，展開專案，並檢查精靈為您的專案所建立的[檔案](../ide/files-created-for-your-wizard.md)。  
  
2.  按兩下 Default.js，在程式碼編輯器中開啟專案的 [JScript 檔案](../ide/jscript-file.md)。  這個檔案包含當使用者在精靈中按一下 \[完成\] 時，就會建立專案的 JScript 函式。  請檢視這個檔案中的函式和 TODO 註解。  
  
3.  如果您的專案具有使用者介面，請查看標示為 [HTML 檔案](../ide/html-files.md)的資料夾，並注意您具有在自訂精靈的[應用程式設定](../ide/application-settings-custom-wizard.md)頁面中所指定的相同數目之 .htm 檔案。  按兩下 Default.htm，在 [HTML 設計工具](../Topic/HTML%20Designer.md)中開啟專案的主 HTML 網頁。  您可在 [Design View](../Topic/Design%20View1.md) 或 HTML 檢視中，以 [HTML 標記](http://msdn.microsoft.com/zh-tw/7bb90672-b36a-4cf9-9bbc-677c9b956318)的方式來檢視 HTML。  切換至 HTML 標記檢視，然後檢閱 HTML 標記。  按一下 \[僅指令碼檢視\] 按鈕 \(位於 HTML 檢視編輯視窗的右上角，在 \[事件\] 下拉式清單 \(Drop\-Down List\) 旁邊\)，然後檢查 .htm 檔案中的 JScript。  根據預設，這個檔案包含初始化和載入此精靈的 JScript 函式，並提供 **IVCWizCtrlUI** 介面的預設行為。  如需詳細資訊，請參閱 coclass <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl> 物件。  
  
4.  儲存並關閉精靈專案。  
  
5.  開啟 Visual Studio \[**新增專案**\] 對話方塊，然後尋找您的精靈圖示。  按兩下該圖示來顯示您的精靈。  您可檢查自訂精靈為您建立的基本精靈頁面。  請注意，第一頁包含一些 HTML 控制項範例，和標準的 \[完成\]、\[取消\] 和 \[說明\] 按鈕。  
  
6.  按一下 \[完成\]，使用您的精靈建置新的專案。  根據預設，您的精靈會建立 ReadMe.txt 和 Sample.txt 兩個文字檔。  這些檔案會描述您的精靈所建立的專案。  關閉這個專案，然後重新開啟您的精靈專案。  
  
7.  閱讀[檢查精靈的結構](../ide/examining-the-mechanics-of-a-wizard.md)，進一步了解 Visual Studio 環境，以及當您執行精靈時 Visual C\+\+ 精靈引擎會如何建立您要建立的專案。  
  
 現在您可以開始[自訂精靈](../ide/customizing-your-wizard.md)。  
  
## 請參閱  
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈步驟](../ide/steps-to-designing-a-wizard.md)   
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [提供即時線上說明](../ide/providing-context-sensitive-help.md)   
 [自訂精靈](../ide/customizing-your-wizard.md)