---
title: 編譯器警告 （層級 4） C4471 |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4471
dev_langs:
- C++
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bcbeafb6952bc40f7fb67c6a0baa2e90051d3ca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023354"
---
# <a name="compiler-warning-level-4-c4471"></a>編譯器警告 （層級 4） C4471

'*列舉型別*': 不限範圍列舉之向前宣告必須含有基礎類型 (假設是 int)

不限範圍列舉之向前宣告找不到沒有規範的基礎類型。 根據預設，Visual c + + 假設`int`是列舉的基礎類型。 如果不同的型別用於列舉型別定義中，例如，如果指定不同的明確類型，或不同的型別會隱含地設定初始設定式，這可能會造成問題。 您可能也必須可攜性問題;其他編譯器不要假設`int`是列舉的基礎類型。

這個警告預設為關閉;您可以使用 /Wall 或 /w*N*來啟用命令列上，或使用 #pragma 4471[警告](../../preprocessor/warning.md)原始程式檔。

在某些情況下，這項警告是假性動作。 如果向前宣告列舉類型出現在定義之後，可能會引發此警告。 比方說，這段程式碼是有效的即使它可能會導致 C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>範例

一般情況下，它是安全地使用完整的定義不限範圍列舉而不是順向宣告。 您可以將定義放在標頭檔，並將它包含參考它的原始程式檔中。 這適用於 C + + 98 和更新版本所撰寫的程式碼。 我們建議此解決方案可攜性和維護的方便性。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>範例

在 C + + 11 中，您可以新增明確的型別，不限範圍列舉型別以及其向前宣告。 只有當複雜的標頭包含邏輯會防止使用而不是順向宣告定義，我們會建議此解決方案。 此解決方案可能會導致維護問題： 如果變更用於列舉型別定義的基礎類型，您也必須變更所有正向宣告相符，或您可能在您的程式碼中的無訊息的錯誤。 您可以放標頭檔，以減少此問題的向前宣告。

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

如果您指定列舉類型的明確型別時，我們建議您同時啟用警告[C4369](compiler-warning-level-1-C4369.md)，預設為開啟。 這會識別列舉項目需要明確指定的型別類型不同的位置的情況。

## <a name="example"></a>範例

您可以變更您的程式碼，以使用限定範圍的列舉，在 C + + 11 中的新功能。 定義和使用列舉類型的任何用戶端程式碼必須變更為使用限定範圍的列舉中。 我們建議您使用限定範圍的列舉有命名空間干擾問題如已定義的列舉型別項目的名稱僅限於列舉的範圍。 限定範圍列舉的另一個功能是其成員無法以隱含方式轉換成另一個整數或列舉類型，它可以是有細微錯誤的來源。

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

