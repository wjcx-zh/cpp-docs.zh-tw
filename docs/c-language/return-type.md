---
title: 傳回型別
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
ms.openlocfilehash: 3f781e59672764dc518f3c6fad61d4021720362a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148136"
---
# <a name="return-type"></a>傳回型別

函式的傳回型別會建立函式傳回值的大小和類型，並且對應於下列語法中的類型規範：

## <a name="syntax"></a>語法

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* 是 Microsoft 專有 \*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8** /\* Microsoft 專有 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16** /\* Microsoft 專有 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32** /\* Microsoft 專有 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64** /\* Microsoft 專有 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-specifier* 可以指定任何基本、結構或等位型別。 如果您未包含 *type-specifier*，則會假設為傳回型別 `int`。

函式定義中提供的傳回型別必須符合程式中其他位置之函式宣告中的傳回型別。 當包含運算式的 `return` 陳述式執行時，函式就會傳回值。 會求出運算式的值，於必要時轉換成傳回值類型，並且返回呼叫函式所在的點。 如果函式是使用傳回類型 `void` 宣告，則包含運算式的傳回陳述式會產生警告，而且不會求出運算式的值。

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

這個範例會定義具有 `STUDENT` 宣告的 `typedef` 類型，並且將函式 `sortstu` 定義為具有 `STUDENT` 傳回類型。 函式會選取並傳回它的兩個結構引數的其中一個。 在後續函式呼叫中，編譯器會檢查並確定引數類型為 `STUDENT`。

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

這個範例會定義傳回字元陣列指標的函式。 這個函式會採用兩個字元陣列 (字串) 做為引數，並傳回兩個字串中較短者的指標。 陣列指標會指向第一個陣列元素並擁有其類型，因此，函式的傳回類型會是 `char` 類型的指標。

您不需要在呼叫函式之前使用 `int` 傳回類型宣告函式，不過建議您使用原型，如此才能夠檢查引數和傳回值的類型是否正確。

## <a name="see-also"></a>另請參閱

[C 函式定義](../c-language/c-function-definitions.md)
