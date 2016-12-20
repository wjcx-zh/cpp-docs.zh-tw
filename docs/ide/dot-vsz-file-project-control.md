---
title: ".Vsz 檔案 (專案控制) | Microsoft Docs"
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
  - ".vsz 檔案"
  - "自訂精靈, .vsz 檔案"
  - "自訂精靈, 專案控制項檔案"
  - "檔案 [C++], 由自訂精靈建立"
  - "vsz 檔案"
ms.assetid: b8678fee-6795-46d1-9338-48b22d5e9207
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# .Vsz 檔案 (專案控制)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每一個精靈的起點都是 .vsz 檔案。  .vsz 檔案是一個文字檔，其決定要呼叫的精靈以及要傳遞給精靈的資訊。  這個檔案含有兩行標題，後接要傳遞給精靈的不同選擇性參數。  如需選擇性參數的清單，請參閱[預先定義的自訂精靈符號](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。  
  
 下列範例顯示 .vsz 檔案中的標題：  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine.10.0  
Param="WIZARD_NAME = My AppWizard"  
```  
  
-   標題的第一行會指定範本檔案格式的版本號碼。  您可以將此號碼指定為 `6.0`、`7.0` 或 `7.1`。  其他數字都無效，使用其他數字會造成「無效的格式」錯誤。  
  
-   第二行將 **Wizard** 變數設定為由 Visual Studio 所共同建立之精靈的 ProgID。  ProgID 是 CLSID 的字串表示，例如 `VsWizard.VsWizardEngine.10.0`。  
  
     如果您的精靈具有使用者介面，則此 ProgID 會自動指定精靈以實作 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>。  根據預設，這個介面的方法是用於專案的 [.htm 檔案](../ide/html-files.md)。  您可在 .htm 檔案中使用這個介面的方法，以變更精靈的行為。  如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>，它是 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI> 的 coclass。  
  
-   在這兩行後面是一份選擇性參數清單，其可讓 .vsz 檔案傳遞其他自訂參數給精靈。  每一個值都是以精靈控制項的 <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> 方法中不同變數陣列的字串元素方式傳遞。  根據預設，具有使用者介面的精靈會產生下列預設參數：  
  
    ```  
    Param="START_PATH = <path to the wizard>"  
    Param="HTML_PATH = <path to the wizard's HTML file>"  
    Param="TEMPLATES_PATH = <path to the wizard's template file>"  
    Param="SCRIPT_PATH = <path to the wizard's script files>"  
    Param="IMAGES_PATH = <path to the wizard's images>"  
    ```  
  
     如果您的精靈沒有使用者介面，它便不會有 `IMAGES_PATH` 參數，而是包含下列參數：  
  
    ```  
    Param="WIZARD_UI = FALSE"  
    Param="SOURCE_FILTER = txt"  
    ```  
  
-   這個 .vsz 檔案可包含下列參數，這些參數可以指定可在 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 檔中找到的函式：  
  
    ```  
    Param="PREPROCESS_FUNCTION = CanAddATLClass"  
    Param="PREPROCESS_FUNCTION = CanAddMFCClass"  
    Param="PREPROCESS_FUNCTION = CanAddClass"  
    ```  
  
 精靈會呼叫 [CanAddATLClass](../ide/canaddatlclass.md)、[CanAddMFCClass](../ide/canaddmfcclass.md) 和 [CanAddClass](../ide/canaddclass.md) 等函式，來確認可使用 [Visual C\+\+ 程式碼模型](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)。  如果有一個函式傳回 **false**，精靈就不會啟動。  
  
 您可將精靈加入至 Visual Studio 中的 \[**新增專案**\] 對話方塊的 \[範本\] 窗格中，方法為將 .vsz 檔案置於 vcprojects 目錄中。  自訂精靈預設會將 .vsz 檔寫入這個目錄。  
  
> [!NOTE]
>  如果您刪除了精靈檔案和目錄，您便必須同時刪除該專案在 vcprojects 目錄中的 .vsz 檔、.vsdir 檔和 .ico 檔。  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [Visual C\+\+ Wizard Model](http://msdn.microsoft.com/zh-tw/159395ac-33c7-47bf-ad42-4e1435ddc758)   
 [使用 .Vsdir 檔案將精靈加入至加入項目和新增專案對話方塊](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)   
 [設計精靈](../ide/designing-a-wizard.md)