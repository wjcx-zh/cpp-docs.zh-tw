---
title: "SetErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetErrorInfo 方法"
ms.assetid: 78bca763-3f90-4e04-b566-b4b7fe2431b1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# SetErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [OnWizFinish](../ide/onwizfinish.md) 和 [CanUseFileName](../ide/canusefilename.md) 呼叫來提供目前的錯誤資訊。  
  
## 語法  
  
```  
  
      function SetErrorInfo(   
   oErrorObj   
);  
```  
  
#### 參數  
 *oErrorObj*  
 錯誤物件。  
  
## 備註  
 由 [OnWizFinish](../ide/onwizfinish.md) 和 [CanUseFileName](../ide/canusefilename.md) 呼叫來提供目前的錯誤資訊。  如需詳細資訊，請參閱＜Visual C\+\+ 精靈模型＞文件中的 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.SetErrorInfo%2A>。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)