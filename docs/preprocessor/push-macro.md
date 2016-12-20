---
title: "push_macro | Microsoft Docs"
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
  - "vc-pragma.push_macro"
  - "push_macro_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "Pragma, push_macro"
  - "push_macro pragma"
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# push_macro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將 *macro\_name* 巨集的值儲存到這個巨集的堆疊頂端。  
  
## 語法  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## 備註  
 您可以使用 **pop\_macro** 擷取 *macro\_name* 的值。  
  
 如需範例，請參閱 [pop\_macro](../preprocessor/pop-macro.md)。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)