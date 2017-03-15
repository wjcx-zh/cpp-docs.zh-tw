---
title: "Templates.inf 檔案 | Microsoft Docs"
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
  - "自訂精靈, 範本檔案"
ms.assetid: 93d60d27-2402-4dc8-a829-e97417ccea49
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Templates.inf 檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Templates.inf 是一個文字檔，其包含要對專案轉譯的樣板清單。  
  
 由於 Templates.inf 本身是一個[樣板檔案](../ide/template-files.md)，因此您可使用指示詞來指出要在專案中併入哪些檔案 \(視使用者的選擇而定\)。  如需可在這個檔案中使用的指示詞清單，請參閱[樣板指示詞](../ide/template-directives.md)。  
  
## 範例  
  
```  
Template1.txt  
Template2.txt  
  [!if TYPE_A]  
TemplateOptionA.h  
TemplateOptionA.cpp  
  [!else]  
TemplateOptionB.h  
TemplateOptionB.cpp  
  [!endif]  
```  
  
 **CreateCustomInfFile** 會將 Templates.inf 轉譯成暫存文字檔，該檔案在檔案處理之後必須刪除。  
  
## 範例  
  
```  
var InfFile = CreateCustomInfFile();  
AddFilesToProject(selProj, strProjectName, InfFile);  
InfFile.Delete();  
```  
  
 如需詳細資訊，請參閱 [JScript 檔案](../ide/jscript-file.md)。  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)