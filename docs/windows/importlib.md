---
title: "importlib | Microsoft Docs"
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
  - "vc-attr.importlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "importlib attribute"
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# importlib
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。  
  
## 語法  
  
```  
  
        [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### 參數  
 *tlb\_file*  
 您要匯入目前專案之類型程式庫中的 .tlb 檔案名稱 \(加上引號\)。  
  
## 備註  
 **importlib** C\+\+ 屬性會導致 `importlib` 陳述式置於所產生 .idl 檔案的程式庫區塊中。  **importlib** 屬性具有與 [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) MIDL 屬性相同的功能。  
  
## 範例  
 下列程式碼示範如何使用 **importlib**：  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)