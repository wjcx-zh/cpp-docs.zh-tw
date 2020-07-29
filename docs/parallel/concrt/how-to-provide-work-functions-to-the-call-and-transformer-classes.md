---
title: 如何：為呼叫和轉換程式類別提供工作函式
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: cecb8b2e6ab3f3ac8b010007018b76e6f58e0ed8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205882"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：為呼叫和轉換程式類別提供工作函式

本主題說明將工作函式提供給[concurrency：： call](../../parallel/concrt/reference/call-class.md)和[concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)類別的數種方式。

第一個範例顯示如何將 lambda 運算式傳遞至 `call` 物件。 第二個範例顯示如何將函式物件傳遞至 `call` 物件。 第三個範例顯示如何將類別方法系結至 `call` 物件。

如需說明，本主題中的每個範例都會使用 `call` 類別。 如需使用類別的範例 `transformer` ，請參閱[如何：在資料管線中使用轉換器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

## <a name="example"></a>範例

下列範例顯示使用類別的常見方式 `call` 。 這個範例會將 lambda 函式傳遞給此函式 `call` 。

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

此範例會產生下列輸出。

```Output
13 squared is 169.
```

## <a name="example"></a>範例

下列範例類似上一個範例，不同之處在于它會 `call` 搭配使用類別與函式物件（仿函數）。

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>範例

下列範例類似上一個範例，不同之處在于它會使用[std：： bind1st](../../standard-library/functional-functions.md#bind1st)和[std：： mem_fun](../../standard-library/functional-functions.md#mem_fun)函式，將物件系結 `call` 至類別方法。

如果您必須將 `call` 或物件系結 `transformer` 至特定類別方法，而不是函式呼叫運算子，請使用這項技術 `operator()` 。

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

您也可以將函數的結果指派 `bind1st` 給[std：： function](../../standard-library/function-class.md)物件，或使用 **`auto`** 關鍵字，如下列範例所示。

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `call.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc 呼叫 .cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[如何：在資料管線中使用轉換器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[呼叫類別](../../parallel/concrt/reference/call-class.md)<br/>
[轉換器類別](../../parallel/concrt/reference/transformer-class.md)
