---
title: C 抽象宣告子
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 540b938e2c4121f189216942bc06630fc61ee19c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220856"
---
# <a name="c-abstract-declarators"></a>C 抽象宣告子

抽象宣告子是一個沒有識別項的宣告子，由一個或多個指標、陣列或函式修飾符組成。 指標修飾詞（ <strong>\*</strong> ）一律在宣告子的識別碼之前，陣列（**[]**）和函式（ **（）** ）修飾詞會遵循識別碼。 知道這一點後，您就可以判斷識別項會出現在抽象宣告子的哪個位置，並據以解譯宣告子。 如需複雜宣告子的詳細資訊和範例，請參閱[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md)。 一般來說 **`typedef`** ，可以用來簡化宣告子。 請參閱 [Typedef 宣告](../c-language/typedef-declarations.md)。

抽象宣告子可能很複雜。 複雜抽象宣告子中的括號會指定特定的解譯，就如同在宣告中針對複雜宣告子所做的動作。

這些範例說明抽象宣告子：

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
> 由一組空括號 "**( )**" 組成的抽象宣告子會造成模稜兩可的情況，因此不允許使用。 要判斷隱含的識別項是落在括號內部 (在此情況下它是未經修改的類型) 或在括號前面 (在此情況下它是函式類型) 是不可能的。

## <a name="see-also"></a>另請參閱

[宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)
