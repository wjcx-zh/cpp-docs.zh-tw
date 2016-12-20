---
title: "no_injected_text | Microsoft Docs"
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
  - "vc-attr.no_injected_text"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_injected_text attribute"
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# no_injected_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以防止編譯器插入的屬性使用的程式碼。  
  
## 語法  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### 參數  
 `boolean`\(選擇性\)  
 **真** 如果您想要插入的程式碼不  **，則為 false** 讓要插入的程式碼。  **真**是預設值。  
  
## 備註  
 最常用的 **no\_injected\_text** C\+\+ 屬性是由 [\/fx 將加入](../build/reference/fx-merge-injected-code.md) 編譯器選項，插入  **no\_injected\_text** .mrg 檔案中的屬性。  
  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)