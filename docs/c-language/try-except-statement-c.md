---
title: try-except 陳述式 (C)
description: Microsoft C/c + + 會使用 try-except 語句語言延伸模組，來實行 (SEH) 的結構化例外狀況處理。
ms.date: 08/24/2020
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: e327150431fef3384f2b98940939444b2e6d96ea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898724"
---
# <a name="try-except-statement-c"></a>try-except 陳述式 (C)

**Microsoft 特定**

`try-except`語句是 C 語言的 Microsoft 擴充功能，可讓應用程式在通常會終止執行的事件發生時，控制程式。 這類事件稱為例外狀況，而處理例外狀況的機制稱為結構化例外狀況處理。

例外狀況可能是以硬體或軟體為基礎。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理還是可以記錄和顯示錯誤資訊。 將應用程式的內部狀態設為可協助診斷問題很有用。 尤其是很容易重現的間歇性問題。

## <a name="syntax"></a>語法

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

子句後面的複合陳述式 **`__try`** 是 *受保護的區段*。 子句後面的複合陳述式 **`__except`** 是例外狀況 *處理常式*。 如果在執行受保護區段期間引發例外狀況，則處理常式會指定要採取的一組動作。 執行程序如下所示：

1. 執行保護的區段。

1. 如果在執行受保護區段期間未發生任何例外狀況，則會在子句之後的語句繼續執行 **`__except`** 。

1. 如果在執行受保護區段期間發生例外狀況，或在受保護區段呼叫的任何常式中發生例外狀況，則會 **`__except`** 評估運算式。 傳回的值會決定例外狀況的處理方式。 有三個可能的值：

   - `EXCEPTION_CONTINUE_SEARCH`：無法辨認例外狀況。 繼續搜尋堆疊中的處理常式，先針對包含 `try-except` 語句，然後針對具有下一個最高優先順序的處理常式。

   - `EXCEPTION_CONTINUE_EXECUTION`：例外狀況已辨識但已關閉。 在例外狀況發生的位置繼續執行。

   - `EXCEPTION_EXECUTE_HANDLER` 辨識例外狀況。 藉由執行複合陳述式來將控制權傳送至例外狀況處理常式 **`__except`** ，然後在發生例外狀況時繼續執行。

因為 **`__except`** 運算式會評估為 C 運算式，所以只能是單一值、條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。

> [!NOTE]
> 結構化例外狀況處理可搭配 C 和 C++ 原始程式檔使用。 但是，它不是專為 c + + 所設計。 針對可移植的 c + + 程式，應該使用 c + + 例外狀況處理，而非結構化例外狀況處理。 此外，C++ 例外狀況處理機制更有彈性，因為它可以處理任何類型的例外狀況。 如需詳細資訊，請參閱*c + + 語言參考*中的[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

應用程式中的每個常式都可以有其本身的例外狀況處理常式。 **`__except`** 運算式會在主體範圍中執行 **`__try`** 。 它可以存取任何宣告的本機變數。

**`__leave`** 關鍵字在語句區塊內是有效的 `try-except` 。 的作用 **`__leave`** 是跳至 `try-except` 區塊結尾。 會在例外狀況處理常式結束之後繼續執行。 雖然 **`goto`** 語句可以用來完成相同的結果，但是 **`goto`** 語句會導致堆疊回溯。 **`__leave`** 語句會更有效率，因為它不包含堆疊回溯。

`try-except`使用 `longjmp` 執行時間函式結束語句會被視為異常終止。 跳到陳述並不合法 **`__try`** ，但要跳到其中一項是合法的。 如果進程在執行語句的過程中終止，則不會呼叫例外狀況處理常式 `try-except` 。

## <a name="example"></a>範例

以下是例外狀況處理常式和終止處理常式的範例。 如需終止處理常式的詳細資訊，請參閱[ `try-finally` (C) 的語句](../c-language/try-finally-statement-c.md)。

```C
.
.
.
puts("hello");
__try {
   puts("in try");
   __try {
      puts("in try");
      RAISE_AN_EXCEPTION();
   } __finally {
      puts("in finally");
   }
} __except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ) {
   puts("in except");
}
puts("world");
```

以下是範例的輸出，並在右側新增評論：

```Output
hello
in try              /* fall into try                        */
in try              /* fall into nested try                 */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**結束 Microsoft 專用**

## <a name="see-also"></a>請參閱

[`try-except` (c + +) 的語句 ](../cpp/try-except-statement.md)
