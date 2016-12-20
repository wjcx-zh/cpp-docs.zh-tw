---
title: "CLS 符合性警告 CLS03302 | Microsoft Docs"
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
  - "CLS03302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03302"
ms.assetid: 3b99e64b-d5cb-4eb8-81b5-fd96992f2c10
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS03302
事件必須遵守特定的命名模式  
  
 事件必須遵守特定的命名模式；事件存取子函式的名稱會與事件名稱相同，但在前面加上 **raise\_**、**remove\_** 或 **add\_**。  
  
 在適當的名稱比較中應忽略 **specialname** 屬性，並且應該遵守識別項規則。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS03302：  
  
```  
.method public specialname instance void add_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::add_MyEvent .method public specialname instance void remove_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::remove_MyEvent .method public specialname instance void raise_MyEventaaa(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent .event specialname MyAssemblyDelegate MyEvent { .addon instance void One::add_MyEventaaa(class MyAssemblyDelegate) .removeon instance void remove_MyEventaaa(class MyAssemblyDelegate) .fire instance void raise_MyEventaaa(object, class [mscorlib]System.EventArgs) } // end of event One::MyEvent } // end of class One  
```  
  
 請注意，存取子方法的名稱與事件的名稱不同。  透過確定所有事件存取子名稱都遵守命名模式，即可解決 CLS03302。