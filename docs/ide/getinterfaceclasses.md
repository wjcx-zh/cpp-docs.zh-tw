---
title: "GetInterfaceClasses | Microsoft Docs"
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
  - "GetInterfaceClasses"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceClasses 方法"
ms.assetid: 712c112f-b4ff-43c4-ad49-c4f4c13c48bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetInterfaceClasses
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回與介面相關聯的 `VCCodeClass` 物件。  
  
## 語法  
  
```  
  
      function GetInterfaceClasses(   
   strInterface,   
   oProject,   
   aryClasses    
);  
```  
  
#### 參數  
 *strInterface*  
 包含類別物件的介面名稱。  
  
 *oProject*  
 選取的專案。  
  
 *aryClasses*  
 \[輸出\] 介面中的類別物件陣列。  
  
## 傳回值  
 與介面相關聯的 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeClass> 物件。  
  
## 備註  
 呼叫此函式以取得與介面相關聯的類別。  
  
## 範例  
  
```  
var aryClasses = new Array();  
GetInterfaceClasses(oInterface.Name, selProj, aryClasses);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetInterfaceType](../ide/getinterfacetype.md)