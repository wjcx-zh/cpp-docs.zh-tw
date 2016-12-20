---
title: "編譯器錯誤 C3185 | Microsoft Docs"
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
  - "C3185"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3185"
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3185
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Managed 或 WinRT 類型 'type' 上使用 'typeid'，請改用 'operator'  
  
 您無法將 [typeid](../../cpp/typeid-operator.md) 運算子套用到 Managed 或 WinRT 類型；請改用 [typeid](../../windows/typeid-cpp-component-extensions.md)。  
  
 下列範例會產生 C3185，並示範如何修正此問題：  
  
```  
// C3185a.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
  
int main() {  
   Derived ^ pd = gcnew Derived;  
   Base ^pb = pd;  
   const type_info & t1 = typeid(pb);   // C3185  
   System::Type ^ MyType = Base::typeid;   // OK  
};  
```  
  
 **Managed Extensions for C\+\+**  
  
 您無法將 [typeid](../../cpp/typeid-operator.md) 套用到 Managed 類型，請改用 [\_\_typeof](../../misc/typeof.md)。  
  
 下列範例會產生 C3185：  
  
```  
// C3185b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__gc class Base {};  
__gc class Derived : public Base {};  
  
int main() {  
   Derived *pd = new Derived;  
   Base *pb = pd;  
   const type_info & t1 = typeid(*pb);   // C3185  
  
   // OK  
   Type * t = __typeof(Base);  
   Type * t1 = __typeof(Derived);  
};  
```