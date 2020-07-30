---
title: 傳回類型
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 1d905e02be02784b562b9d1a8f72a9bfa4057b9b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226323"
---
# <a name="return-type"></a>傳回類型

函式的傳回型別會建立函式傳回值的大小和類型，並且對應於下列語法中的類型規範：

## <a name="syntax"></a>語法

*函式定義*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\**屬性-seq*是 Microsoft 特有的\*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int8`** /\*Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int16`** /\*Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int32`** /\*Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int64`** /\*Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct 或 union-規範*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*列舉規範*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-名稱*

*type-specifier* 可以指定任何基本、結構或等位型別。 如果您未包含*類型規範*，則會假設為傳回類型 **`int`** 。

函式定義中提供的傳回型別必須符合程式中其他位置之函式宣告中的傳回型別。 當執行包含運算式的語句時，函數會傳回值 **`return`** 。 會求出運算式的值，於必要時轉換成傳回值類型，並且返回呼叫函式所在的點。 如果函式是使用傳回型別宣告 **`void`** ，則包含運算式的 return 語句會產生警告，而且不會評估運算式。

下列範例將說明函式傳回值。

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

這個範例會定義 `STUDENT` 具有宣告的類型，並將函式 **`typedef`** 定義 `sortstu` 為具有傳回 `STUDENT` 類型。 函式會選取並傳回它的兩個結構引數的其中一個。 在後續函式呼叫中，編譯器會檢查並確定引數類型為 `STUDENT`。

> [!NOTE]
> 不傳遞整個結構，而是傳遞結構的指標，可提升效率。

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

這個範例會定義傳回字元陣列指標的函式。 這個函式會採用兩個字元陣列 (字串) 做為引數，並傳回兩個字串中較短者的指標。 陣列的指標會指向陣列元素的第一個，並具有其類型。因此，函式的傳回類型是類型的指標 **`char`** 。

您不需要在呼叫函式之前宣告具有傳回類型的函式 **`int`** ，雖然我們建議使用原型，以便啟用引數和傳回值的正確類型檢查。

## <a name="see-also"></a>另請參閱

[C 函式定義](../c-language/c-function-definitions.md)
