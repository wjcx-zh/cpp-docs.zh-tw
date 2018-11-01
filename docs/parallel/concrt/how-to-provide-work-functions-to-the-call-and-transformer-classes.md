---
title: 如何：為呼叫和轉換程式類別提供工作函式
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: d9d472ddd8d5c7baf3cb16e1df33a2bdb74c5381
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500994"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：為呼叫和轉換程式類別提供工作函式

本主題將說明數種方式可提供工作函式，來[concurrency:: call](../../parallel/concrt/reference/call-class.md)並[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)類別。

第一個範例示範如何將傳遞至 lambda 運算式`call`物件。 第二個範例示範如何將傳遞至函式物件`call`物件。 第三個範例示範如何繫結類別方法，以`call`物件。

舉例來說，本主題中的每個範例會使用`call`類別。 如需使用的範例`transformer`類別，請參閱[如何： 在資料管線中的使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

## <a name="example"></a>範例

下列範例示範一個常見的方式來使用`call`類別。 這個範例會傳遞至 lambda 函式`call`建構函式。

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

此範例會產生下列輸出。

```Output
13 squared is 169.
```

## <a name="example"></a>範例

下列範例類似上一個，不同之處在於它會使用`call`函式物件 (functor) 類別。

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>範例

下列範例類似上一個，不同之處在於它會使用[std::bind1st](../../standard-library/functional-functions.md#bind1st)並[std::mem_fun](../../standard-library/functional-functions.md#mem_fun)繫結的函式`call`類別方法的物件。

如果您有要繫結，請使用這項技術`call`或是`transformer`物件的特定類別方法，而不是函式呼叫運算子`operator()`。

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

您也可以指派的結果`bind1st`函式[std:: function](../../standard-library/function-class.md)物件，或使用`auto`關鍵字，如下列範例所示。

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`call.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc call.cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call 類別](../../parallel/concrt/reference/call-class.md)<br/>
[transformer 類別](../../parallel/concrt/reference/transformer-class.md)
