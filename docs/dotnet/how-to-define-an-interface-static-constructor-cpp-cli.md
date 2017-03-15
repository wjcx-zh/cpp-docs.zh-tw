---
title: "如何：定義介面靜態建構函式 (C++/CLI) | Microsoft Docs"
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
  - "建構函式 [C++]"
  - "介面靜態建構函式"
  - "靜態建構函式, interface"
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定義介面靜態建構函式 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介面只能有靜態建構函式，可以用來初始化靜態資料成員。第一次靜態介面成員存取，靜態建構函式只會呼叫一次與之前呼叫。  
  
 如需靜態建構函式詳細資訊，請參閱[如何：在類別或結構中定義靜態建構函式](../misc/how-to-define-static-constructors-in-a-class-or-struct.md)。  
  
## 範例  
  
```  
// mcppv2_interface_class2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct MyInterface {  
   static int i;  
   static void Test() {  
      Console::WriteLine(i);  
   }  
  
   static MyInterface() {   
      Console::WriteLine("in MyInterface static constructor");  
      i = 99;  
   }  
};  
  
ref class MyClass : public MyInterface {};  
  
int main() {  
   MyInterface::Test();  
   MyClass::MyInterface::Test();  
  
   MyInterface ^ mi = gcnew MyClass;  
   mi->Test();  
}  
```  
  
  **in MyInterface static constructor**  
**99**  
**99**  
**99**   
## 請參閱  
 [interface class](../windows/interface-class-cpp-component-extensions.md)