---
title: "ConvertProjectToAttributed | Microsoft Docs"
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
  - "ConvertProjectToAttributed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertProjectToAttributed 方法"
ms.assetid: 56a2d6e1-7e8e-4595-b2be-ade026593798
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ConvertProjectToAttributed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將 ATL 非屬性化專案轉換成屬性化專案。  
  
## 語法  
  
```  
  
function ConvertProjectToAttributed( );  
  
```  
  
## 傳回值  
 如果成功地轉換專案則為 **True**，否則為 **False**。  
  
## 備註  
 呼叫此函式將 ATL 專案從非屬性化轉換成屬性化。  如需詳細資訊，請參閱[屬性化程式設計](../windows/attributed-programming-concepts.md)。  
  
## 範例  
  
```  
// Create a function called CheckAddtoProject.  
function CheckAddtoProject(oProj)  
{  
// Is the project attributed already?  
   try  
   {  
      if (!IsAttributedProject(wizard))  
      {  
         // If the project is not converted to attributed, return false.  
         if (!ConvertProjectToAttributed(oProj))  
            return false;  
      }  
   }  
   catch (e)  
   {  
      var L_ErrMsg1_Text = "Error in CheckAddtoProject: ";  
      wizard.ReportError( L_ErrMsg1_Text + e.description);  
      return false;  
   }  
  
   return true;  
}  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [CanAddNonAttributed](../ide/canaddnonattributed.md)