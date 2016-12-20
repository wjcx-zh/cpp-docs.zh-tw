---
title: "編譯器錯誤 C3825 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3825"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3825"
ms.assetid: 18e204a1-f26e-42c6-8d74-2b49cc95f940
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3825
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class'：managed 或 WinRT 類別只能支援 managed 或 WinRT 事件  
  
 managed 類別中只支援 .NET 事件。  Windows 執行階段類別中只支援 Windows 執行階段事件。  若要在 managed 程式碼中修正此錯誤，請將 `event_source` 和 `event_receiver` 的類型參數從 `native` 變更為 `managed`。  或者，移除屬性。  
  
## 範例  
 下列範例會產生 C3825，並顯示如何修正此問題：  
  
```  
// C3825a.cpp  
// compile with: /clr  
public delegate void del1();  
  
[event_source(native)]           // To fix, change 'native' to 'managed' or delete this line  
ref class CEventSrc  
{  
public:  
   event del1^ event1;       // C3825  
  
   void FireEvents() {  
      event1();  
   }  
};  
  
[event_receiver(native)]         // To fix, change 'native' to 'managed' or delete this line  
ref class CEventRec  
{  
public:  
   void handler1()  
   {  
      System::Console::WriteLine("Executing handler1().\n");  
   }  
   void HookEvents(CEventSrc^ pSrc)   
   {  
      pSrc->event1 += gcnew del1(this, &CEventRec::handler1);  
   }  
   void UnhookEvents(CEventSrc^ pSrc)   
   {  
      pSrc->event1 -= gcnew del1(this, &CEventRec::handler1);  
   }  
};  
  
int main()   
{  
   CEventSrc^ pEventSrc = gcnew CEventSrc;  
   CEventRec^ pEventRec = gcnew CEventRec;  
   pEventRec->HookEvents(pEventSrc);  
   pEventSrc->FireEvents();  
   pEventRec->UnhookEvents(pEventSrc);  
}  
```