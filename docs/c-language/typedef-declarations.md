---
title: Typedef 宣告
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: 6493c5240ca66fc1f12c9617e05072f8399d4786
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468896"
---
# <a name="typedef-declarations"></a>Typedef 宣告

typedef 宣告是將 typedef 宣告為儲存類別的宣告。 宣告子會變成新的類型。 您可以使用 typedef 宣告，針對 C 已經定義或您已經宣告的類型建構較短或更有意義的名稱。 Typedef 名稱可讓您封裝可能變更的實作詳細資料。

typedef 宣告的解譯方式和變數或函式宣告相同，但識別項會變成該類型的同義字，而不是假設宣告所指定的類型。

## <a name="syntax"></a>語法

*宣告*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier declaration-specifiers*<sub>opt</sub>

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**

*type-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*typedef-name*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

請注意，typedef 宣告不會建立類型。 它會建立現有類型的同義字，或是可透過其他方式指定之類型的名稱。 將 typedef 名稱做為類型指定名稱時，它可以結合特定的類型指定名稱，但不能結合其他類型指定名稱。 可接受的修飾詞包含 **const** 與 `volatile`。

Typedef 名稱和一般識別項共用命名空間 (如需詳細資訊，請參閱[命名空間](../c-language/name-spaces.md))。 因此，程式可以具有相同名稱的 typedef 名稱和區域範圍識別項。 例如: 

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

將相同名稱的區域範圍識別項宣告為 typedef 時，或者宣告相同範圍或內部範圍之結構或等位的成員時，必須指定類型指定名稱。 這個範例說明此條件約束：

```C
typedef char FlagType;
const FlagType x;
```

若要重複使用 `FlagType` 名稱做為識別項、結構成員或等位成員的名稱，必須提供類型：

```C
const int FlagType;  /* Type specifier required */
```

只有下列做法是不夠的：

```C
const FlagType;      /* Incomplete specification */
```

因為 `FlagType` 會被當做類型的一部分，而非將重新宣告的識別項。 這個宣告會被視為不合法的宣告，如同

```C
int;  /* Illegal declaration */
```

您可以使用 typedef 宣告任何類型，包括指標、函式和陣列類型。 您可以在定義結構或等位類型之前宣告結構或等位類型指標的 typedef 名稱，只要定義的可見度和宣告相同即可。

Typedef 名稱可用來改善程式碼的可讀性。 下列三個 `signal` 宣告都指定同一個類型，但第一個不使用任何 typedef 名稱。

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>範例

下列範例示範 typedef 宣告：

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

請注意，`WHOLE` 現在可用於變數宣告 (例如 `WHOLE i;` 或 `const WHOLE i;`)。 不過，`long WHOLE i;` 宣告並不合法。

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

這個陳述式會將 `GROUP` 宣告為具有三個成員的結構類型。 由於同時指定了結構標記 `club`，因此宣告中可以使用 typedef 名稱 (`GROUP`) 或結構標籤。 您必須使用結構關鍵字加標記，而無法使用結構關鍵字加 typedef 名稱。

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

`PG` 類型會被宣告為 `GROUP` 類型的指標 (之後也被定義為結構類型)。

```C
typedef void DRAWF( int, int );
```

這個範例提供類型 `DRAWF` 給未傳回任何值的函式，並且接受兩個 int 引數。 例如，這表示宣告

```C
DRAWF box;
```

相當於下列宣告：

```C
void box( int, int );
```

## <a name="see-also"></a>請參閱

[宣告和類型](../c-language/declarations-and-types.md)
