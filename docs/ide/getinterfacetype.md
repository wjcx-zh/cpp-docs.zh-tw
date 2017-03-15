---
title: "GetInterfaceType | Microsoft Docs"
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
  - "GetInterfaceType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceType 方法"
ms.assetid: cc6403a8-0c2b-47f7-a8f7-9db95df87d5a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetInterfaceType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得介面的型別。  
  
## 語法  
  
```  
  
      function GetInterfaceType(   
   oInterface    
);  
```  
  
#### 參數  
 *oInterface*  
 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface> 物件。  
  
## 傳回值  
 表示介面型別的字串，例如 Custom、Dual、Dispinterface 或 Oleautomation。  
  
## 備註  
 呼叫這個函式，以取得介面的型別。  
  
## 範例  
 請參閱 [GetMaxID](../ide/getmaxid.md)。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetInterfaceClasses](../ide/getinterfaceclasses.md)