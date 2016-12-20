---
title: "GetRuntimeErrorDesc | Microsoft Docs"
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
  - "GetRuntimeErrorDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConversionError 方法"
  - "GetRuntimeErrorDesc 方法"
  - "RangeError 方法"
  - "ReferenceError 方法"
  - "RegExpError 方法"
  - "SyntaxError 方法"
  - "TypeError 方法"
  - "URIError 方法"
ms.assetid: d56fdd2e-6ad0-4c49-9e98-bcf0105e1b12
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetRuntimeErrorDesc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回例外狀況類型的描述，  
  
## 語法  
  
```  
  
      function GetRuntimeErrorDesc(   
   strRuntimeErrorName    
);  
```  
  
#### 參數  
 *strRuntimeErrorName*  
 已發生的例外狀況類型名稱。  
  
## 傳回值  
 例外狀況類型的描述。  
  
## 備註  
 傳回例外狀況類型的描述，  可以是下列例外狀況類型之一：  
  
|例外狀況類型|描述|  
|------------|--------|  
|ConversionError|試圖將物件轉換成無法轉換的物件時，就會發生這個錯誤。|  
|RangeError|提供給函式的引數超出允許的範圍時，就會發生這個錯誤。  例如，建構 `Array` 物件時，若試圖使用不是有效的正整數長度，就會發生這個錯誤。|  
|ReferenceError|偵測到無效的參考時，就會發生這個錯誤。  例如，如果預期的參考是 null，就會發生這個錯誤。|  
|RegExpError|規則運算式 \(Regular Expression\) 發生編譯錯誤時，就會發生這個錯誤。  然而，規則運算式一旦經過編譯後，就不可能會發生這個錯誤。  例如，如果宣告規則運算式所用的模式語法無效，或旗標不是 *i*、*g* 或 *m*，或同一個旗標出現不止一次，就會發生這樣的例子。|  
|SyntaxError|剖析原始程式文字時若該文字不符合正確語法，就會發生這個錯誤。  例如，如果呼叫 `eval` 函式時所用的引數不是有效的程式文字，就會發生這樣的錯誤。|  
|TypeError|只要運算元實際的型別不符合預期型別時，就會發生這個錯誤。  例如，如果對非物件的東西呼叫函式，或這個東西不支援該呼叫，就會發生這樣的例子。|  
|URIError|偵測到非法的 Uniform Resource Indicator \(URI\) 時，就會發生這個錯誤。  例如，在編碼或解碼的字串中發現非法的字元時，就會發生這個錯誤。|  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)