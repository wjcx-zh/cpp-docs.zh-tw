---
title: "使用 Common JScript 函式自訂 C++ 精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "精靈 JScript 方法, 建立 C++ 精靈"
ms.assetid: c602978f-a2c4-462f-85c3-50b5897bec46
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 Common JScript 函式自訂 C++ 精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用[自訂精靈](../ide/creating-a-custom-wizard.md)建立精靈專案時，專案就會包含 Common.js。  如果您指定了精靈的使用者介面，則專案也會包含指定 JScript 指令碼語言的 HTML 網頁，並包含 Common.js 檔，如下所示：  
  
```  
<SCRIPT ID="INCLUDE_COMMON" LANGUAGE ="JSCRIPT"></SCRIPT>  
```  
  
 精靈也會建立名為 Default.js 的唯一檔案。  您可以在 Default.js 中自訂自己的 JScript 函式。  如需詳細資訊，請參閱 [JScript 檔案](../ide/jscript-file.md)。  
  
 Common.js 包含您可以從每一個精靈的 HTML 網頁和從 Default.js 呼叫的函式。  如果您想要在不同的精靈上，使用相同的函式，則您可以將這些函式置於 Common.js 中。  
  
## 請參閱  
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)