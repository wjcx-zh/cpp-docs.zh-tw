---
title: "CreateProject | Microsoft Docs"
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
  - "CreateProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateProject 方法"
ms.assetid: b5598b46-fe29-4ad0-8bfe-a4dc789aeebd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreateProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立 C\+\+ 專案。  
  
## 語法  
  
```  
  
      function CreateProject(   
   strProjectName,   
   strProjectPath    
);  
```  
  
#### 參數  
 `strProjectName`  
 包含專案名稱的字串。  
  
 *strProjectPath*  
 包含專案路徑的字串。  
  
## 傳回值  
 專案物件。  
  
## 備註  
 呼叫此函式會建立一個可於 Visual Studio 中開啟的 C\+\+ 專案。  如果精靈的 **WizardType** 內容參數被指定為 **vsWizardAddSubProject**，則會將此專案當做子專案加入至現有的專案中。  如需詳細資訊，請參閱 [ContextParams 列舉](../Topic/Context%20Parameters%20for%20Launching%20Wizards.md)。  
  
## 範例  
 請參閱 [AddFilesToProject](../ide/addfilestoproject.md)。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)