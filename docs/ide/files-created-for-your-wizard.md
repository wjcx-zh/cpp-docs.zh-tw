---
title: "您的精靈所建立的檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "自訂精靈, 刪除檔案"
  - "自訂精靈, 建立的檔案"
  - "檔案 [C++], 由自訂精靈建立"
  - "圖示, 刪除"
ms.assetid: 7f0e393c-395e-491b-add2-904cf8838e81
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 您的精靈所建立的檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的精靈會使用您在 \[**新增專案**\] 對話方塊的 \[**名稱**\] 方塊內的指定名稱來衍生某些檔案和類別的名稱。  
  
 [自訂精靈](../ide/custom-wizard.md)會將註解加入至它為您的精靈所建立的檔案中。  此自訂精靈也會在新的應用程式目錄中建立一個 readme.txt 文字檔。  這個檔案會說明其他由此自訂精靈所建立的新檔案之內容和用法。  
  
 下表說明了此自訂精靈所建立的檔案。  如需關鍵項目建立精靈的互動方式之詳細資訊，請參閱[設計精靈](../ide/designing-a-wizard.md)。  
  
|檔案|描述|  
|--------|--------|  
|[Project.vsz](../ide/dot-vsz-file-project-control.md)|一個類似舊式 .ini 格式的文字檔。  它會辨識精靈引擎，並提供內文和選擇性的[自訂參數](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。|  
|[Project.vsdir](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)|這是一個文字檔，可以讓 Visual Studio Shell 尋找精靈，並且將精靈顯示在 \[**新增專案**\] 對話方塊中。|  
|[HTML 檔案 \(選擇項\)](../ide/html-files.md)|精靈可以包含一個 HTML 介面的使用者介面 \(UI\)。  沒有 UI 的精靈便不包含 HTML 檔案。<br /><br /> 如果精靈有 UI，則精靈中的每個個別畫面都稱為「*頁面*」\(Page\)，而每個頁面都會指定 UI 功能。<br /><br /> default.htm 檔定義精靈的第一頁。  使用[應用程式設定、自訂精靈](../ide/application-settings-custom-wizard.md)的 \[**頁數**\] 清單方塊可指定額外頁面。  每個額外頁面都由一個 Page\_*page\-number*.htm 檔案定義，其中 *page\-number* 的範圍可從 2 到您指定的頁數。|  
|[指令碼檔](../ide/jscript-file.md)|自訂精靈會為每個建立的精靈各建立一個 JScript 檔：default.js。  這個檔案包含可存取 Visual C\+\+ 精靈、程式碼和環境物件模型來自訂精靈的 JScript 函式。  您可在精靈的 default.js 檔中自訂和加入函式。<br /><br /> 此外，您的精靈也包含 [common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 檔，其包含常用的 JScript 函式，並供包括 Visual C\+\+ 用來建立其他專案類型的精靈在內的所有精靈共用。  如需詳細資訊，請參閱 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)。|  
|[範本](../ide/template-files.md)|精靈的樣板是指一個包含指示詞的文字檔之集合物件 \(Collection\)，這些指示詞會被剖析並插入至符號表中 \(視精靈使用者的選取而定\)。  此樣板文字檔會根據使用者輸入來進行轉譯，再加入至精靈所建立的專案。  取得適當資訊的方法，是直接存取精靈控制項的符號表。|  
|[Templates.inf](../ide/templates-inf-file.md)|一個文字檔，其會列出與該專案關聯的所有樣板。|  
|Default.vcxproj|一個 .xml 檔案，包含了該專案類型的相關資訊。|  
|Sample.txt|一個樣板檔案，顯示了您的精靈指示詞的使用方式。|  
|ReadMe.txt|一個樣板檔案，其包含了此自訂精靈所建立的每個檔案之摘要。|  
|Images \(選擇項\)|您可提供任何影像 \(例如圖示、GIF、BMP 和其他 HTML 支援的影像格式\) 來增強精靈的 UI。  沒有 UI 的精靈則不需要影像。|  
|Styles.css \(選擇項\)|一個定義 UI 樣式的檔案。  如果您的精靈沒有使用者介面，此自訂精靈便不會建立 .css 檔。|  
  
 如果您刪除了精靈檔案和目錄，就必須同時刪除下列在 \\vc7\\vcprojects\\ 目錄內的檔案。  直到刪除這些檔案之前，這些精靈的圖示將會持續出現在**新增專案**對話方塊裡。  
  
-   *projectname*.vsz  
  
-   *projectname*.ico  
  
-   *projectname*.vsdir  
  
## 請參閱  
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)