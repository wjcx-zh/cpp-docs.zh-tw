---
title: 如何： 在資料管線中的使用轉換程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c39491543c4d3a16202dac3caee50122ba0c7cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403119"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在資料管線中使用轉換程式

本主題包含基本範例，示範如何使用[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)資料管線中的類別。 使用資料管線執行映像處理的更完整範例，請參閱 <<c0> [ 逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

*資料管線*是並行程式設計中常見的模式。 資料管線是由一系列的階段，其中每個階段會執行工作，並接著將該工作的結果傳遞至下一個階段所組成。 `transformer`類別資料中的主要元件管線因為它會接收輸入的值，該值，在執行工作，然後產生的結果，若要使用的另一個元件。

## <a name="example"></a>範例

此範例會使用以下的資料管線中執行一系列轉換指定的初始輸入的值：

1. 第一個階段會計算其輸入的絕對值。

1. 第二個階段計算其輸入的平方根。

1. 第三階段計算其輸入的平方。

1. 詳述階段取消其輸入。

1. 第五個階段會將最終結果寫入至訊息緩衝區。

最後，這個範例會列印到主控台管線的結果。

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

這個範例會產生下列輸出：

```Output
The result is -42.
```

通常會在資料管線，以輸出的值，其輸入值的類型與不同階段。 在此範例中，第二個階段會採用值的型別`int`做為輸入，並產生該值的平方根 ( `double`) 做為輸出。

> [!NOTE]
>  圖是此範例中的資料管線。 因為每個轉換作業會執行一些工作，額外負荷也就是需要執行訊息傳遞可以彌補使用資料管線的優點。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`data-pipeline.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc data-pipeline.cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

