---
title: "Windows Runtime and Managed Templates (C++ Component Extensions) | Microsoft Docs"
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
  - "templates, with CLR types"
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Runtime and Managed Templates (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用其他樣板型別參數，範本可讓您定義 Windows 執行階段或 Common Language Runtime 型別的原型，然後具現化該型別的變數。  
  
## 所有執行階段  
 您可以從值或參考型別建立範本。如需建立值或參考型別的詳細資訊，請參閱 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 如需C\+\+類別範本的詳細資訊，請參閱[類別樣板](../cpp/class-templates.md)。  
  
## Windows Runtime \- Windows 執行階段  
 \(這個語言功能沒有只適用於 Windows 執行階段的備註。\)  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 從 Managed 型別建立類別樣板有一些限制，在下列程式碼範例所示。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 以 Managed 型別樣板參數的泛型型別是可行的，不過，您無法執行個體化泛型型別的樣板參數的 Managed 樣板。這是因為，泛型型別在執行階段解析。如需詳細資訊，請參閱[Generics and Templates \(Visual C\+\+\)](../windows/generics-and-templates-visual-cpp.md)。  
  
```cpp  
// managed_templates.cpp  
// compile with: /clr /c  
  
generic<class T>   
ref class R;   
  
template<class T>   
ref class Z {  
   // Instantiate a generic with a template parameter.  
   R<T>^ r;    // OK  
};  
  
generic<class T>   
ref class R {  
   // Cannot instantiate a template with a generic parameter.  
   Z<T>^ z;   // C3231  
};  
```  
  
 **範例**  
  
 泛型型別或函式在 Managed 樣板不能巢狀。  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **範例**  
  
 在具有 C\+\+\/CLI 語言語法的參考組件中定義的無法存取範本，不過，您可以使用反映。如果樣板不會具現化，它在中繼資料中沒有發出。如果樣板具現化，只有參考的成員函式會出現在中繼資料。  
  
```cpp  
// managed_templates_3.cpp  
// compile with: /clr  
  
// Will not appear in metadata.  
template<class T> public ref class A {};  
  
// Will appear in metadata as a specialized type.  
template<class T> public ref class R {  
public:  
   // Test is referenced, will appear in metadata  
   void Test() {}  
  
   // Test2 is not referenced, will not appear in metadata  
   void Test2() {}  
};  
  
// Will appear in metadata.  
generic<class T> public ref class G { };  
  
public ref class S { };  
  
int main() {  
   R<int>^ r = gcnew R<int>;  
   r->Test();  
}  
```  
  
 **範例**  
  
 您可以將類別的 Managed 修飾詞在類別樣板的部分特製化或明確特製化。  
  
```cpp  
// managed_templates_4.cpp  
// compile with: /clr /c  
  
// class template  
// ref class  
template <class T>  
ref class A {};  
  
// partial template specialization  
// value type  
template <class T>  
value class A <T *> {};  
  
// partial template specialization  
// interface  
template <class T>   
interface class A<T%> {};  
  
// explicit template specialization  
// native class  
template <>  
class A <int> {};  
  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)