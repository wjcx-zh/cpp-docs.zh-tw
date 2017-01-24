---
title: "retval | Microsoft Docs"
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
  - "vc-attr.retval"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "retval attribute"
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# retval
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定接收成員傳回值的參數。  
  
## 語法  
  
```  
  
[retval]  
  
```  
  
## 備註  
 **Retval** C\+\+ 屬性具有相同的功能，為 [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL 屬性。  
  
 **retval** 必須出現在函式宣告中的最後一個引數。  
  
## 範例  
 請參閱範例的[可繫結](../windows/bindable.md) 的範例使用  **retval**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數，介面方法|  
|**可重複**|否|  
|**必要的屬性**|**out**|  
|**無效的屬性**|**in**|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)