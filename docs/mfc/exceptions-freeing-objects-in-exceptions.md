---
title: 例外狀況：釋放例外狀況中的物件
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 6e03d46a2600458f3107efa6e0b6b0d643c9b160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442467"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>例外狀況：釋放例外狀況中的物件

這篇文章會說明需要和例外狀況發生時釋放物件的方法。 主題包括：

- [處理在本機的例外狀況](#_core_handling_the_exception_locally)

- [終結物件之後擲回例外狀況](#_core_throwing_exceptions_after_destroying_objects)

由架構或您的應用程式中斷一般程式流程所擲回的例外狀況。 因此，它會保持關閉追蹤的物件，以便萬一發生例外狀況時，您可以正確地在其中處置非常重要。

有兩種主要的方法，若要這樣做。

- 處理在本機使用的例外狀況**嘗試**並**攔截**關鍵字，然後終結使用一個陳述式的所有物件。

- 中的任何物件的終結**攔截**區塊之前擲回的例外狀況，以進一步處理區塊之外。

這兩種方法如下所示為下例有問題的解決方案：

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

如上面，所記載`myPerson`將不會刪除所擲回的例外狀況是如果`SomeFunc`。 執行直接跳到下一個外部例外狀況處理常式，略過在正常的函式結束和刪除物件的程式碼。 物件的指標超出範圍例外狀況會離開函式，並將永遠無法復原物件所佔用的記憶體，只要在程式執行時。 這是記憶體流失;它會偵測到使用記憶體診斷。

##  <a name="_core_handling_the_exception_locally"></a> 處理在本機的例外狀況

**Try/catch**架構提供的防禦性程式設計方法，來避免記憶體流失，並確保發生例外狀況時，會終結物件。 比方說，這篇文章稍早所示的範例可以改寫，如下所示：

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

這個新的範例會設定攔截例外狀況，並在本機處理的例外狀況處理常式。 然後它會正常結束函式，並終結物件。 此範例中很重要的層面是建立來攔截例外狀況內容時，會使用**try/catch**區塊。 沒有本機的例外狀況框架，函式永遠不會知道已擲回例外狀況，並不會有機會正常結束，並終結物件。

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> 終結物件之後擲回例外狀況

若要處理的例外狀況的另一個方法是將它們傳遞到下一個外部例外狀況處理內容。 在您**攔截**區塊中，您可以執行一些清除工作，您在本機配置的物件，並再擲回例外狀況供進一步處理。

擲回的函式可能會或可能不需要解除配置堆積物件。 如果函式一律會取消堆積物件配置在正常的情況下，傳回前，則函式也應該取消的堆積物件配置之前擲回例外狀況。 相反地，如果函式不會無法正常解除配置物件正常的情況下傳回之前，然後您必須決定案例的基礎上是否應該取消配置的堆積物件。

下列範例會示範如何在本機配置的物件可以清除：

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

例外狀況機制會自動取消配置框架物件;也稱為框架物件的解構函式。

如果您呼叫可能會擲回例外狀況的函式時，您可以使用**try/catch**區塊，藉此確定您攔截的例外狀況，並有機會摧毀任何您已建立的物件。 特別是，請注意，許多 MFC 函式可以擲回例外狀況。

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)

