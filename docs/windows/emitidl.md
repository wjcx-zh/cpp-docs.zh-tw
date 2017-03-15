---
title: "emitidl | Microsoft Docs"
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
  - "vc-attr.emitidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "emitidl attribute"
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# emitidl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

決定是否所有後續的 IDL 屬性將加以處理並放置在產生的.idl 檔。  
  
## 語法  
  
```  
  
      [ emitidl([boolean],  
   defaultimports=[boolean]  
) ] ;  
```  
  
#### 參數  
 `boolean`  
 Possible values: **true**, **false**, **forced**, **restricted**, **push**, or **pop**.  
  
-   如果 **，則為 true**，在原始程式碼檔案中遇到的任何 IDL 類別屬性將被置於產生的.idl 檔。  這是預設值，如 **emitidl**。  
  
-   如果 **，則為 false**，將不會在產生的.idl 檔放在原始程式檔中遇到的任何 IDL 類別屬性。  
  
-   如果**限制**，可讓 IDL 屬性中的檔案，而不是 [模組](../windows/module-cpp.md)屬性。  編譯器將不會產生的.idl 檔。  
  
-   如果**強制**，就會覆寫後續 **限制**屬性，而這會讓檔案 **模組**檔案中的屬性是否有 IDL 屬性。  
  
-   **推入**讓玩家儲存目前的  **emitidl** 設定，以內部  **emitidl** 堆疊，並  **pop** 可讓您設定  **emitidl** 到任何數值是在內部頂端  **emitidl** 堆疊。  
  
 **defaultimports** *\=* `boolean` \(可省略\)  
 -   如果`boolean`是 **，則為 true**，docobj.idl 就會匯入到產生的.idl 檔。  此外，如果.idl 檔同名的.h 檔案，您`#include`到您的來源.h 檔中，相同目錄中找到程式碼，則產生的.idl 檔會包含該.idl 檔中的提供匯入陳述式。  
  
-   如果`boolean`是 **，則為 false**，docobj.idl 將不會被發送至產生的.idl 檔。  您必須明確地匯入.idl 檔案，與[匯入](../windows/import.md)。  
  
## 備註  
 後 **emitidl** 在 C\+\+ 屬性中所遇到的原始程式碼檔、 將放置產生的.idl 檔內的 IDL 類別屬性。  如果沒有任何 **emitidl** 的原始程式檔中的 IDL 屬性的屬性會為產生的.idl 檔的輸出。  
  
 可以有多個 **emitidl** 的原始程式碼檔中的屬性。  如果`[emitidl(false)];`而不需後續的檔案中遇到`[emitidl(true)];`，則沒有屬性將產生的.idl 檔進行處理。  
  
 編譯器遇到新的檔案，每次 **emitidl** 隱含地被設定為 **，則為 true**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|全螢幕輸入|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)