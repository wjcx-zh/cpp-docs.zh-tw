---
title: Windows 執行階段和 Managed 的樣板 （c + + 元件擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9053b101428ac26e96446d9c6756ec5de35e06c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891359"
---
# <a name="windows-runtime-and-managed-templates-c-component-extensions"></a>Windows 執行階段和 Managed 樣板 (C++ 元件擴充功能)
範本可讓您定義 Windows 執行階段或通用語言執行平台 (CLR) 類型的原型，然後使用不同的範本型別參數具現化該類型的變化。  
  
## <a name="all-runtimes"></a>所有執行階段  
 您可以從值或參考類型建立範本。  如需建立值或參考類型的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 如需標準 c + + 類別樣板的詳細資訊，請參閱[類別樣板](../cpp/class-templates.md)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 (這個語言功能沒有只適用於 Windows 執行階段的備註。)  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 從 Managed 類型建立類別範本會有一些限制，下列程式碼範例將示範這些限制。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 雖然您可以用 Managed 類型範本參數具現化泛型類型，但是無法使用泛型類型範本參數具現化 Managed 範本。  這是因為泛型類型會在執行階段解析。  如需詳細資訊，請參閱[泛型和樣板 （Visual c + +）](../windows/generics-and-templates-visual-cpp.md)。  
  
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
  
 泛型類型或函式無法在 Managed 範本中設為巢狀。  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **範例**  
  
 雖然您無法存取使用 C++/CLI 語言語法的參考組件中定義的範本，但是可以使用反映。  如果範本未具現化，就不會在中繼資料中發出。  如果範本已具現化，則只有參考的成員函式會出現在中繼資料中。  
  
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
  
 您可以在類別範本的部分特製化或明確特製化中，變更類別的 Managed 修飾詞。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)