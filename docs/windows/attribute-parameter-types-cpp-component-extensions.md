---
title: "Attribute Parameter Types  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom attributes, parameter types"
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Attribute Parameter Types  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

值傳遞至屬性必須在編譯時期編譯器知道。屬性參數可以是下列型別:  
  
-   `bool`  
  
-   `char`, `unsigned char`  
  
-   `short`, `unsigned short`  
  
-   `int`, `unsigned int`  
  
-   `long`, `unsigned long`  
  
-   `__int64`, `unsigned __int64`  
  
-   `float`, `double`  
  
-   `wchar_t`  
  
-   `char*` 或 `wchar_t*` 或 `System::String*`  
  
-   `System::Type ^`  
  
-   `System::Object ^`  
  
-   `enum`  
  
## 範例  
  
### 程式碼  
  
```  
// attribute_parameter_types.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct AStruct {};  
  
[AttributeUsage(AttributeTargets::ReturnValue)]  
ref struct Attr : public Attribute {  
   Attr(AStruct ^ i){}  
   Attr(bool i){}  
   Attr(){}  
};  
  
ref struct MyStruct {  
   static AStruct ^ x = gcnew AStruct;  
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104  
   [returnvalue:Attr] int Test2() { return 0; }   // OK  
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK  
};  
```  
  
## 範例  
  
### 說明  
 當指定屬性時，所有未命名的 \(位置\) 引數必須在任何具名引數之前。  
  
### 程式碼  
  
```  
// extending_metadata_c.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class)]  
ref class MyAttr : public Attribute {  
public:  
   MyAttr() {}  
   MyAttr(int i) {}  
   property int Priority;  
   property int Version;  
};  
  
[MyAttr]   
ref class ClassA {};   // No arguments  
  
[MyAttr(Priority = 1)]   
ref class ClassB {};   // Named argument  
  
[MyAttr(123)]   
ref class ClassC {};   // Positional argument  
  
[MyAttr(123, Version = 1)]   
ref class ClassD {};   // Positional and named  
```  
  
## 範例  
  
### 說明  
 屬性參數可以是上一個型別的一維陣列。  
  
### 程式碼  
  
```  
// extending_metadata_d.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## 請參閱  
 [User\-Defined Attributes](../windows/user-defined-attributes-cpp-component-extensions.md)