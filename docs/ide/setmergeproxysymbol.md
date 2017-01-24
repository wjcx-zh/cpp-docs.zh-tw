---
title: "SetMergeProxySymbol | Microsoft Docs"
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
  - "SetMergeProxySymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetMergeProxySymbol 方法"
ms.assetid: d6a9db59-2d5b-4431-98bc-785675e0eafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SetMergeProxySymbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此函式由精靈所呼叫，用來在必要時加入 \_MERGE\_PROXYSTUB 符號。  
  
## 語法  
  
```  
  
      function SetMergeProxySymbol(   
   oProj    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案物件。  
  
## 備註  
 此函式由精靈所呼叫，用來在必要時加入 \_MERGE\_PROXYSTUB 符號。  
  
## 範例  
  
```  
SetMergeProxySymbol (selproj);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)