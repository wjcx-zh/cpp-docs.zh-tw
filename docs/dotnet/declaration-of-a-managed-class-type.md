---
title: Managed 的類別類型的宣告 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f9ceb0867fbdfbbdb46075662fca802d1ee0bba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393668"
---
# <a name="declaration-of-a-managed-class-type"></a>Managed 類別類型的宣告

若要宣告參考類別的型別，從 Managed Extensions for c + + 變更為 Visual c + + 方法。

管理擴充功能中參考類別類型前面加上`__gc`關鍵字。 在新語法中，`__gc`關鍵字取代其中兩個含空格關鍵字：`ref class`或`ref struct`。 選擇`struct`或`class`表示公用 (如`struct`) 或私用 (如`class`) 預設存取層級，其成員的宣告類型的主體的初始標記區段中。

同樣地，在受管理的擴充功能，實值類別類型前面加上`__value`關鍵字。 在新語法中，`__value`關鍵字取代其中兩個含空格關鍵字：`value class`或`value struct`。

介面類型，受管理的擴充功能中以關鍵字表示`__interface`。 在新語法中，這會取代`interface class`。

例如，下列類別中的宣告 Managed Extensions:

```
public __gc class Block {};     // reference class
public __value class Vector {}; // value class
public __interface IFooBar {};  // interface class
```

在新語法中這些是以同等方式宣告，如下所示：

```
public ref class Block {};         // reference class
public value class Vector {};      // value class
public interface class IFooBar {}; // interface class
```

## <a name="specifying-the-class-as-abstract"></a>指定的類別為抽象

在受管理的擴充功能，您將關鍵字放`__abstract`之前`class`關鍵字 (在之前或之後`__gc`) 以指出類別是不完整，且在程式內，無法建立類別的物件：

```
public __gc __abstract class Shape {};
public __gc __abstract class Shape2D: public Shape {};
```

在新語法中，您指定`abstract`遵循的類別名稱，然後在類別主體中，基底類別衍生的清單或分號之前的內容關鍵字。

```
public ref class Shape abstract {};
public ref class Shape2D abstract : public Shape{};
```

當然，語意意義不變。

## <a name="specifying-the-class-as-sealed"></a>指定為密封的類別

在受管理的擴充功能，您將關鍵字放`__sealed`之前`class`關鍵字 (在之前或之後`__gc`) 來表示類別的物件，無法繼承自：

```
public __gc __sealed class String {};
```

在新語法中，您指定`sealed`遵循的類別名稱，然後在類別主體中，基底類別衍生的清單或分號之前的內容關鍵字。

您可以同時衍生類別，並將它密封。 例如，`String`類別會隱含地衍生自`Object`。 密封類別的優點是它支援靜態解析度 (也就是在編譯時期) 透過 sealed 的參考類別物件的所有虛擬函式呼叫。 這是因為`sealed`規範可確保`String`追蹤控制代碼時，不能指向後續在衍生類別可能會提供要叫用虛擬方法的覆寫執行個體。 在新語法中，以下是密封類別的範例：

```
public ref class String sealed {};
```

其中也可以指定類別為這兩個抽象和密封-這是特別的條件，表示的靜態類別。 這稱為 CLR 文件中，如下所示：

"的類型，它是兩者`abstract`和`sealed`應該只有靜態成員，並可做為項目有些語言呼叫命名空間。 」

例如，以下是使用 Managed Extensions 語法抽象密封類別的宣告：

```
public __gc __sealed __abstract class State {
public:
   static State() {}
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

而以下是這項宣告轉譯成新的語法：

```
public ref class State abstract sealed {
public:
   static State();
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

## <a name="clr-inheritance-specifying-the-base-class"></a>CLR 繼承： 指定的基底類別

CLR 物件模型中，只公開單一支援繼承。 不過，Managed Extensions 會保留而不需要存取關鍵字與指定的私用衍生的基底類別的 ISO c + + 預設解譯。 這表示每個 CLR 繼承宣告必須提供`public`關鍵字覆寫預設解譯。

```
// Managed Extensions: error: defaults to private derivation
__gc class Derived : Base {};
```

在新的語法定義中，沒有存取關鍵字會指示 CLR 繼承定義中的公用衍生。 因此，`public`存取關鍵字現在是選擇性。 雖然這不需要任何修改 Managed Extensions 的 c + + 程式碼，我會列出此變更此處的完整性。

```
// New syntax: ok: defaults to public derivation
ref class Derived : Base{};
```

## <a name="see-also"></a>另請參閱

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[abstract](../windows/abstract-cpp-component-extensions.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)