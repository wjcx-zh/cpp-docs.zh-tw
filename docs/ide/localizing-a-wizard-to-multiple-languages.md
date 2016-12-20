---
title: "將精靈當地語系化為多種語言 | Microsoft Docs"
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
  - "自訂精靈, 當地語系化"
  - "全球化 [C++], 精靈"
  - "當地語系化 [C++], 精靈"
  - "精靈 [C++], 當地語系化"
ms.assetid: 879885c2-fafd-44fd-8032-bf0c301f4f45
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將精靈當地語系化為多種語言
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立任何 Visual Studio 提供支援的語言之精靈。  根據預設，當您安裝 Visual Studio 時，它會辨識登錄中的地區設定 \(Locale\)，並對該地區設定提供適當的樣板。  
  
 Visual Studio 使用語言 ID 來辨識一個精靈所需要的語言支援。  根據預設，語言 ID 會設成登錄項目 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage 的十進位值。  如果精靈找不到語言項目，便會預設成英文 \(1033\)。  
  
> [!NOTE]
>  如需十進位語言值清單的詳細資訊，請參閱[其他語言的精靈支援](../ide/wizard-support-for-other-languages.md)。  
  
 此語言 ID 會指定成為 [HTML 檔案](../ide/html-files.md)和[樣板檔案](../ide/template-files.md)所在路徑的 [.vsz 檔案](../Topic/Configuring%20.Vsz%20Files%20to%20Start%20Wizards.md)的自訂參數。  
  
 您應為每個提供 .htm 檔案的每種語言指定路徑。  
  
## 範例  
 在 .vsz 檔中設定下列自訂參數，指示您提供英文 \(1033\)、日文 \(1041\) 和德文 \(1031\) 的 HTML：  
  
```  
Param="START_PATH\HTML\1033"  
Param="START_PATH\HTML\1041"  
Param="START_PATH\HTML\1031"  
Param="START_PATH\Templates\1033"  
Param="START_PATH\Templates\1041"  
Param="START_PATH\Templates\1031"  
```  
  
 上述自訂參數設定會以下列方式設定您的精靈目錄結構：  
  
```  
MyWizard1  
   HTML  
      1033  
         default.htm  
         myEnglishHTML.htm  
      1041  
         default.htm  
         myJapaneseHTML.htm  
      1031  
         default.htm  
         myGermanHTML.htm  
   Templates  
      1033  
         stdafx.h  
         stdafx.cpp  
      1041  
         stdafx.h  
         stdafx.cpp  
      1031  
         stdafx.h  
         stdafx.cpp  
   Images  
      HtmlPage1.bmp  
      HtmlPage2.jpg  
   Scripts  
      Default.js  
```  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [精靈 .Vsz 檔案中的自訂參數](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)