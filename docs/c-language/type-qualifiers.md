---
title: 類型限定詞
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: 729e9f65fd1054b8381f45b81e5276846145ebc1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198719"
---
# <a name="type-qualifiers"></a>類型限定詞

類型限定詞會提供兩個屬性的其中一個給識別項。 **`const`** 類型限定詞會將物件宣告為不可修改。 **`volatile`** 類型限定詞會宣告一個專案，其值可由超出其出現的程式控制範圍（例如同時執行的執行緒）合法地變更。

這兩個類型限定詞 **`const`** 和只能 **`volatile`** 在宣告中出現一次。 類型限定詞可搭配任何類型規範出現，不過不能出現在多重項目宣告中的第一個逗號後面。 例如，下列宣告是合法的：

```
typedef volatile int VI;
const int ci;
```

下列宣告是不合法的：

```
typedef int *i, volatile *vi;
float f, const cf;
```

類型限定詞只有在存取做為運算式中左值的識別項時才相關。 如需有關左值和運算式的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。

## <a name="syntax"></a>語法

*type-qualifier*: **constvolatile**

以下是合法 **`const`** 和宣告 **`volatile`** ：

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

如果陣列類型的規格包括類型限定詞，則元素為限定，而不是陣列類型。 如果函式類型的規格包含限定詞，則行為會是未定義。 和都不 **`volatile`** **`const`** 會影響物件的值範圍或算術屬性。

這份清單說明如何使用 **`const`** 和 **`volatile`** 。

- **`const`** 關鍵字可以用來修改任何基本或匯總類型，或任何類型之物件的指標，或 **`typedef`** 。 如果專案僅以 **`const`** 類型限定詞宣告，其類型會被視為**const int**。**`const`** 變數可以初始化，也可以放在儲存區的唯讀區域中。 **`const`** 關鍵字對於宣告的指標很有用， **`const`** 因為這需要函式不會以任何方式變更指標。

- 編譯器會假設在程式中的任何時間點， **`volatile`** 變數都可以由使用或修改其值的未知進程來存取。 因此，不論在命令列上指定的優化為何，都必須產生變數的每個或參考的程式碼， **`volatile`** 即使它似乎沒有任何作用也一樣。

   如果 **`volatile`** 單獨使用， **`int`** 則會假設為。 **`volatile`** 型別規範可用來提供可靠的存取權給特殊的記憶體位置。 搭配 **`volatile`** 信號處理常式、並存執行程式或特殊硬體（例如記憶體對應 i/o 控制暫存器）存取或變更的資料物件使用。 您可以將變數宣告為 **`volatile`** 它的存留期，也可以將單一參考轉換為 **`volatile`** 。

- 專案可以同時是 **`const`** 和 **`volatile`** ，在這種情況下，專案無法由自己的程式合法修改，但是可以由某個非同步進程進行修改。

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
