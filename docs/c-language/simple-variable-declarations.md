---
title: 簡單變數宣告
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 42547828e78566982053d22e8288fe1ccbe6e26b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229528"
---
# <a name="simple-variable-declarations"></a>簡單變數宣告

簡單變數的宣告 (直接宣告子的最簡單形式) 會指定變數的名稱和類型。 另外也會指定變數的儲存類別和資料類型。

儲存類別或類型 (或兩者皆是) 為變數宣告中所必要。 不具類型的變數 (例如 `var;`) 會產生警告。

## <a name="syntax"></a>語法

宣告*子：*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct-* 宣告子：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*

*識別碼*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼* *數字*

針對算術、結構、等位、列舉和 void 類型，以及名稱所代表的類型 **`typedef`** ，可以在宣告中使用簡單宣告子，因為類型規範會提供所有輸入資訊。 指標、陣列和函式類型都需要更複雜的宣告子。

您可以使用以逗號分隔 (**,**) 的識別項清單，在相同的宣告中指定數個變數。 宣告中定義的所有變數都會具有相同的基底類型。 例如：

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

變數 `x` 和 `y` 可以保存集合中的任何值，該 **`int`** 類型是由特定的執行所定義。 簡單物件 `z` 會初始化為值 1，而且不可修改。

如果 `z` 是針對未初始化的靜態變數或是在檔案範圍內宣告，就會收到初始值 0，而且該值不可修改。

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

在此範例中，和這兩個變數 `reply` `flag` 都具有 **`unsigned long`** 類型並保留不帶正負號的整數值。

## <a name="see-also"></a>另請參閱

[宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)
