---
title: "自訂精靈 | Microsoft Docs"
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
  - "自訂精靈"
  - "自訂精靈, 在 Visual C++ 專案中建立"
ms.assetid: a3ff1c81-3eef-41e7-a6bc-2f98e4bf423f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自訂精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您必須在使用[自訂精靈](../ide/application-settings-custom-wizard.md)自訂您建立的精靈時，考量下列共同的工作。  
  
-   在 .vsz 檔案中，指定任何讓精靈能作業的必要自訂參數。  如需詳細資訊，請參閱 [.vsz 檔案 \(專案控制\)](../ide/dot-vsz-file-project-control.md) 和[預先定義的自訂精靈符號](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。  
  
     如果您將精靈當地語系化為數種不同的語言，請將該語言參數加入至 .vsz 檔案。  如需詳細資訊，請參閱[將精靈當地語系化為多種語言](../ide/localizing-a-wizard-to-multiple-languages.md)。  
  
-   自訂[樣板檔案](../ide/template-files.md) \(和 [Templates.inf](../ide/templates-inf-file.md)\) 來指定用於使用者選取的指示詞。  
  
-   自訂 [Default.js 檔](../ide/jscript-file.md)來指定精靈的其他特殊處理方式。  您可撰寫您自己的函式，也可以使用 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 中提供的函式。  
  
-   設計圖示以及您的 HTML 使用者介面要使用的其他影像。  
  
-   設計 HTML 使用者介面。  
  
-   將符號加入至 HTML 符號表，以符合您的精靈使用的按鈕、控制項、文字方塊和其他項目。  
  
     以下顯示自訂精靈所提供之 HTML 的摘錄：  
  
    ```  
    <SYMBOL NAME="WIZARD_DIALOG_TITLE" TYPE=text VALUE="MyCustomWiz">  
          </SYMBOL>  
    <SYMBOL NAME="SAMPLE_CHECKBOX" TYPE=checkbox VALUE=true>  
          </SYMBOL>  
    ```  
  
     這個名為 MyCustomWiz 的精靈顯示一個預設選取的核取方塊。  
  
-   在 HTML 檔案中標示為 `<SCRIPT LANGUAGE="JSCRIPT">` 的區段中，加入 JScript 函式呼叫，並存取 Visual Studio 物件模型來自訂精靈的行為。  您必須依下列方式使用 `window.external` 來呼叫這些函式：  
  
    ```  
    window.external.AddSymbol("MAIN_FRAME_DEFAULT_STYLES", true);  
    window.external.AddSymbol("MAIN_FRAME_STYLE_FLAGS", "");  
    ```  
  
    > [!NOTE]
    >  透過 [Visual Studio 的 Automation 和擴充性](../Topic/Automation%20and%20Extensibility%20for%20Visual%20Studio.md)、[Visual C\+\+ 程式碼模型](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)、[專案模型](http://msdn.microsoft.com/zh-tw/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)和[精靈模型](http://msdn.microsoft.com/zh-tw/159395ac-33c7-47bf-ad42-4e1435ddc758)公開的方法、屬性和事件，可以讓您在 JScript 檔和 .htm 檔中，以程式設計的方式管理精靈專案從建立到建置 \(Build\) 的所有層面。  
  
-   必要時，請自訂 [.vsdir 檔案](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)，讓 Shell 能瞭解 .vsz 檔案和其他所有樣板的相關資訊。  例如，指示圖示資源 ID、旗標、當地語系化名稱等等。  
  
-   建立精靈必須當地語系化成之所有語言的 .htm 檔案和樣板檔案。  將它們加入至適當的專案目錄。  
  
-   提供精靈的[顯示即時線上說明](../ide/providing-context-sensitive-help.md)。  
  
## 請參閱  
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈步驟](../ide/steps-to-designing-a-wizard.md)   
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [提供即時線上說明](../ide/providing-context-sensitive-help.md)   
 [精靈的錯誤處理](../ide/handling-errors-in-wizards.md)