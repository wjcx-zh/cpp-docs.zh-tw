---
title: "__delegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__delegate_cpp"
  - "__delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_delegate 關鍵字的委派"
  - "受管理的函式指標"
  - "__delegate 關鍵字"
ms.assetid: a41d2211-b79b-4509-a4c2-cc91f3d4fc9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __delegate
**注意**：本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [delegate](../windows/delegate-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 定義可使用特定簽章封裝方法的參考類型。  
  
## 語法  
  
```  
  
__delegate   
function-declarator  
  
```  
  
## 備註  
 委派大致上相當於 C\+\+ 函式指標，但下列差異除外：  
  
-   委派只能繫結至 \_\_gc 類別內的一個或多個方法。  
  
 當編譯器遇到 `__delegate` 關鍵字時，會產生 \_\_gc 類別的定義。 這個 \_\_gc 類別具有下列特性：  
  
-   它繼承自 **System::MulticastDelegate**。  
  
-   它擁有的建構函式接受兩個引數：\_\_gc 類別或 **NULL** \(適用於繫結至靜態方法的情況\) 的指標，以及所指定類型的完整限定方法。  
  
-   它擁有稱為 `Invoke` 的方法，其簽章與宣告的委派簽章相符。  
  
## 範例  
 下列範例將會宣告 \_\_gc 類別 \(`MyCalendar`\) 和委派 \(`GetDayOfWeek`\)。 然後委派會繫結至 `MyCalendar` 的不同方法，並輪流叫用每一個方法：  
  
```  
// keyword__delegate.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate int GetDayOfWeek();  
__gc class MyCalendar {  
public:  
   MyCalendar() : m_nDayOfWeek(4) {}  
   int MyGetDayOfWeek() {   
      Console::WriteLine("handler"); return m_nDayOfWeek;   
   }  
   static int MyStaticGetDayOfWeek() {   
      Console::WriteLine("static handler");   
      return 6;  
   }  
private:  
   int m_nDayOfWeek;  
};  
  
int main () {  
   GetDayOfWeek * pGetDayOfWeek;  // declare delegate type  
   int nDayOfWeek;  
  
   // bind delegate to static method  
   pGetDayOfWeek = new GetDayOfWeek(0, &MyCalendar::MyStaticGetDayOfWeek);  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // bind delegate to instance method  
   MyCalendar * pcal = new MyCalendar();  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Combine(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // delegate now bound to two methods; remove instance method  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Remove(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
}  
```  
  
## 範例輸出  
  
```  
static handler  
6  
static handler  
handler  
4  
```