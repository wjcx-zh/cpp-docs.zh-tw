---
title: "cpp_quote | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.cpp_quote"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cpp_quote attribute"
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cpp_quote
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的字串，不能包含引號的字元，發出至產生的.idl 檔。  
  
## 語法  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### 參數  
 *statement*  
 C 的指令。  
  
## 備註  
 **Cpp\_quote** C\+\+ 屬性非常好用，如果您想要放置的.idl 檔的前置處理器指示詞。  
  
 您也可以使用 **cpp\_quote** ，且產生的.h 檔案 MIDL 編譯的一部分。  比方說，如果您有使用 C\+\+ IDL 屬性，但有些工作無法使用這個檔的 C\+\+ 標頭檔，然後您可以編譯它建立一個 MIDL 產生的.h 檔案，您可以使用。  
  
 **Cpp\_quote** 屬性具有相同的功能，為 [cpp\_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL 屬性。  
  
## 範例  
 請參閱範例的[雙](../windows/dual.md) 的範例使用如何使用  **cpp\_quote**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|全螢幕輸入|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)