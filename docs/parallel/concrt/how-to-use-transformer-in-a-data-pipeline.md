---
title: 如何：在資料管線中使用轉換程式
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 4eb490ecf51abea324f20395279bff2d74b7af77
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215851"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在資料管線中使用轉換程式

本主題包含一個基本範例，說明如何在資料管線中使用[concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)類別。 如需使用資料管線執行影像處理的更完整範例，請參閱[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

*資料管道*是並行程式設計的常見模式。 資料管線是由一系列的階段所組成，其中每個階段都會執行工作，然後將該工作的結果傳遞至下一個階段。 `transformer`類別是資料管線中的重要元件，因為它會接收輸入值、執行該值的工作，然後產生另一個要使用之元件的結果。

## <a name="example"></a>範例

這個範例會使用下列資料管線來執行一系列的轉換，並指定初始輸入值：

1. 第一個階段會計算其輸入的絕對值。

1. 第二個階段會計算其輸入的平方根。

1. 第三個階段會計算其輸入的平方。

1. 來回階段會否定其輸入。

1. 第五個階段會將最終結果寫入訊息緩衝區。

最後，此範例會將管線的結果列印到主控台。

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

這個範例會產生下列輸出：

```Output
The result is -42.
```

資料管線中的階段通常會輸出其類型與輸入值不同的值。 在此範例中，第二個階段會採用類型的值 **`int`** 作為其輸入，並產生該值（a）的平方根 **`double`** 做為其輸出。

> [!NOTE]
> 此範例中的資料管線是用來說明。 由於每個轉換作業會執行很少的工作，因此執行訊息傳遞所需的額外負荷可能會超過使用資料管線的優點。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `data-pipeline.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc data-pipeline.cpp .cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
