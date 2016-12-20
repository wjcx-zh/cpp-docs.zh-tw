---
title: "CanUseFileName | Microsoft Docs"
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
  - "CanUseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanUseFileName 方法"
ms.assetid: 60b669fa-9484-4435-b502-78ec8e960a00
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanUseFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檢查檔案是否存在。  如果檔案存在且不受限制，則精靈會提示使用者將程式碼合併，以加入至現存的檔案中。  
  
## 語法  
  
```  
  
      function CanUseFileName(   
   strFileName,   
   bCheckIfMidlHeader,   
   bCannotExist,   
   bSetMergeFlag    
);  
```  
  
#### 參數  
 `strFileName`  
 要檢查的檔案名稱。  
  
 *bCheckIfMidlHeader*  
 設定為 **True** 會檢查檔名是否是由 MIDL 產生的。  
  
 *bCannotExist*  
 設定為 **True** 會檢查檔名是否已經存在且無法覆寫。  
  
 *bSetMergeFlag*  
 設定為 **True** 以包含 MERG\_FILE 符號，該符號指示使用者可以將程式碼合併至現存的檔名中。  
  
## 傳回值  
 如果 `strFileName` 是唯一，或者程式碼可以附加至現存的檔案中則為 **true**，否則為 **false**。  
  
## 備註  
 呼叫此函式以檢查檔名是否已經存在。  如果檔名存在，且它不是由 MIDL 所建立的或其他方面不受限制，則此函式會提示使用者將新的程式碼合併至現存的檔案中。  
  
 如果檔名不存在且不受限制，則將會以指定的名稱來建立檔案。  
  
 如果檔名是由 MIDL 所建立或受限於其他的因素，則精靈會顯示錯誤訊息。  
  
## 範例  
  
```  
case "HTML_FILE":  
if (!HTML_FILE.disabled)  
   {  
   if (!window.external.FindSymbol("HTML_FILE_VALID"))  
      {  
      bValid = CanUseFileName(obj.value, false, true);  
      if (!bValid)  
      break;  
      window.external.AddSymbol("HTML_FILE_VALID", true)  
      }  
   }  
   bValid = window.external.ValidateFile(HTML_FILE.value, vsCMValidateFileExtHtml);  
   break;   
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)