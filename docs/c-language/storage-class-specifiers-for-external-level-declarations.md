---
title: 外部層級宣告的儲存類別指定名稱
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 6c30b8a12c0bf26bc35905872fb6fa527b367ef4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229463"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>外部層級宣告的儲存類別指定名稱

外部變數是指在檔案範圍的變數。 這些變數是在任何函式之外定義，因此可能可供許多函式使用。 由於函式只能在外部層級定義，因此不可為巢狀。 根據預設，所有對相同名稱之外部變數和函式的參考都是相同物件的參考，這表示它們具有*外部連結*。 （您可以使用 **`static`** 關鍵字來覆寫此行為）。

外部層級的變數宣告是變數（*定義*宣告）的定義，或在其他地方定義之變數的參考（*參考*宣告）。

若外部變數宣告也會初始化變數 (隱含或明確)，則是定義變數的宣告。 外部層級的定義可採用數種形式：

- 您使用 **`static`** 儲存類別規範宣告的變數。 您可以 **`static`** 使用常數運算式來明確初始化變數，如[初始化](../c-language/initialization.md)中所述。 如果您省略初始設定式，則預設會將變數初始化為 0。 例如，這兩個陳述式都視為變數 `k` 的定義。

    ```C
    static int k = 16;
    static int k;
    ```

- 您在外部層級明確初始化的變數。 例如，`int j = 3;` 是變數 `j` 的定義。

在外部層級（也就是在所有函數之外）的變數宣告中，您可以使用 **`static`** 或 **`extern`** 儲存類別規範，或完全省略儲存類別規範。 您不能 **`auto`** **`register`** *`storage-class-specifier`* 在外部層級使用和終端機。

一旦在外部層級定義變數，該變數在轉譯單位的所有其餘部分就會是可見狀態。 變數在相同原始程式檔中宣告之前為不可見。 此外，除非參考宣告讓該變數成為可見，否則它在程式的其他原始程式檔中也不可見，如下所述。

與相關的規則 **`static`** 包括：

- 不含關鍵字的所有區塊外宣告 **`static`** 的變數一律會在整個程式中保留其值。 若要限制其對特定轉譯單位的存取，您必須使用 **`static`** 關鍵字。 這會提供*內部連結*。 若要使其成為整個程式的全域，請省略明確的儲存類別，或使用關鍵字 **`extern`** （請參閱下一份清單中的規則）。 這會提供*外部連結*。 內部和外部連結也將在[連結](../c-language/linkage.md)中加以討論。

- 您只能在程式內於外部層級定義變數一次。 您可以在不同的轉譯單位中，定義另一個具有相同名稱和 **`static`** 儲存類別規範的變數。 由於每個 **`static`** 定義只有在自己的轉譯單位內才可見，因此不會發生衝突。 它提供一個有用的方式來隱藏必須在單一轉譯單位的函式之間共用的識別碼名稱，但其他轉譯單位看不到。

- **`static`** 儲存類別規範也可以套用至函式。 如果您宣告函式 **`static`** ，其名稱在其宣告所在的檔案外部不可見。

使用的規則 **`extern`** 包括：

- **`extern`** 儲存類別規範會宣告在其他位置定義之變數的參考。 您可以使用宣告 **`extern`** ，讓另一個原始程式檔中的定義變成可見，或讓變數在相同原始程式檔中的定義之前顯示。 一旦在外部層級宣告變數的參考之後，變數就會顯示在宣告的參考發生的轉譯單元的其餘部分。

- **`extern`** 若要讓參考有效，它所參考的變數必須在外部層級定義一次。 這個定義（不含 **`extern`** 儲存類別）可以是組成程式的任何轉譯單位。

## <a name="example"></a>範例

下列範例將說明外部宣告：

```C
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

這個範例中的兩個原始程式檔總共包含三個 `i` 的外部宣告。 其中只有一個宣告為「定義宣告」。 該宣告：

```C
int i = 3;
```

會定義全域變數 `i` 並以初始值 3 將它初始化。 第一個來源檔案頂端的「參考」宣告，會在檔案 `i` **`extern`** 中的定義宣告之前，讓全域變數可見。 第二個原始程式檔中 `i` 的參考宣告也會讓變數在該原始程式檔中成為可見。 如果轉譯單位中未提供定義變數的執行個體，編譯器會假設有

```C
extern int x;
```

參考宣告，而且定義參考

```C
int x = 0;
```

出現在程式的另一個轉譯單位中。

這三個函式 `main`、`next` 和 `other` 全都會執行相同的工作：它們會增加並列印 `i`。 列印的值為 4、5 和 6。

如果變數 `i` 尚未初始化，則會自動設定為0。 在這種情況下會列印值 1、2 和 3。 如需變數初始化的詳細資訊，請參閱[初始化](../c-language/initialization.md)。

## <a name="see-also"></a>另請參閱

[C 儲存類別](../c-language/c-storage-classes.md)
