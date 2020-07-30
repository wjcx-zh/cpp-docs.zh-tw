---
title: 編譯器警告（層級4） C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: b107b25714dd3333c3adcb8c83bf56775bf91823
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228748"
---
# <a name="compiler-warning-level-4-c4471"></a>編譯器警告（層級4） C4471

'*列舉*'：不限範圍列舉的向前宣告必須有基礎類型（假設為 int）

找不到不限範圍列舉的向前宣告，但沒有基礎類型的規範。 根據預設，Visual C++ 假設 **`int`** 是列舉的基礎類型。 如果在列舉定義中使用不同的類型（例如，如果指定了不同的明確類型），或如果初始化運算式隱含設定不同的類型，這可能會造成問題。 您也可能有可攜性問題;其他編譯器不會假設 **`int`** 是列舉的基礎類型。

此警告預設為關閉;您可以使用/Wall 或/w*N*4471，在命令列上啟用它，或在原始程式檔中使用 #pragma[警告](../../preprocessor/warning.md)。

在某些情況下，這個警告是偽的。 如果列舉的向前宣告出現在定義之後，可能會引發此警告。 例如，雖然這段程式碼可能會導致 C4471，但這是有效的：

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>範例

一般來說，您可以安全地使用不限範圍列舉的完整定義，而不是向前宣告。 您可以將定義放在標頭檔中，並將它包含在參考它的原始程式檔中。 這適用于以 c + + 98 和更新版本撰寫的程式碼。 我們建議此解決方案提供可攜性和輕鬆維護。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>範例

在 c + + 11 中，您可以將明確類型加入至不限範圍的列舉和其正向宣告。 只有在複雜的標頭包含邏輯防止使用定義而非向前宣告時，才建議您使用此解決方案。 這個方案可能會導致維護問題：如果您變更用於列舉定義的基礎類型，也必須變更所有向前宣告以符合，否則您的程式碼可能會有無訊息錯誤。 您可以將正向宣告放在標頭檔中，以將此問題降至最低。

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

如果您為列舉指定明確的類型，建議您同時啟用 [警告[C4369](compiler-warning-level-1-C4369.md)] （預設為開啟）。 這會識別列舉專案需要的類型與明確指定類型不同的情況。

## <a name="example"></a>範例

您可以變更您的程式碼，以使用範圍列舉，這是 c + + 11 中的新功能。 定義和使用列舉類型的任何用戶端程式代碼都必須變更，才能使用已設定範圍的列舉。 如果您遇到命名空間污染的問題，建議使用已設定範圍的列舉，因為已定義之列舉專案的名稱會限制為列舉的範圍。 範圍列舉的另一個功能是它的成員無法隱含轉換成另一個整數或列舉類型，這可能是微妙錯誤的來源。

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
