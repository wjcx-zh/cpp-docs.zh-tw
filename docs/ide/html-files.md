---
title: "HTML 檔案 | Microsoft Docs"
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
  - "自訂精靈, HTML 檔案"
  - "自訂精靈, 使用者介面"
  - "檔案 [C++], 由自訂精靈建立"
  - "HTML 網頁, 自訂精靈的使用者介面"
  - "精靈的使用者介面"
  - "精靈 [C++], 自訂精靈的使用者介面"
ms.assetid: 3b6ed080-6560-418b-b908-d84d71bdf145
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HTML 檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

精靈可包含是 HTML 介面的使用者介面。  連同 Default.htm，精靈可包含任何數目的 .htm 檔案，您可在[自訂精靈](../ide/custom-wizard.md)中的 \[**頁數**\] 方塊內指出該數目。  每一個 .htm 檔案都代表您精靈的 HTML 網頁，您可使用 `Next` 和 \[上一頁\] 按鈕、標籤，或是您在精靈設計中所指定的任何其他格式來存取該 HTML 網頁。  
  
 HTML 包含：  
  
-   SYMBOL 標籤，它可辨識使用者定義選項的預設值。  當使用者按一下 \[完成\] 時，符號會寫入符號表，例如：  
  
```  
<SYMBOL NAME='HEADER_FILE' VALUE='MyHeader.h' TYPE=text></SYMBOL>  
```  
  
 在精靈使用者介面 \(UI\) 中，符號表內被辨識為「HEADER\_FILE」的文字方塊含有預設文字「MyHeader.h」。  您可在精靈使用者介面中變更這個值，而在您按一下 \[完成\] 時，結果值會寫入專案的符號表中，例如：  
  
```  
<SYMBOL NAME='CHECKBOX1' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
 在精靈使用者介面中，根據預設，會清除在符號表內被辨識為「CHECKBOX1」的核取方塊。  您可在 HTML 使用者介面中選取這個方塊，而在您按一下 \[完成\] 時，結果值會寫入符號表中。  
  
 每一個 .htm 檔案都會將使用者的選取記錄到符號表。  
  
-   包含 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) \(其包含通用且有用的 JScript 函式\) 和 Default.js。  
  
-   可顯示於 HTML 的專案影像參考。  
  
-   可自訂精靈的使用者介面外觀之 HTML 文字和格式  
  
-   可存取 Visual C\+\+ 精靈物件模型以提供該精靈的自訂行為之 JScript 函式。  這些函式位於標題為 \<SCRIPT LANGUAGE\='JSCRIPT'\> 的 HTML 網頁區段中，如下列範例所示。  
  
    > [!NOTE]
    >  若要從 HTML 存取精靈和環境物件模型，請在物件模型項目前附加 "window.external"。  
  
    ```  
    function InitDocument(document)  
    {  
       setDirection();  
  
       if (window.external.FindSymbol('DOCUMENT_FIRST_LOAD'))  
       {  
          // This function sets the default symbols based   
          // on the values specified in the SYMBOL tags above  
          //  
          window.external.SetDefaults(document);  
       }  
  
       // Load the document and initialize the controls   
       // with the appropriate symbol values  
       //  
       window.external.Load(document);  
    }  
    ```  
  
 以下為主控台應用程式 \(Console Application\) 精靈範例：  
  
```  
<SYMBOL NAME='WIZARD_DIALOG_TITLE' TYPE=text VALUE='Console Application Wizard'></SYMBOL>  
  
<SYMBOL NAME='EMPTY_PROJECT' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_ATL' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_MFC' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)