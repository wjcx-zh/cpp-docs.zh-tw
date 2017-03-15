---
title: "精靈 .Vsz 檔案中的自訂參數 | Microsoft Docs"
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
  - "ABSOLUTE_PATH 巨集"
  - "自訂精靈, .vsz 檔案"
  - "HTML_FILTER 巨集"
  - "HTML_PATH 巨集"
  - "IMAGE_FILTER 巨集"
  - "IMAGES_PATH 巨集"
  - "MISC_FILTER 巨集"
  - "PRODUCT 巨集"
  - "PRODUCT_INSTALLATION_DIR 巨集"
  - "PROJECT_TEMPLATE_NAME 巨集"
  - "PROJECT_TEMPLATE_PATH 巨集"
  - "RELATIVE_PATH 巨集"
  - "SCRIPT_COMMON_PATH 巨集"
  - "SCRIPT_FILTER 巨集"
  - "SCRIPT_PATH 巨集"
  - "START_PATH 巨集"
  - "TEMPLATE_FILTER 巨集"
  - "TEMPLATES_PATH 巨集"
  - "WIZARD_NAME 巨集"
  - "WIZARD_UI 巨集"
ms.assetid: 560dd5c0-7cff-4974-b856-5ca25b0669b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 精靈 .Vsz 檔案中的自訂參數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此 .vsz 檔案會在其前兩行中辨識精靈版本，和要共同建立的精靈之 ProgID 或 CLSID。  此 .vsz 檔案也可以包含要加入至符號表 \(連同 HTML 符號區段中提供的符號\) 的選擇性內文參數和自訂參數。  
  
 <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> 方法會顯示精靈，而該精靈會將定義在 .vsz 檔案中的內容和自訂參數之陣列做為其參數。  
  
 下列常用的符號被指定為在 [.vsz 檔案](../ide/dot-vsz-file-project-control.md)或 .htm 檔案中的自訂參數，並可用於精靈 HTML 檔案、指令碼檔或樣板檔案中。  
  
## 範例  
 如下列 .vsz 檔案項目指示，名為 MyProjWiz 的精靈包含了一個使用者介面。  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine  
Param="WIZARD_NAME = MyProjWiz"  
Param="WIZARD_UI = TRUE"  
```  
  
### 精靈 .vsz 檔案中的自訂精靈符號  
  
|符號|定義|  
|--------|--------|  
|ABSOLUTE\_PATH|精靈檔案的位置。|  
|HTML\_FILTER|指定在 .vsz 檔案中。  置於**方案總管**的 \[HTML 檔案\] 資料夾內的檔案類型。  通常指定為「htm」。|  
|HTML\_PATH|指定在 .vsz 檔案中。  精靈 [HTML 檔案](../ide/html-files.md)的位置。  根據預設，它是 START\_PATH\\HTML\\ *LANGUAGE* \(其中 *LANGUAGE* 是您的系統登錄所指定的地區設定。 **Note:**  您可將 \<LangID\> 設為 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage 的十進位值，來指定不同的語言。  如需詳細資訊，請參閱[將精靈當地語系化為多種語言](../ide/localizing-a-wizard-to-multiple-languages.md)。  如需十進位語言值清單的詳細資訊，請參閱[其他語言的精靈支援](../ide/wizard-support-for-other-languages.md)。|  
|IMAGE\_FILTER|指定在 .vsz 檔案中。  置於 \[方案總管\] 的 \[影像檔\] 資料夾內的檔案類型。  通常指定為「bmp;gif」。|  
|IMAGES\_PATH|指定在 .vsz 檔案中。  html 檔案中使用的影像檔之位置。  根據預設，其為 START\_PATH\\Images。|  
|MISC\_FILTER|指定在 .vsz 檔案中。  置於 \[方案總管\] 中的 \[雜項\] 資料夾內的檔案類型。  通常指定為 「vsz;vsdir;ico;vcproj;csproj;css;inf」。|  
|PRODUCT|根據預設，設成 Visual C\+\+；不過，您可將此值設成 Visual Basic 來建立 Visual Basic 精靈等等。|  
|PRODUCT\_INSTALLATION\_DIR|列示於 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\\<Product\>\\ ProductDir 登錄機碼的目錄。|  
|PROJECT\_TEMPLATE\_NAME|指定在 .vsz 檔案中。  精靈用來建立專案的專案樣板檔案。  通常指定為「txt」。|  
|PROJECT\_TEMPLATE\_PATH|這個目錄包含專案的[樣板檔案](../ide/template-files.md)。  在 Visual C\+\+ 中，其預設值為 PRODUCT\_INSTALLATION\_DIR\\VCWizards。|  
|RELATIVE\_PATH|如果找不到 ABSOLUTE\_PATH，則考慮 RELATIVE\_PATH。  這是相對於 PRODUCT\_INSTALLATION\_DIR 的路徑。  在 Visual C\+\+ 中，RELATIVE\_PATH 為 PRODUCT\_INSTALLATION\_DIR\\VCWizards。|  
|SCRIPT\_COMMON\_PATH|相對於 PRODUCT\_INSTALLATION\_DIR 的目錄名稱，其中可找到通用指令碼檔。  例如，在 Visual C\+\+ 中，這是 VCWizards。|  
|SCRIPT\_FILTER|指定在 .vsz 檔案中。  置於 \[方案總管\] 的 \[指令碼檔\] 資料夾內的檔案類型。  通常指定為「js」\(JScript\) 或「vbs」\(VBScript\)。|  
|SCRIPT\_PATH|精靈 [JScript 檔案](../ide/jscript-file.md)的位置。  根據預設，其為 START\_PATH\\Scripts|  
|START\_PATH|指定在 .vsz 檔案中。  這不是由使用者所設定，而是在內部用來辨識 RELATIVE\_PATH 或 ABSOLUTE\_PATH。  精靈名稱 \(WIZARD\_NAME\) 會附加至這個值上。|  
|TEMPLATE\_FILTER|指定在 .vsz 檔案中。  置於 \[方案總管\] 的 \[樣板檔案\] 資料夾內的檔案類型。  通常指定為「txt」。|  
|TEMPLATES\_PATH|指定在 .vsz 檔案中。  精靈樣板檔案的位置。  根據預設，其為 START\_PATH\\Templates\\\<LangID\>。 **Note:**  如需 LangID 的詳細資訊，請參閱 HTML\_PATH。|  
|WIZARD\_NAME|指定精靈名稱。  位於 .vsz 中，並由符號的其餘部分使用。|  
|WIZARD\_UI|指定在 .vsz 檔案中。  一個布林 \(Boolean\) 值，其指出精靈是否含有使用者介面。  有使用者介面即指定 **TRUE**，沒有使用者介面則指定 **FALSE**。|  
  
## 請參閱  
 <xref:EnvDTE.IDTWizard.Execute%2A>   
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)