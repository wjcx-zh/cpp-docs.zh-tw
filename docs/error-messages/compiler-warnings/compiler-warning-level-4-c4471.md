---
title: 編譯器警告 (層級 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 5b8c3ef419a4c6eaf9a674827cd5545a1f1b2bfe
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685498"
---
# <a name="compiler-warning-level-4-c4471"></a>編譯器警告 (層級 4) C4471

'*enumeration*'：不限範圍列舉的向前宣告必須有 (int 的基礎類型) 

找到不限範圍列舉的向前宣告，但沒有基礎類型的規範。 根據預設，Visual C++ **`int`** 會假設為列舉的基礎類型。 如果列舉定義中使用不同的型別（例如，如果指定了不同的明確型別），或是由初始化運算式隱含設定不同的型別，這可能會造成問題。 您可能也會有可攜性問題;其他編譯器 **`int`** 則不會假設為列舉的基礎類型。

此警告預設為關閉;您可以使用/Wall 或/w*N*4471 在命令列上啟用它，或在原始程式檔中使用 #pragma [警告](../../preprocessor/warning.md) 。

## <a name="examples"></a>範例

在某些情況下，此警告為偽。 如果列舉的向前宣告出現在定義之後，可能會引發此警告。 例如，雖然這段程式碼可能會造成 C4471，不過這個程式碼是有效的：

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

一般而言，您可以放心地針對不限範圍列舉（而非向前宣告）使用完整定義。 您可以將定義放在標頭檔中，並將其包含在參考它的原始程式檔中。 這適用于以 c + + 98 和更新版本撰寫的程式碼。 我們建議將此解決方案用於可攜性和容易維護。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

在 c + + 11 中，您可以將明確類型加入至不限範圍的列舉和其向前宣告。 只有當複雜標頭包含邏輯防止使用定義而不是向前宣告時，才建議使用此解決方案。 此解決方案可能會導致維護問題：如果您變更列舉定義所使用的基礎型別，您也必須將所有的向前宣告變更為相符，否則您的程式碼中可能會有無訊息錯誤。 您可以將轉寄宣告放在標頭檔中，以將此問題降至最低。

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

如果您為列舉指定明確的型別，建議您也啟用預設為開啟的警告 [C4369](compiler-warning-level-1-C4369.md)。 這會找出列舉專案所需的類型與明確指定類型不同的案例。

您可以變更程式碼，以使用範圍列舉，這是 c + + 11 中的新功能。 定義和使用列舉型別的任何用戶端程式代碼都必須變更為使用範圍列舉。 如果您有命名空間污染的問題，建議您使用已設定領域的列舉，因為定義的列舉專案名稱會限制為列舉的範圍。 範圍列舉的另一項功能，就是它的成員無法隱含轉換成另一個整數或列舉型別，而這可能是微妙錯誤的來源。

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```
