---
title: "OffsetToLineNumber | Microsoft Docs"
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
  - "OffsetToLineNumber"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OffsetToLineNumber 函式"
ms.assetid: ac7e3c22-6b3b-432c-85cc-b50bbef9ce8c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OffsetToLineNumber
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [InsertIntoFunction](../ide/insertintofunction.md) 呼叫，用來將函式主體內的索引轉換成行號。  
  
## 語法  
  
```  
  
      function OffsetToLineNumber(   
   strString,   
   nPos    
);  
```  
  
#### 參數  
 `strString`  
 包含函式主體的字串。  函式主體是一個以 CR\-LF \(歸位換行\) 字元組分隔的多行字串。  
  
 `nPos`  
 字串內的一個位置。  
  
## 傳回值  
 `nPos` 所在之主體函式內的行。  函式的首行將視為是第 1 行 \(而不是第 0 行\)。  
  
## 備註  
 尋找函式主體內指定位置的行號。  
  
 此函式由 `InsertIntoFunction` 呼叫，用來將位於函式主體內的 `nPos` 索引轉換成行號。  
  
## 範例  
  
```  
strString = "function DelFile(fso,  
 strWizTempFile)\r\n{\r\n\ttry\r\n\t{\r\nif   
(fso.FileExists(strWizTempFile))\r\nreturn true;\r\n";  
  
nLine =  OffsetToLineNumber(strString, 60);  
  
// The return value for the above is 5, because character 60 in the string   
// occurs in the 5th line within the string.  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [LineBeginsWith](../ide/linebeginswith.md)