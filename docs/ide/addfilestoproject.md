---
title: "AddFilesToProject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddFilesToProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddFilesToProject 方法"
ms.assetid: 3ff11406-bb4a-4eb7-a8df-c655b964ff76
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddFilesToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將列於 Templates.inf 中的所有檔案加入至專案中。  
  
## 語法  
  
```  
  
      function AddFilesToProject(   
   oProj,   
   strProjectName,   
   InfFile    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
 `strProjectName`  
 專案的名稱。  
  
 *InfFile*  
 Templates.inf 檔案物件。  這個檔案包含精靈完成時所建立的檔名清單。  
  
## 備註  
 呼叫此函式將列於 Templates.inf 中的所有檔案加入至專案中。  您可以使用此函式來加入樣板檔、資源檔或說明檔。  
  
## 範例  
  
```  
// Assign the project path and project name.  
var strProjectPath = wizard.FindSymbol("PROJECT_PATH");  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Create the Visual C++ project and call it "MyProj"  
selProj = CreateProject(strProjectName, strProjectPath);  
selProj.Object.Keyword = "MyProj";  
  
// Add common and specific configurations to the project.  
AddCommonConfig(selProj, strProjectName);  
AddSpecificConfig(selProj, strProjectName);  
  
// Set the project filters  
SetFilters(selProj);  
  
// Create the project's Templates.inf file   
var InfFile = CreateInfFile();  
  
// Add the files in Templates.inf to the project.  
AddFilesToProject(selProj, strProjectName, InfFile);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [CreateInfFile](../ide/createinffile.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)