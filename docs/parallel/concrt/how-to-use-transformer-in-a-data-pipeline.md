---
title: 如何： 在資料管線中的使用轉換程式 |Microsoft 文件
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
ms.openlocfilehash: a291b5c53338137ae59d9361ee36b6df29df277e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>如何：在資料管線中使用轉換程式
本主題包含基本範例，示範如何使用[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)在資料管線中的類別。 如需更完整的範例執行映像處理時，用以在資料管線，請參閱[逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 *資料管線*是在並行程式設計的一般模式。 在資料管線包含一連串的階段，其中每個階段執行工作，然後將該工作的結果傳遞給下一個階段。 `transformer`類別資料的重要元件管線，因為它會接收輸入的值，該值，在執行工作，然後產生的結果，若要使用的另一個元件。  
  
## <a name="example"></a>範例  
 這個範例會使用下列資料管線中的執行一系列指定的初始輸入的值的轉換：  
  
1.  第一個階段計算其輸入的絕對值。  
  
2.  第二個階段計算其輸入的平方根。  
  
3.  第三個階段計算其輸入的平方。  
  
4.  制定階段變換正負號的輸入。  
  
5.  第五個階段會將最終結果寫入至訊息緩衝區。  
  
 最後，這個範例會列印到主控台管線的結果。  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
The result is -42.  
```  
  
 通常會針對輸出型別不同於其輸入值的值在資料管線中的階段。 在此範例中，第二個階段會型別的值`int`做為輸入，並產生該值的平方根 ( `double`) 做為輸出。  
  
> [!NOTE]
>  資料管線，在此範例是為了說明。 因為每個轉換作業會執行一些工作，額外負荷也就是所需執行訊息傳遞可能會超過使用在資料管線的優點。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`data-pipeline.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc data-pipeline.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

