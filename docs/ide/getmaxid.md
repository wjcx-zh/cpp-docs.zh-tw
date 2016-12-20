---
title: "GetMaxID | Microsoft Docs"
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
  - "GetMaxID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMaxID 方法"
ms.assetid: a155ec2e-6132-4e40-9b85-d710538778a1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetMaxID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從這個介面的成員與其所有的基底 \(Base\) 取得最大的 Dispid。  
  
## 語法  
  
```  
  
      function GetMaxID(   
   ointerface    
);  
```  
  
#### 參數  
 *ointerface*  
 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface> 物件。  
  
## 傳回值  
 *oInterface* 的成員和其所有基底中最高的 Dispid。  
  
## 備註  
 呼叫此函式從指定之介面的成員與其所有的基底取得最大的 Dispid。  
  
## 範例  
  
```  
if (strInterfaceType == "custom")  
      window.external.AddSymbol("DISPID_DISABLED", true);  
   else  
   {  
      var nDispID = window.external.FindSymbol("DISPID");  
      if (!nDispID.length)  
      {  
         nDispID = GetMaxID(oInterface) + 1;  
         window.external.AddSymbol("DISPID", nDispID);  
      }  
   }  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)