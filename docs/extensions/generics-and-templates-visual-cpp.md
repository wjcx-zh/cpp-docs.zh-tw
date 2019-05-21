---
title: 泛型與範本 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 74cfd791e8400b788d38f272eed3d421ca4230e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516353"
---
# <a name="generics-and-templates-ccli"></a>泛型與範本 (C++/CLI)

泛型與範本都是支援參數化型別的語言功能。 不過，它們不一樣且有不同的用途。 本主題提供多個差異的概觀。

如需詳細資訊，請參閱 [Windows 執行階段與受控範本](windows-runtime-and-managed-templates-cpp-component-extensions.md)。

## <a name="comparing-templates-and-generics"></a>比較範本與泛型

泛型與 C++ 範本之間的主要差異：

- 泛型在執行階段使用型別來替換它們之前均為泛型。 範本則會在編譯時間進行特製化，因此，它們在執行階段仍然不是參數化的型別

- 具體而言，Common Language Runtime 在 MSIL 中支援泛型。 由於執行階段知道泛型，因此，在參考包含泛型型別的組件時，可以使用特定型別來替換泛型型別。 相較之下，範本會在編譯時間解析為一般型別，而產生的型別可能不會在其他組件中進行特製化。

- 在兩個不同組件中使用相同型別引數特製化的泛型都是同一個型別。 在兩個不同組件中使用相同型別引數特製化的範本會被執行階段視為不同型別。

- 泛型會產生來作為單一可執行程式碼，可用於所有參考型別引數 (這不適用實值型別，其在每個實值型別上均有唯一實作)。 JIT 編譯器知道泛型，且能夠將用來作為型別引數的參考或實值型別的程式碼最佳化。 範本會針對為每個特製化產生個別的執行階段程式碼。

- 泛型不允許非型別的範本參數，例如 `template <int i> C {}`。 但範本允許它們。

- 泛型不允許明確特製化 (也就是，特定型別之範本的自訂實作)。 但範本允許。

- 泛型不允許部分特製化 (型別引數子集的自訂實作)。 但範本允許。

- 泛型不允許使用型別參數作為泛型型別的基底類別。 但範本允許。

- 範本支援 template-template 參數 (例如 `template<template<class T> class X> class MyClass`)，但泛型不支援。

## <a name="combining-templates-and-generics"></a>合併範本與泛型

泛型中的基本差異會對建置合併範本與泛型的應用程式產生影響。 例如，假設您有一個範本類別，而且想要為其建立泛型包裝函式，以將該範本當成泛型公開至其他語言。 您不能讓泛型採用它接著要傳遞至範本的型別參數，因為範本必須在編譯時間具備該型別參數，但泛型要等到執行階段才會解析該型別參數。 此外，也不能在泛型內巢狀處理範本，因為沒有任何方法可以在編譯時間，針對要在執行階段具現化的任意泛型型別展開範本。

## <a name="example"></a>範例

### <a name="description"></a>說明

下列範例顯示同時使用範本與泛型的簡單範例。 在此範例中，範本類別會將其參數傳遞給泛型型別。 反向操作則不行。

當您想要在現有的泛型 API 上使用 C++/CLI 組件本機的範本程式碼來建置，或者當您想要在泛型型別中額外加入一層參數化，就可以使用這個慣用語，以善用某些泛型不支援的範本功能。

### <a name="code"></a>程式碼

```cpp
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

```Output
F
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)