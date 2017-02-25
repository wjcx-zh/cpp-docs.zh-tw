---
title: "CreateInfFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateInfFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInfFile 方法"
ms.assetid: 941ea2ce-db10-428e-b423-8dc2a7e825cf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CreateInfFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立精靈的 Templates.inf 檔。  
  
## 語法  
  
```  
  
function CreateInfFile( );  
  
```  
  
## 傳回值  
 精靈樣板檔。  
  
## 備註  
 呼叫此函式從 Templatesinf.txt \(在暫存目錄中根據使用者的選擇所建立的一個暫存文字檔\) 建立精靈的 Templates.inf 檔。  Templates.inf 包含精靈所建立的檔案名稱清單。  如需詳細資訊，請參閱[樣板檔](../ide/template-files.md)。  
  
 如果這個函式無法在暫存目錄中建立 Templatesinf.txt 檔，則它會顯示出一項錯誤。  
  
## 範例  
 請參閱 [AddFilesToProject](../ide/addfilestoproject.md)。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)   
 [SetFilters](../ide/setfilters.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)