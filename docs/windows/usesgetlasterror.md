---
title: "usesgetlasterror | Microsoft Docs"
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
  - "vc-attr.usesgetlasterror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "usesgetlasterror attribute"
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# usesgetlasterror
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

告知呼叫端是否呼叫該函式時，卻發生錯誤，然後呼叫端就可以呼叫`GetLastError`以取得錯誤的程式碼。  
  
## 語法  
  
```  
  
[usesgetlasterror]  
  
```  
  
## 備註  
 **Usesgetlasterror** C\+\+ 屬性具有相同的功能，為 [usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL 屬性。  
  
## 範例  
 請參閱 [idl\_module](../windows/idl-module.md) 範例示範如何使用 **usesgetlasterror**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**單元**屬性|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)