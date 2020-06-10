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
ms.openlocfilehash: e4fafd12d22f6ff7635380e139f60c110a193d9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622816"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>例外狀況：釋放例外狀況中的物件

本文說明在發生例外狀況時釋放物件的需求和方法。 主題包括：

- [在本機處理例外狀況](#_core_handling_the_exception_locally)

- [終結物件之後擲回例外狀況](#_core_throwing_exceptions_after_destroying_objects)

架構或應用程式擲回的例外狀況會中斷一般程式流程。 因此，請務必仔細追蹤物件，好讓您可以在擲回例外狀況時適當地處置它們。

有兩個主要方法可執行此動作。

- 使用**try**和**catch**關鍵字在本機處理例外狀況，然後使用一個語句終結所有物件。

- 先終結**catch**區塊中的任何物件，然後再將例外狀況擲回區塊外，以進一步處理。

以下說明這兩種方法，做為下列有問題範例的解決方案：

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

如以上所寫，如果擲回例外狀況， `myPerson` 則不會刪除 `SomeFunc` 。 執行會直接跳到下一個外部例外狀況處理常式，略過一般函式 exit 和刪除物件的程式碼。 當例外狀況離開函式時，物件的指標會超出範圍，而且只要程式正在執行，就永遠不會復原物件所佔用的記憶體。 這是記憶體流失;您可以使用記憶體診斷來偵測它。

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>在本機處理例外狀況

**Try/catch**架構提供了一種防禦性程式設計方法，可避免記憶體流失，並確保您的物件在發生例外狀況時遭到終結。 例如，本文稍早所示的範例可以改寫如下：

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

這個新範例會設定例外狀況處理常式來攔截例外狀況，並在本機進行處理。 然後，它會正常結束函式並終結物件。 這個範例的重要層面是，會使用**try/catch**區塊來建立攔截例外狀況的內容。 如果沒有本機例外狀況框架，函式永遠不會知道已擲回例外狀況，而且不會有機會正常結束並終結物件。

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>終結物件之後擲回例外狀況

處理例外狀況的另一種方法是將它們傳遞至下一個外部例外狀況處理內容。 在您的**catch**區塊中，您可以清除本機配置的物件，然後在上擲回例外狀況，以供進一步處理。

擲回的函數不一定需要解除配置堆積物件。 如果函式一律會在正常情況下傳回之前解除配置堆積物件，則函式也應該在擲回例外狀況之前，先取消配置堆積物件。 另一方面，如果函式在正常情況下傳回之前，通常不會解除配置物件，則您必須根據案例，決定是否應將堆積物件解除配置。

下列範例會顯示如何清除本機配置的物件：

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

例外狀況機制會自動解除配置框架物件;框架物件的析構函式也會被呼叫。

如果您呼叫的函式可能會擲回例外狀況，您可以使用**try/catch**區塊來確保攔截例外狀況，並有機會終結已建立的任何物件。 特別要注意的是，許多 MFC 函數可能會擲回例外狀況。

如需詳細資訊，請參閱[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
