---
title: 型別參數的泛型條件約束 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- where
dev_langs:
- C++
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b5a81f8e0472a9f30c8a29a94724063ddae4250
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059996"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>泛型型別參數的條件約束 (C++/CLI)

在泛型類型或方法宣告中，您可以使用條件約束限定型別參數。 條件約束是做為型別引數使用的類型必須符合的需求。 例如，條件約束可能是指，類型引數必須實作特定介面或從特定類別繼承。

條件約束是選擇性的，未在參數上指定條件約束就相當於將該參數限制為 <xref:System.Object>。

## <a name="syntax"></a>語法

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>參數

*型別參數*<br/>
其中一個要限制的型別參數。

*條件約束清單*<br/>
*條件約束清單*是以逗號分隔的條件約束規格清單。 清單可以包括型別參數要實作的介面。

清單也可以包括類別。 為了讓型別引數符合基底類別條件約束，它必須與條件約束的類別相同，或是衍生自條件約束。

您也可以指定**gcnew （)** 來表示型別引數必須具有公用的無參數建構函式，或**ref 類別**表示型別引數必須是參考型別，包括任何類別，介面、 委派或陣列類型，或是**實值類別**來表示的類型引數必須是實值型別。 任何實值型別，可為 Null 以外\<T > 您可以指定。

您也可以指定泛型參數做為條件約束。 針對您要限制的類型提供的型別引數必須是或衍生自條件約束的類型。 這稱為巢狀類型條件約束。

## <a name="remarks"></a>備註

條件約束子句組成**何處**後面接著類型參數、 冒號 (**:**)，和條件約束，型別參數指定限制的性質。 **何處**即時線上關鍵字; 請參閱 <<c2> [ 即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)如需詳細資訊。 分隔多個**其中**空格的定序子句。

條件約束套用至型別參數後，就會對可做為泛型類型或方法的引數使用的類型加以限制。

類別和介面條件約束會指定，引數類型必須是或繼承自指定的類別，或是實作指定的介面。

將條件約束應用至泛型類型或方法，可讓該類型或方法中的程式碼利用條件約束類型的已知功能。 比方說，您可以宣告泛型類別，型別參數實作`IComparable<T>`介面：

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

這個條件約束需要型別引數，已用於`T`實作`IComparable<T>`在編譯時期。 它也可讓介面方法，例如`CompareTo`呼叫。 呼叫介面方法時，不需要再型別參數的執行個體上進行轉型。

型別引數類別中的靜態方法無法透過型別參數呼叫，只能透過實際的具名類型呼叫。

條件約束不能是實值類型，包括內建類型，例如**int**或是**double**。 由於實值類型不能有衍生類別，因此只有一個類別能夠符合條件約束。 在這種情況下，可以重新撰寫泛型，將類型參數取代為特定實值類型。

在某些情況下會需要條件約束，因為編譯器不允許使用未知類型的方法或其他功能，除非條件約束表示未知的類型支援方法或介面。

同一個型別參數的多個條件約束可以使用逗號分隔清單指定。

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

具有多個類型參數，使用其中一個**其中**每個類型參數的子句。 例如: 

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

- 條件約束本身不能是類型參數，但是可以在開放式建構類型中包含類型參數。 例如: 

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

下列範例將示範在型別參數上使用條件約束呼叫執行個體方法。

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

在下列範例中，`T`的內容中的巢狀類型條件約束`Add`方法。

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

[泛型](../windows/generics-cpp-component-extensions.md)