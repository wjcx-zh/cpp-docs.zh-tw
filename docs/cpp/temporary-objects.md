---
title: 暫存物件
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: 0f4cca7100ff8046123f7b2950c1d557797c70f4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223547"
---
# <a name="temporary-objects"></a>暫存物件

在某些情況下，編譯器必須建立暫存物件。 可能需要建立這些暫存物件的原因如下：

- 若要 **`const`** 使用與所初始化之參考的基礎類型不同之類型的初始化運算式來初始化參考。

- 為了儲存傳回使用者定義類型之函式的傳回值。 只有在您的程式不會將傳回值複製到物件時，才會建立這些暫存物件。 例如：

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   由於傳回值不會複製到另一個物件，因此會建立暫存物件。 建立暫存物件的更常見案例是在評估運算式期間，必須呼叫多載運算子函式時。 這些多載運算子函式傳回的使用者定義類型通常不會複製到另一個物件。

   以 `ComplexResult = Complex1 + Complex2 + Complex3` 運算式為例。 `Complex1 + Complex2` 運算式會加以評估，而且結果會儲存在暫存物件中。 接下來，會評估運算式*暫存* `+ Complex3` ，並將結果複製到 `ComplexResult` （假設指派運算子未多載）。

- 為了將轉型的結果儲存為使用者定義類型。 當特定類型的物件明確轉換成使用者定義類型時，該新物件會建構為暫存物件。

暫存物件具有存留期，該存留期是從物件建立的時間點開始到終結的時間點為止。 任何建立超過一個暫存物件的運算式，最終都會依建立物件的反向順序終結這些物件。 下表顯示發生終結的點。

### <a name="destruction-points-for-temporary-objects"></a>暫存物件的終結點

|建立暫存的原因|終結點|
|------------------------------|-----------------------|
|運算式評估結果|運算式評估結果所建立的所有而暫存物件都會在運算式語句的結尾（也就是分號），或在 **`for`** 、 **`if`** 、、 **`while`** **`do`** 和 **`switch`** 語句的控制運算式結尾處終結。|
|初始化 **`const`** 參考|如果初始設定式不是與所要初始化的參考相同類型的左值，則會建立基礎物件類型的暫存，並且使用初始化運算式進行初始化。 這個暫存物件會在其所繫結的參考物件終結時立即終結。|
