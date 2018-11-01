---
title: 解析模稜兩可的宣告 （c + +）
ms.date: 11/04/2016
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
ms.openlocfilehash: 52e94f474d59505298cb4f78a477cedd21b90aad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507363"
---
# <a name="resolving-ambiguous-declarations-c"></a>解析模稜兩可的宣告 （c + +）

若要從一個類型明確轉換成另一個類型，您必須使用轉型來指定所需的類型名稱。 某些類型轉換會導致語意模稜兩可的情況。 下列函式樣式類型轉換就是模稜兩可的情況：

```cpp
char *aName( String( s ) );
```

不清楚它是函式宣告或是物件宣告的函式樣式轉換為初始設定式： 它可以宣告傳回類型的函式`char *`採用一個引數的型別`String`，也可以宣告的物件`aName`並將它初始化的值`s`轉型為類型`String`。

如果宣告可以視為有效的函式宣告，則會以此方式處理。 只有在不可能是函式宣告的情況下 (也就是它的語意不正確)，才會查看陳述式是否為函式樣式類型轉換。 因此，編譯器會將陳述式視為函式宣告，必且忽略識別項 `s` 前後的括號。 換句話說，陳述式：

```cpp
char *aName( (String)s );
```

和

```cpp
char *aName = String( s );
```

宣告的物件，以及使用者定義類型轉換是清楚這類`String`鍵入`char *`會叫用來執行的初始化`aName`。