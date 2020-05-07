---
title: 簡單變數宣告
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158232"
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

對於算術、結構、等位、列舉和 void 類型，以及 `typedef` 名稱所代表的類型，簡單宣告子可以在宣告中使用，因為類型規範會提供所有類型相關資訊。 指標、陣列和函式類型都需要更複雜的宣告子。

您可以使用以逗號分隔 (**,**) 的識別項清單，在相同的宣告中指定數個變數。 宣告中定義的所有變數都會具有相同的基底類型。 例如：

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

變數 `x` 和 `y` 可以保存集合中以特定實作的 `int` 類型定義的任何值。 簡單物件 `z` 會初始化為值 1，而且不可修改。

如果 `z` 是針對未初始化的靜態變數或是在檔案範圍內宣告，就會收到初始值 0，而且該值不可修改。

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

在這個範例中，`reply` 和 `flag` 這兩個變數都具有 `unsigned long` 類型並且保存不帶正負號的整數值。

## <a name="see-also"></a>請參閱

[宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)
