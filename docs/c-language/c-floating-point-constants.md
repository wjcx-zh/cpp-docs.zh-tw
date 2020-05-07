---
title: C 浮點常數
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 5e17490926ee328c3a4ca03b1de9cb6e752959a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325673"
---
# <a name="c-floating-point-constants"></a>C 浮點常數

「浮點常數」是代表帶正負號實數的十進位數字。 帶正負號的實數表示包含整數部分、分數部分和指數。 使用浮點常數表示不能變更的浮點值。

## <a name="syntax"></a>語法

*floating-point-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*數位序列*<sub>選擇</sub> **。** *數位順序*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*數位序列*  **。**

*exponent-part*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *sign*<sub>opt</sub> *位順序*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *sign*<sub>opt</sub> *位順序*

*sign*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*數位-序列*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*八進位*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

您可以省略小數點之前的數字 (值的整數部分)，或小數點之後的數字 (分數部分)，但不能省略兩者。 只有在加入指數時，才可以省略小數點。 不能使用空白字元分隔常數的數字或字元。

下列範例說明某些形式的浮點常數和表示式︰

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

除非前面加上負號（**-**），否則浮點常數為正數。 此時，負號會視為一元算術負運算子。 浮點常數有 `float`、`double` 或 `long double` 型別。

沒有**f**、**F**、**l** 或 **L** 後置字元的浮點常數是 `double` 型別。 如果後置字元是字母 **f** 或 **F**，常數則是 `float` 型別。 如果後置字元是字母 **l** 或 **L**，則是 `long double` 型別。 例如：

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

請注意，Microsoft C 編譯器在內部將 `long double` 表示為 `double` 型別。 如需類型`double`、 `float`和`long double`的詳細資訊，請參閱[基本類型的儲存區](../c-language/storage-of-basic-types.md)。

您可以省略浮點常數的整數部分，如下列範例所示。 數字 .75 可以包括下列多種方式表示︰

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>請參閱

[C 常數](../c-language/c-constants.md)
