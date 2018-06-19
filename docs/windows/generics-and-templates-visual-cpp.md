---
title: 泛型和樣板 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d6dc0a64c5d225f6e80a21dc008e5a2486ad3d9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878901"
---
# <a name="generics-and-templates-visual-c"></a>泛型和樣板 (Visual C++)
泛型和範本都是參數化類型中提供支援這兩種語言功能。 不過，它們不相同，且有不同用途。 本主題提供許多差異的概觀。  
  
 如需詳細資訊，請參閱[Windows 執行階段和 Managed 樣板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。  
  
## <a name="comparing-templates-and-generics"></a>比較範本和泛型  
 泛型和 c + + 範本之間的主要差異：  
  
-   泛型是泛型，直到類型會取代它們在執行階段。 範本被專門在編譯時期，因此不會在執行階段仍參數化的類型  
  
-   通用語言執行平台特別支援 MSIL 泛型。 由於執行階段知道有關泛型，特定類型可以取代為泛型類型，參考包含泛型類型的組件時。 範本，相較之下，將解析成一般類型在編譯時期和結果的型別未進行特製化其他組件中。  
  
-   在兩個不同的組件特製化的泛型與相同的型別引數是相同的型別。 樣板特製化中兩個不同的組件使用相同的類型引數會被視為執行階段是不同的類型。  
  
-   泛型會產生為單一的可執行程式碼是用來 （這不適用於有唯一的實作，每個值類型的值類型） 的所有參考型別引數。 JIT 編譯器知道有關泛型，並且可以最佳化程式碼參考或值類型做為型別引數。 範本會產生個別的執行階段程式碼，針對每個特製化。  
  
-   泛型，無法進行非類型樣板參數，例如`template <int i> C {}`。 範本可讓它們。  
  
-   泛型不允許明確特製化 （亦即，自訂實作的特定類型的範本）。 執行範本。  
  
-   泛型不允許部分特製化 （自訂實作子集的型別引數）。 執行範本。  
  
-   泛型不允許型別參數做為泛型類型的基底類別。 執行範本。  
  
-   範本可支援範本範本參數 (例如`template<template<class T> class X> class MyClass`)，但泛型則不行。  
  
## <a name="combining-templates-and-generics"></a>結合範本和泛型  
  
-   泛型中的基本差異有建置結合範本和泛型的應用程式的影響。 例如，假設您擁有您想要建立泛型包裝函式公開為泛型該範本向其他語言的範本類別。 您不能有泛型採用型別參數，然後傳遞至範本，因為需要有在編譯時期，該型別參數的範本但一般不會解析型別參數執行階段之前。 巢狀在泛型內的範本將無法運作是因為沒有任何方法可以在編譯時期針對任意無法在執行階段具現化的泛型類型展開範本。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例同時使用範本和泛型的簡單範例。 在此範例中，此範本類別會將透過其參數傳遞給泛型類型。 反向執行則不可能。  
  
 無法使用這個慣用語，當您想要在 Visual c + + 組件的本機範本程式碼的現有泛型 API 上建置，或當您需要加入一層額外的參數化泛型類型，若要利用特定功能的範本不 supporte泛型的 d。  
  
### <a name="code"></a>程式碼  
  
```  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
F  
```  
  
## <a name="see-also"></a>另請參閱  
 [泛型](../windows/generics-cpp-component-extensions.md)