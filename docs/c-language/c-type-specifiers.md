---
title: C 類型指定名稱
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 652388fdf345cab7878bbd8c054b769377b322a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217151"
---
# <a name="c-type-specifiers"></a>C 類型指定名稱

宣告中的類型指定名稱會定義變數或函式宣告的類型。

## <a name="syntax"></a>語法

*類型規範*： &nbsp; &nbsp; &nbsp; &nbsp; **`void`** &nbsp; &nbsp; &nbsp; &nbsp; **`char`** &nbsp; &nbsp; &nbsp; &nbsp; **`short`** &nbsp; &nbsp; &nbsp; &nbsp; **`int`** &nbsp; &nbsp; &nbsp; &nbsp; **`long`** &nbsp; &nbsp; &nbsp; &nbsp; **`float`** &nbsp; &nbsp; &nbsp; &nbsp; **`double`** &nbsp; &nbsp; &nbsp; &nbsp; **`signed`** &nbsp; &nbsp; &nbsp; &nbsp; **`unsigned`** &nbsp; &nbsp; &nbsp; &nbsp; *結構或*等位-規範 &nbsp; &nbsp; &nbsp; &nbsp; *列舉規範* &nbsp; &nbsp; &nbsp; &nbsp; *typedef-名稱*

**`signed char`**、 **`signed int`** 、 **`signed short int`** 和帶正負號的**long int**類型連同其 **`unsigned`** 對應的和 **`enum`** ，都稱為*整數*類型。 **`float`**、 **`double`** 和類型指定名稱稱為「 **`long double`** *浮點*」或「*浮點*」類型。 您可以在變數或函式宣告中使用任何整數或浮點類型指定名稱。 如果宣告中未提供*類型規範*，則會將它視為 **`int`** 。

選擇性的關鍵字 **`signed`** 和 **`unsigned`** 可以在任何整數類資料類型之前或後面，除了之外， **`enum`** 也可以單獨當做類型規範使用，在此情況下，它們會 **`signed int`** 分別理解為和 **`unsigned int`** 。 單獨使用時，關鍵字 **`int`** 會假設為 **`signed`** 。 單獨使用時，會將關鍵字 **`long`** 和 **`short`** 理解為**long int**和 **`short int`** 。

列舉類型被視為基本類型。 列舉類型的類型指定名稱會在[列舉宣告](../c-language/c-enumeration-declarations.md)中討論。

關鍵字 **`void`** 有三個用途：指定函式傳回類型、指定不採用任何引數之函數的引數類型清單，以及指定未指定類型的指標。 您可以使用類型來宣告未傳回 **`void`** 任何值的函式，或宣告未指定類型的指標。 如[Arguments](../c-language/arguments.md)需在函式 **`void`** 名稱後面的括弧中單獨出現時的資訊，請參閱引數。

**Microsoft 特定的**

類型檢查現在符合 ANSI 標準，這表示類型 **`short`** 和類型 **`int`** 是不同的類型。 例如，這是在舊版編譯器中接受之 Microsoft C 編譯器的重新定義。

```C
int   myfunc();
short myfunc();
```

下一個範例也會產生關於不同類型間接取值的警告：

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Microsoft C 編譯器也會產生是否帶正負號之差異的警告。 例如：

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

類型 **`void`** 運算式會針對副作用進行評估。 您不能以任何方式使用具有類型之運算式的（不存在）值 **`void`** ，也不能將 **`void`** 運算式（透過隱含或明確轉換）轉換成除了以外的任何類型 **`void`** 。 如果您在需要運算式的內容中使用任何其他類型的運算式 **`void`** ，則會捨棄其值。

為符合 ANSI 規格， <strong>void \* \* </strong>不能用來做為<strong>int \* \* </strong>。 只能 **`void`** <strong>\*</strong> 用來做為未指定類型的指標。

**結束 Microsoft 專有**

您可以使用宣告建立其他類型指定名稱 **`typedef`** ，如[Typedef](../c-language/typedef-declarations.md)宣告中所述。 如需每種類型之大小的詳細資訊，請參閱[基本類型的儲存區](../c-language/storage-of-basic-types.md)。

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
