---
title: "委派和事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__delegate 關鍵字"
  - "__event 關鍵字 [C++]"
  - "delegate 關鍵字 [C++]"
  - "委派 [C++], 從 Managed Extensions for C++ 升級"
  - "event 關鍵字 [C++]"
  - "事件 [C++], 從 Managed Extensions for C++ 升級"
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 委派和事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，宣告委派和事件的方式已變更。  
  
 不再需要雙底線，如下列範例所示。  以下是採用 Managed Extensions 的範例程式碼：  
  
```  
__delegate void ClickEventHandler(int, double);  
__delegate void DblClickEventHandler(String*);  
  
__gc class EventSource {  
   __event ClickEventHandler* OnClick;    
   __event DblClickEventHandler* OnDblClick;    
};  
```  
  
 同一個程式碼採用新語法時看起來如下：  
  
```  
delegate void ClickEventHandler( int, double );  
delegate void DblClickEventHandler( String^ );  
  
ref class EventSource {  
   event ClickEventHandler^ OnClick;   
   event DblClickEventHandler^ OnDblClick;   
};  
```  
  
 事件 \(和委派\) 是參考型別，它們在新語法中因為使用帽型符號 \(`^`\) 而相當清楚。事件同時支援明確宣告語法和上述程式碼中所示的一般格式。  在明確的格式中，使用者會指定 `add`、`raise` 和 `remove` 方法和事件產生關聯 \(只有 `add` 和 `remove` 方法為必要項目，`raise` 方法則為選擇性項目\)。  
  
 在 Managed Extensions 中，如果您提供這些方法，並不必提供明確的事件宣告，但您必須決定未顯示的事件名稱。  每個方法會以 `add_EventName`、`raise_EventName` 和 `remove_EventName` 的格式指定，如下列從 Managed Extensions 規格所取出的範例所示：  
  
```  
// explicit implementations of add, remove, raise  
public __delegate void f(int);  
public __gc struct E {  
   f* _E;  
public:  
   E() { _E = 0; }  
  
   __event void add_E1(f* d) { _E += d; }  
  
   static void Go() {  
      E* pE = new E;  
      pE->E1 += new f(pE, &E::handler);  
      pE->E1(17);   
      pE->E1 -= new f(pE, &E::handler);  
      pE->E1(17);   
   }  
  
private:  
   __event void raise_E1(int i) {  
      if (_E)  
         _E(i);  
   }  
  
protected:  
   __event void remove_E1(f* d) {  
      _E -= d;  
   }  
};  
```  
  
 新語法簡化了宣告，如下列轉譯示範所示。  一個事件會指定兩個或三個方法，將它們括在一組大括號中，並放在緊接事件宣告及其相關委派型別宣告之後，如下所示：  
  
```  
public delegate void f( int );  
public ref struct E {  
private:  
   f^ _E; // delegates are also reference types  
  
public:  
   E() {  // note the replacement of 0 with nullptr!  
      _E = nullptr;   
   }  
  
   // the new aggregate syntax of an explicit event declaration  
   event f^ E1 {  
   public:  
      void add( f^ d ) {  
         _E += d;  
      }  
  
   protected:  
      void remove( f^ d ) {  
         _E -= d;  
      }  
  
   private:  
      void raise( int i ) {  
         if ( _E )  
            _E( i );  
      }  
   }  
  
   static void Go() {  
      E^ pE = gcnew E;  
      pE->E1 += gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
      pE->E1 -= gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
   }  
};  
```  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [delegate](../windows/delegate-cpp-component-extensions.md)   
 [event](../windows/event-cpp-component-extensions.md)