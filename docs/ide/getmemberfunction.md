---
title: "GetMemberfunction | Microsoft Docs"
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
  - "GetMemberFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMemberfunction 方法"
ms.assetid: 1e610977-9bc7-4ff2-a79f-132c8e913b4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetMemberfunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呼叫此函式可根據指定名稱來取得函式物件。  
  
## 語法  
  
```  
  
      function GetMemberfunction(   
   oClass,   
   strFuncName,   
   oProj    
);  
```  
  
#### 參數  
 *oClass*  
 選取的類別物件。  
  
 `strFuncName`  
 要擷取的函式名稱。  
  
 `oProj`  
 選取的專案。  
  
## 傳回值  
 由 `strFuncName` 所表示的函式。  
  
## 備註  
 呼叫此函式可根據指定名稱來取得函式物件。  如需詳細資訊，請參閱＜Visual C\+\+ 程式碼模型＞中的 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeModel.Functions%2A>。  
  
## 範例  
  
```  
// Gets the function ExitInstance from the class CWinApp in the   
// current project.  
var oExitInstance = GetMemberFunction(oCWinApp, "ExitInstance", oProj);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)