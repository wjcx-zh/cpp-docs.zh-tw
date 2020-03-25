---
title: 泛型類型參數的條件約束 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: be5af8f6b2edaa8f93fef7ae06b2175b54b25396
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172474"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>泛型類型參數的條件約束 (C++/CLI)

在泛型類型或方法宣告中，您可以使用條件約束限定類型參數。 條件約束是做為類型引數使用的類型必須符合的需求。 例如，條件約束可能是指，類型引數必須實作特定介面或從特定類別繼承。

條件約束是選擇性的，未在參數上指定條件約束就相當於將該參數限制為 <xref:System.Object>。

## <a name="syntax"></a>語法

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>參數

*type-parameter*<br/>
其中一個要限制的型別參數。

*constraint list*<br/>
*constraint list* 是以逗號分隔的限制式規格清單。 清單可以包括型別參數要實作的介面。

清單也可以包括類別。 為了讓類型引數符合基底類別條件約束，它必須與條件約束的類別相同，或是衍生自條件約束。

您也可以指定 **gcnew()** ，以指出型別引數必須具有公用的無參數建構函式；或指定 **ref class**，以指出型別引數必須是參考型別，包括任何類別、介面、委派或陣列型別；或指定 **value class**，以指出型別引數必須是實值型別。 您可以指定 Nullable\<T> 以外的任何實值型別。

您也可以指定泛型參數做為條件約束。 針對您要限制的類型提供的型別引數必須是或衍生自條件約束的類型。 這稱為巢狀類型條件約束。

## <a name="remarks"></a>備註

限制式子句包括 **where**，後面接著型別參數、冒號 ( **:** ) 及限制式 (可用於指定型別參數上限制的性質)。 **where** 是內容相關性關鍵字；如需詳細資訊，請參閱[內容相關性關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。 請以空格分隔多個 **where** 子句。

條件約束套用至型別參數後，就會對可做為泛型類型或方法的引數使用的類型加以限制。

類別和介面條件約束會指定，引數類型必須是或繼承自指定的類別，或是實作指定的介面。

將條件約束應用至泛型類型或方法，可讓該類型或方法中的程式碼利用條件約束類型的已知功能。 例如，您可以宣告泛型類別，讓型別參數能夠實作 `IComparable<T>` 介面：

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

這個限制式要求用於 `T` 的引數在編譯時間實作 `IComparable<T>`。 另外也允許呼叫介面方法，例如 `CompareTo`。 呼叫介面方法時，不需要再類型參數的執行個體上進行轉型。

類型引數類別中的靜態方法無法透過類型參數呼叫，只能透過實際的具名類型呼叫。

限制式不可以是實值型別，包括 **int** 或 **double** 等內建型別。 由於實值類型不能有衍生類別，因此只有一個類別能夠符合條件約束。 在這種情況下，可以重新撰寫泛型，將型別參數取代為特定實值類型。

在某些情況下會需要條件約束，因為編譯器不允許使用未知類型的方法或其他功能，除非條件約束表示未知的類型支援方法或介面。

同一個類型參數的多個條件約束可以使用逗號分隔清單指定。

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

若有多個型別參數，請對每個型別參數使用一個 **where** 子句。 例如：

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

總而言之，請根據下列規則在程式碼中使用條件約束：

- 如果列出了多個條件約束，條件約束可依照任意順序列出。

- 條件約束也可以是類別類型，例如抽象基底類別。 不過，條件約束不可以是實值類型或密封類別。

- 條件約束本身不能是型別參數，但是可以在開放式建構類型中包含型別參數。 例如：

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>範例

下列範例將示範在類型參數上使用條件約束呼叫執行個體方法。

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

## <a name="example"></a>範例

當泛型型別參數做為條件約束使用時，它稱為巢狀類型條件約束。 當具有自己的型別參數之成員函式需要將該參數限制為包含類型的型別參數時，巢狀類型條件約束就很有用。

在下列範例中，`T` 是 `Add` 方法內容中的 Naked 型別限制式。

巢狀類型參數也可以在泛型類別定義中使用。 巢狀類型條件約束對泛型類別來說並不那麼實用，因為編譯器除了會假設巢狀類型約束條件衍生自 <xref:System.Object> 之外，不會再做其他任何假設。 如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上使用巢狀類型條件約束。

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)
