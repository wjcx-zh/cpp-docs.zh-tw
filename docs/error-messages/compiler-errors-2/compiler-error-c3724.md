---
title: "編譯器錯誤 C3724 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3724
dev_langs: C++
helpviewer_keywords: C3724
ms.assetid: cab8aba7-14fc-406f-8cc6-32744c8f31c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac7b5e86c7df7dd2927f98eb969a554c38518255
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3724"></a>編譯器錯誤 C3724
必須 #include \<windows.h > 若要使用多執行緒模式使用事件  
  
 Windows.h 檔案是必要的如果您使用多執行緒模式使用事件。 若要修正這個錯誤，加入`#include <windows.h>`接收者所定義的事件來源和事件中的檔案頂端。  
  
```  
// C3724.cpp  
// uncomment the following line to resolve  
// #include <windows.h>  
  
[event_source(native), threading(apartment)]  
class CEventSrc {  
public:  
   __event void event1();   // C3724  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {  
   }  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
  
int main() {  
}  
```