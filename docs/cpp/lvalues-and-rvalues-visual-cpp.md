---
title: 值的類別： Lvalues 和 Rvalues （Visual c + +）
ms.date: 04/06/2018
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 301e6140699c921ee1b1229b9183c8555992f716
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330604"
---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues 和 Rvalues （Visual c + +）

每個 c + + 運算式都有類型，而且屬於*值分類*。 值類別是當建立、 複製和移動在運算式評估期間的暫存物件時，編譯器必須遵循的規則的基礎。

C + + 17 標準會定義運算式值的類別，如下所示：

- A *glvalue*是的運算式的評估會決定物件、 位元欄位或函式的身分識別。
- A *prvalue*是其評估初始化物件或位元欄位，或計算運算子的運算元的值，因為在它出現內容所指定的運算式。
- *Xvalue*是代表物件或位元欄位 （通常是因為它是接近其存留期結束時），可以重複使用其資源的 glvalue。 範例： 特定種類的運算式涉及右值參考 (8.3.2) 產生 xvalues，例如其傳回型別是右值參考的函式呼叫或轉型為右值參考類型。
- *左值*是不是 xvalue glvalue。
- *Rvalue* prvalue 或 xvalue。

下圖說明兩個類別之間的關聯性：

![C + + 運算式值類別](media/value_categories.png "c + + 運算式值類別")

左值會有您的程式可以存取的位址。 左值運算式的範例包括變數名稱，包括**const**變數，陣列項目，函式會傳回左值參考、 位元欄位、 等位和類別成員的呼叫。

Prvalue 運算式有沒有可供您的程式存取的位址。 Prvalue 運算式的範例包括常值、 函式呼叫會傳回非參考類型，並只能由編譯器建立運算式評估期間，但可存取的暫存物件。

Xvalue 運算式有一個位址，無法再存取您的程式，但可以用來初始化右值參考，可讓您存取運算式。 範例包括傳回右值參考，以及陣列註標、 成員和指標成員運算式之陣列或物件是右值參考的函式呼叫。

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

    const int ci = 7;
    // Incorrect usage: the variable is a non-modifiable lvalue (C3892).
    ci = 9; // C3892

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;
}
```

> [!NOTE]
> 本主題中的範例將說明運算子未多載時的正確和不正確用法。 藉由多載運算子，您就可以讓像是 `j * 4` 這樣的運算式變成左值。

條款*左值*並*右值*通常會在您參考的物件參考時所使用。 如需參考的詳細資訊，請參閱[左值參考宣告子： &](../cpp/lvalue-reference-declarator-amp.md)並[右值參考宣告子： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
[左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)
