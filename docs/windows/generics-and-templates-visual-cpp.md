---
title: 泛型和樣板 (C + + /cli CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 81b2812faa2fcb7acfdc272474d22039afa24655
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660041"
---
# <a name="generics-and-templates-ccli"></a>泛型和樣板 (C + + /cli CLI)

泛型和範本都是這兩種語言功能提供支援的參數化類型。 不過，他們會不同，而且有不同的用途。 本主題提供的許多差異的概觀。

如需詳細資訊，請參閱 < [Windows 執行階段和 Managed 樣板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。

## <a name="comparing-templates-and-generics"></a>比較範本和泛型

泛型和 c + + 範本之間的主要差異：

- 泛型是泛型，直到類型取代它們在執行階段。 範本專門在編譯時期，因此它們都不在執行階段仍然參數化的類型

- 具體而言，common language runtime 會在 MSIL 中支援泛型。 因為執行階段知道泛型時，特定類型，可取代泛型型別參考包含泛型類型的組件時。 範本，相較之下，解析成一般類型在編譯時期和產生的型別未進行特製化其他組件中。

- 泛型的專門領域為兩個不同的組件相同的類型引數都是相同的型別。 樣板特製化中使用相同的型別引數會被視為由執行階段不同類型的兩個不同組件。

- 泛型會產生為單一的可執行的程式碼可用於所有 （這是不具有每個值類型的唯一實作實值型別，則為 true） 的參考型別引數。 JIT 編譯器知道泛型，並能夠最佳化的程式碼參考或實值類型做為型別引數。 範本會產生每個特製化的個別執行階段程式碼。

- 泛型這類不允許非類型範本參數， `template <int i> C {}`。 範本可讓它們。

- 泛型不允許明確特製化 （也就是特定類型的範本的自訂實作）。 執行範本。

- 泛型不允許部分特製化 （的自訂實作的一小部分的型別引數）。 執行範本。

- 泛型不允許使用型別參數作為泛型類型的基底類別。 執行範本。

- 範本支援範本範本參數 (例如`template<template<class T> class X> class MyClass`)，但不會泛型。

## <a name="combining-templates-and-generics"></a>合併範本和泛型

泛型中的基本差異有建置合併範本和泛型的應用程式的影響。 例如，假設您擁有您想要建立的泛型包裝函式，以公開該範本，以其他語言當成是一般的範本類別。 您不能有泛型將型別參數，然後傳遞至範本，但因為範本必須有該型別參數，在編譯時期，但一般不會在執行階段之前，解決型別參數。 巢狀在泛型內的範本將無法運作是因為沒有任何方法可以展開 [範本]，請在編譯時期針對任意無法在執行階段具現化的泛型型別。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例顯示同時使用範本和泛型的簡單範例。 在此範例中，此範本類別會將透過其參數傳遞給泛型類型。 反向執行則不可能。

無法使用此慣用句，當您想要建置在現有的一般 API 與範本程式碼的本機 C + + /cli CLI 組件，或當您需要新增一層額外的參數化泛型型別，才能利用範本的某些功能不支援 by 泛型。

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

[泛型](../windows/generics-cpp-component-extensions.md)