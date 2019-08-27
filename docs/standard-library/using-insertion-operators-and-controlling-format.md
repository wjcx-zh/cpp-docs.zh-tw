---
title: 使用插入運算子和控制格式
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 2cf399501c0eab32e8bee80dfcb98d870c0193cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458030"
---
# <a name="using-insertion-operators-and-controlling-format"></a>使用插入運算子和控制格式

本主題說明如何控制格式，以及如何為您自己的類別的建立插入運算子。 插入 ( **<<** ) 運算子已針對所有標準 C++ 資料類型預先排定，可將位元組傳送至輸出資料流物件。 插入運算子會使用預先定義的「操作工具」，這是會變更整數引數預設格式的元素。

您可以使用下列選項來控制格式：

- [輸出寬度](#vclrfoutputwidthanchor3)

- [對齊](#vclrfalignmentanchor4)

- [整數位數](#vclrfprecisionanchor5)

- [基數](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a> 輸出寬度

若要對齊輸出, 您可以藉由將操作工具放`setw`入資料流程或`width`呼叫成員函式, 來指定每個專案的輸出寬度。 此範例會以至少 10 個字元的寬度靠右對齊資料行中的值：

```cpp
// output_width.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   for( int i = 0; i < 4; i++ )
   {
      cout.width(10);
      cout << values[i] << '\n';
   }
}
```

```Output
      1.23
     35.36
     653.7
   4358.24
```

任何寬度少於 10 個字元的值，都會加入前置空白。

若要填補欄位, 請使用`fill`成員函式, 為具有指定寬度的欄位設定填補字元的值。 預設值為空白。 若要以星號填補數字資料行，請以下列方式修改先前的 **for** 迴圈：

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

`endl` 操作工具會取代新行字元 (`'\n'`)。 輸出顯示如下：

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

若要指定同一行中的資料元素寬度，請使用 `setw` 操作工具：

```cpp
// setw.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };
   for( int i = 0; i < 4; i++ )
      cout << setw( 7 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

成員函式是在 iostream \<> 中宣告。 `width` 如果您將 `setw` 或任何其他操作工具與引數搭配使用，您必須加入 \<iomanip>。 在輸出中，字串會列印在寬度為 6 的欄位中，整數則列印在寬度為 10 的欄位中：

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

`setw` 和`width`都不會截斷值。 如果格式化輸出超過寬度，則會根據資料流的精確度設定列印整個值。 `setw` 和`width`都只會影響下欄欄位。 在列印欄位之後，欄位寬度會回復原預設行為 (必要寬度)。 不過，其他資料流格式選項在變更之前仍然有效。

## <a name="vclrfalignmentanchor4"></a> 對齊

輸出資料流預設為靠右對齊文字。 若要將前述範例中的名稱靠左對齊，並將數值靠右對齊，請依照下列方式取代 **for** 迴圈：

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

輸出顯示如下：

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

使用 [setiosflags](../standard-library/iomanip-functions.md#setiosflags) 操作工具和 `left` 列舉值可設定靠左對齊旗標。 此列舉值定義於 [ios](../standard-library/basic-ios-class.md) 類別中，因此其參考必須包含 **ios::** 前置詞。 [resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) 操作工具會關閉靠左對齊旗標。 與`width`和`setw`不同, `setiosflags`和的效果是永久性的。`resetiosflags`

## <a name="vclrfprecisionanchor5"></a> 整數位數

浮點精確度的預設值為六。 例如，數值 3466.9768 會列印為 3466.98。 若要變更此值的列印方式，請使用 [setprecision](../standard-library/iomanip-functions.md#setprecision) 操作工具。 此操作工具有兩個旗標：[固定](../standard-library/ios-functions.md#fixed)和[科學](../standard-library/ios-functions.md#scientific)。 如果設定了[固定](../standard-library/ios-functions.md#fixed)，則此數值會列印為 3466.976800。 如果`scientific`設定, 則會列印為 3.4669773 + 003。

若要以具有一個有效位數的[對齊](#vclrfalignmentanchor4)方式顯示浮點數，請以下列方式取代 **for** 迴圈：

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6)
         << names[i]
         << resetiosflags(ios::left)
         << setw(10)
         << setprecision(1)
         << values[i]
         << endl;
```

程式會列印這份清單：

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

若要消除科學標記法，請在 **for** 迴圈前面插入下列陳述式：

```cpp
cout << setiosflags(ios::fixed);
```

使用固定標記法時，程式會在小數點後面列印一位數。

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

如果您將`ios::fixed`旗標變更`ios::scientific`為, 程式會列印下列內容:

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

同樣地，程式會在小數點後面列印一位數。 如果設定了`ios::scientific`或,則精確度值會決定小數點後面的位數。 `ios::fixed` 如果未設定任一旗標，精確度值將會決定有效位數的總數。 `resetiosflags` 操作工具會清除這些旗標。

## <a name="vclrfradixanchor6"></a> 基數

`dec`、和操作`hex`工具會設定輸入和輸出的預設基數。 `oct` 例如, 如果您將操作工具`hex`插入輸出資料流程中, 物件會正確地將整數的內部資料標記法轉譯成十六進位輸出格式。 如果清除[大寫](../standard-library/ios-functions.md#uppercase)旗標 (預設值)，將會以小寫的 a 到 f 顯示數字；否則會以大寫顯示。 預設基數為`dec` (十進位)。

## <a name="quoted-strings-c14"></a>使用引號的字串 (C++14)

當您將字串插入至資料流時，您可以呼叫 stringstream::str() 成員函式，輕鬆地將相同的字串擷取回來。 不過，如果您後續想要使用擷取運算子將資料流插入新的字串中，可能會出現非預期的結果，因為 >> 運算子依預設會在遇到第一個空白字元時停止。

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

這種行為可以手動解決, 但是為了讓字串往返更方便, c + + 14 會在`std::quoted` p > 中\<加入資料流程操作工具。 在插入時，`quoted()` 會在字串兩側加上分隔符號 (預設為雙引號 '"')，並在進行擷取時使資料流擷取所有字元，直到最後一個分隔符號為止。 任何內嵌引號都會以逸出字元 (預設為 '\\\\') 逸出。

分隔符號只會出現在資料流程物件中;它們不會出現在解壓縮的字串中, 但會出現在[basic_stringstream:: str](../standard-library/basic-stringstream-class.md#str)所傳回的字串中。

插入和擷取作業的空白行為與字串在程式碼中的呈現方式無關，因此無論輸入字串是原始字串常值還是一般字串，加上引號的運算子都有效用。 輸入字串無論採用何種格式，都可以有內嵌引號、換行符號、定位字元等項目，且 quoted() 操作工具會保留前述所有的項目。

如需詳細資訊和完整的程式碼範例, 請參閱[加上引號](../standard-library/iomanip-functions.md#quoted)。

## <a name="see-also"></a>另請參閱

[輸出資料流](../standard-library/output-streams.md)
