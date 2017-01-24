---
title: "OnWizFinish | Microsoft Docs"
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
  - "OnWizFinish"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnWizFinish 方法"
ms.assetid: 5e0790c3-c5b4-43de-b9db-b18d07c19f41
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OnWizFinish
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者按一下 \[完成\] 時，由精靈 HTML 指令碼所呼叫的函式。  此函式接下來會呼叫精靈控制項的 **Finish** 函式。  
  
## 語法  
  
```  
  
      function OnWizFinish(   
   document    
);  
```  
  
#### 參數  
 `document`  
 HTML 文件物件  
  
## 備註  
 此函式是在使用者按一下 \[完成\] 時，由精靈 HTML 指令碼所呼叫。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)