---
title: C++/CLI 中的泛型概觀
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: a1a66b6464bf952a530dbf1ea188bfd681d684d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172070"
---
# <a name="overview-of-generics-in-ccli"></a>C++/CLI 中的泛型概觀

泛型是通用語言執行平台 (CLR) 所支援的參數化類型。 參數化類型是以使用泛型時指定的未知類型參數定義的類型。

## <a name="why-generics"></a>為什麼選擇泛型？

C++ 支援範本，而且範本和泛型都支援使用參數化類型建立具類型的集合類別。 不過，範本會提供編譯時期參數化。 您無法參考包含範本定義的組件，並建立範本的新特製化。 一旦編譯之後，特製化的範本外觀就像任何其他類別或方法。 相反地，泛型會在 MSIL 中做為參數化類型發出，執行階段會將它視為參數化類型。參考包含泛型類型之組件的原始程式碼可以建立泛型類型的特製化。 如需比較標準 C++ 範本和泛型的詳細資訊，請參閱[泛型與範本 (C++/CLI)](generics-and-templates-visual-cpp.md)。

## <a name="generic-functions-and-types"></a>泛型函式和類型

類別類型只要是 Managed 類型，就可以是泛型。 這類範例可能是 `List` 類別。 清單中物件的類型會是類型參數。 如果您需要適用於各種不同型別物件的 `List` 類別，您可能已在泛型之前使用了 `List`，以採用 `System::Object` 作為項目型別。 但是，這樣會允許在清單中使用所有物件 (包括錯誤類型的物件)。 這類清單會稱為不具類型的集合類別。 最佳的情況是，您可以在執行階段檢查這個類型，並且擲回例外狀況。 或者，您可能使用了範本，這樣一旦編譯成組件，就會失去其泛型本質。 組件的消費者無法建立自己的範本特製化。 泛型可讓您建立具型別的集合類別，例如 `List<int>` (讀為 "List of int") 及 `List<double>` (讀為 "List of double")，如果您嘗試將並非集合原本可接受的型別放入具型別的集合中，則會產生編譯時間錯誤。 此外，這些類型在編譯之後仍然是泛型。

您或許能在[泛型類別 (C++/CLI)](generic-classes-cpp-cli.md) 中找到泛型類別的語法說明。 新的命名空間 <xref:System.Collections.Generic> 引進了一組參數化的集合型別，包括 <xref:System.Collections.Generic.Dictionary%602>、<xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.LinkedList%601>。

執行個體和靜態類別成員函式、委派及全域函式也可以是泛型。 若函式的參數是未知的類型，或者函式本身必須與泛型類型一起使用，則可能需要泛型函式。 在多數情況下，`System::Object` 以往可能用來作為未知物件型別的參數，現在則可改用泛型型別參數，以允許更多型別安全的程式碼。 若嘗試傳入非函式所設計使用的類型，則該類型會在編譯時期標記為錯誤。 使用 `System::Object` 作為函式參數，就不會偵測到意外傳遞不適合函式處理之物件的情形，而且您必須將未知的物件型別轉換為函式主體中的特定型別，並將 InvalidCastException 的可能性納入考量。 使用泛型時，嘗試將物件傳遞至函式的程式碼會引起類型衝突，因此就能保證函式主體具有正確的類型。

相同的優點適用於泛型上建立的集合類別。 以往集合類別都會使用 `System::Object` 來將元素儲存於集合中。 若插入非集合所設計使用之類型的物件，這種情形不會在編譯時期標記，而且甚至不會在插入物件時標記。 通常會在集合中存取物件時，將該物件轉型成其他類型。 只有在轉型失敗時，才會偵測到非預期的類型。 泛型會在編譯時期藉由偵測是否有插入類型不符合 (或隱含轉換成) 泛型集合之類型參數的任何程式碼，來解決這個問題。

如需語法的說明，請參閱[泛型函式 (C++/CLI)](generic-functions-cpp-cli.md)。

## <a name="terminology-used-with-generics"></a>泛型使用的詞彙

### <a name="type-parameters"></a>類型參數

泛型宣告包含一或多個稱為「型別參數」的未知型別。 類型參數的指定名稱代表泛型宣告主體內的類型的名稱。 型別參數會做為泛型宣告主體內的類型使用。 `List<T>` 的泛型宣告包含型別參數 T。

### <a name="type-arguments"></a>類型引數

「型別引數」是在針對一或多個特定型別將泛型特製化時，用以取代型別參數的實際型別。 例如，**int** 是 `List<int>` 中的型別引數。 實值類型和控制代碼類型是泛型型別引數唯一允許的類型。

### <a name="constructed-type"></a>建構類型

建構自泛型型別的型別稱為「建構型別」。 未完整指定的型別 (例如 `List<T>`) 為「開放式建構型別」；完整指定的型別 (例如 `List<double>,`) 為「封閉式建構型別」或「特製化型別」。 開放式建構類型可用於定義其他泛型類型或方法，而且在指定封入泛型本身之前，可以不必完整指定。 例如，下面是開放式建構類型做為泛型基底類別的用法：

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>條件約束

條件約束是對可做為型別參數之類型的限制。 例如，某一特定泛型類別只能接受繼承自指定類別的類別，或者實作指定的介面。 如需詳細資訊，請參閱[泛型型別參數的限制式 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="reference-types-and-value-types"></a>參考類型和值類型

控制代碼類型和實值類型可做為型別引數使用。 在使用任一類型的泛型定義中，語法會是參考類型的語法。 例如，無論最終使用的型別是參考型別或實值型別，都會使用 `->` 運算子來存取型別參數的型別成員。 當實值類型做為類型引數使用時，執行階段會產生直接使用實值類型的程式碼，而不會對實值類型進行 Boxing 處理。

當使用參考類型做為泛型型別引數時，請使用控制代碼語法。 當使用實值類型做為泛型型別引數時，請直接使用類型的名稱。

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>類型參數

泛型類別中的型別參數會視為其他識別項。 不過，由於類型未知，因此其用途也會有所限制。 例如，您不能使用型別參數類別的成員和方法，除非已知這個型別參數支援這些成員。 也就是說，若要透過型別參數存取成員，您必須將包含成員的類型加入至型別參數的條件約束清單中。

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

這些限制也適用於運算子。 不受條件約束的泛型類型參數不能使用 `==` 和 `!=` 運算子比較類型參數的兩個執行個體。以免該類型不支援這些運算子。 這些檢查是泛型所必要的，但不適合範本，因為泛型可能會在執行階段以任何符合條件約束的類別特製化，而那時再檢查使用的成員是否無效已經太慢。

預設的類型參數執行個體可以使用 `()` 運算子建立。 例如：

`T t = T();`

其中 `T` 是泛型類別或方法定義中的類型參數，會將變數初始化為其預設值。 如果 `T` 是 ref 類別，它會是 null 指標；如果 `T` 是實值類別，則物件會初始化為零。 這稱為「預設初始設定式」。

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)
