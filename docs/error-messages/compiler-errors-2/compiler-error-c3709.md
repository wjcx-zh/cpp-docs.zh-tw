---
title: "編譯器錯誤 C3709 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3709
dev_langs: C++
helpviewer_keywords: C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d56a4c18543ad71e524a4cc08eecd35ab6e7e2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3709"></a>編譯器錯誤 C3709
'function': 不適當的語法指定事件在 __hook /\__unhook  
  
 當您指定的事件來源[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md)、 第一個參數必須是有效的事件方法和第二個參數必須是有效的事件來源物件 （而非方法）。  
  
 下列範例會產生 C3709:  
  
```  
// C3709.cpp  
// compile with: /LD  
[event_source(native)]  
class CEventSrc  
{  
public:  
   __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec  
{  
public:  
   void handler1()  
   {  
   }  
  
   void HookEvents(CEventSrc* pSrc)  
   {  
      __hook(bad, pSrc, CEventRec::handler1);   // C3709  
      // Try the following line instead:  
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc)  
   {  
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
```