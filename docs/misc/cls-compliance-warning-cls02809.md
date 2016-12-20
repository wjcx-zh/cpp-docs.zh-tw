---
title: "CLS 符合性警告 CLS02809 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS02809
屬性必須遵守特定的命名模式  
  
 屬性必須遵守特定的命名模式；屬性存取子函式的名稱會與屬性名稱相同，但在前面加上 **get\_** 或 **set\_**。  
  
 在適當的名稱比較中應忽略 **specialname** 屬性，並且應該遵守識別項規則。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS02809：  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 請注意，存取子方法的名稱與屬性的名稱不同。  透過確定所有屬性名稱都遵守命名模式，即可解決 CLS02809。