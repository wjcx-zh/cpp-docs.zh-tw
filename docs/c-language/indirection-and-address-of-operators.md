---
title: 間接取值和傳址運算子 | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75afd44b8c0a31d9f3731a4c6f9fb86c15de4328
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389416"
---
# <a name="indirection-and-address-of-operators"></a>間接取值和傳址運算子

間接取值運算子 (__&#42;__) 會透過指標間接存取值。 運算元必須是指標類型。 運算的結果為由運算元定址的值，即其運算元指向位址的值。 結果的類型是運算元所定址的類型。

如果運算元的類型是*類型指標*，則間接取值運算子的結果為*類型*。 如果運算元指向某個函式，則結果為函式指示項。 如果其指向物件，則結果為指定物件的左值。

如果指標值無效，則間接取值運算子的結果為未定義。 下列說明使指標值無效的一些最常見情況：

- 指標是一個 null 指標。

- 指標在參考時指定已過存留期之物件的位址 (例如範圍外的物件或已解除配置的物件)。

- 指標指定的位址與物件指向的類型並不一致。

- 指標指定了執行中程式未使用的位址。

一元傳址運算子 (**&**) 提供其運算元的位址。 運算元必須是指定未宣告 __register__ 且非位元欄位或者非一元 __&#42;__ 運算子結果或陣列參考 (__&#91;&#93;__) 運算子結果之物件的左值，或者必須是函式指示項。 若運算元的類型為*類型*，則結果為*類型指標*的類型。

如果運算元是一元 __&#42;__ 運算子的結果，則不評估運算子，且結果就如同兩者已省略。 結果不是左值，並仍套用運算子的條件約束。 如果運算元是 __&#91;&#93;__ 運算子的結果，則 __&__ 運算子或 __&#91;&#93;__ 運算子隱含的一元 __&#42;__ 皆不評估。 結果和移除 __&__ 運算子及將 __&#91;&#93;__ 運算子變更為 __+__ 運算子具有相同的效果。 否則，結果就是運算元指定之物件或函式的指標。


## <a name="examples"></a>範例

下列是使用這些常見宣告的範例：

```C
int *pa, x;
int a[20];
double d;
```

此陳述式使用傳址運算子 (**&**) 取得陣列 `a` 第六個元素的位址。 結果會儲存在指標變數 `pa`：

```C  
pa = &a[5];
```

此範例中使用間接取值運算子 (__&#42;__) 在儲存於 `pa` 中的位址存取 `int` 值。 該值已指派給整數變數 `x`：

```C
x = *pa;
```

此範例示範對 `x` 位址套用間接取值運算子的結果與 `x` 相同：

```C
assert( x == *&x );
```

此範例示範宣告函式指標的對等方式：

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```  

宣告 `roundup` 函式後，就會宣告及初始化 `roundup` 的兩個指標。 第一個指標 (`proundup`) 只使用函式的名稱初始化，而第二個指標 (`pround`) 則在初始化時使用傳址運算子。 兩個初始化相同。

## <a name="see-also"></a>另請參閱

[間接取值運算子：&#42;](../cpp/indirection-operator-star.md)  
[傳址運算子：&](../cpp/address-of-operator-amp.md)  
