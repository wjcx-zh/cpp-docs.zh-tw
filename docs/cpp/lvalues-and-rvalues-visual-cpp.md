---
title: 值類別：左值和右值（c + +）
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: b4b3ba5fdbc11ec97870b0f06fd1aabd3b57f5ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225965"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues 和 Rvalues (C++)

每個 c + + 運算式都有類型，而且屬於*值分類*。 值類別目錄是編譯器在運算式評估期間建立、複製和移動暫存物件時必須遵循之規則的基礎。

C + + 17 標準定義了運算式值分類，如下所示：

- *Glvalue*是一種運算式，其評估會決定物件、位欄位或函數的識別。
- *X prvalue*是一種運算式，其評估會初始化物件或位欄位，或計算運算子的運算元值，如其出現所在內容所指定。
- *Xvalue*是一種 glvalue，代表可以重複使用其資源的物件或位欄位（通常是因為它在其存留期的結尾附近）。 範例：牽涉到右值參考（8.3.2）的特定類型運算式會產生 xvalues，例如呼叫的函式，其傳回類型是 rvalue 參考，或轉換成右值參考型別。
- *左*值是不是 xvalue 的 glvalue。
- *右*值是 x prvalue 或 xvalue。

下圖說明類別之間的關聯性：

![C + + 運算式值類別目錄](media/value_categories.png "C + + 運算式值類別目錄")

左值具有您的程式可以存取的位址。 左值運算式的範例包括變數名稱，包括 **`const`** 變數、陣列元素、傳回左值參考的函式呼叫、位欄位、等位和類別成員。

X prvalue 運算式沒有可供您的程式存取的位址。 X prvalue 運算式的範例包括常值、傳回非參考型別的函式呼叫，以及在運算式 evalution 期間建立的暫存物件，但只能由編譯器存取。

Xvalue 運算式具有您的程式無法再存取的位址，但可用來初始化右值參考，以提供運算式的存取權。 範例包括傳回右值參考的函式呼叫，以及陣列或物件為 rvalue 參考之成員運算式的陣列注標、成員和指標。

## <a name="example"></a>範例

下列範例將示範數種正確和不正確的左值和右值用法：

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> 本主題中的範例將說明運算子未多載時的正確和不正確用法。 藉由多載運算子，您就可以讓像是 `j * 4` 這樣的運算式變成左值。

當您參考物件參考時，通常會使用「*左*值」和「*右*值」等詞彙。 如需參考的詳細資訊，請參閱左值參考宣告子[： &](../cpp/lvalue-reference-declarator-amp.md)和右值參考宣告子[：  &&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
[左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)
