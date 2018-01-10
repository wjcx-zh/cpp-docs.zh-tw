---
title: "如何： 為呼叫和轉換程式類別提供工作函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52ab28a015fa0312a5d064401451640c2747e9db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：為呼叫和轉換程式類別提供工作函式
本主題將說明幾種方式可以將工作函式提供給[concurrency:: call](../../parallel/concrt/reference/call-class.md)和[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)類別。  
  
 第一個範例示範如何將 lambda 運算式給`call`物件。 第二個範例示範如何函式物件傳送至`call`物件。 第三個範例示範如何將繫結的類別方法`call`物件。  
  
 舉例來說，本主題中的每個範例會使用`call`類別。 如需範例，會使用`transformer`類別，請參閱[How to： 在資料管線中的使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
## <a name="example"></a>範例  
 下列範例示範一個常見的方式來使用`call`類別。 這個範例會傳遞至 lambda 函式`call`建構函式。  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
13 squared is 169.  
```  
  
## <a name="example"></a>範例  
 下列範例類似，不同之處在於它會使用`call`連同函式物件 （仿函式） 的類別。  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## <a name="example"></a>範例  

 下列範例類似，不同之處在於它會使用[std::bind1st](../../standard-library/functional-functions.md#bind1st)和[std::mem_fun](../../standard-library/functional-functions.md#mem_fun)函式繫結`call`類別方法的物件。  

  
 如果您必須繫結，請使用這項技術`call`或`transformer`物件至特定類別方法，而不是函式呼叫運算子`operator()`。  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 您也可以指派的結果`bind1st`函式以[std:: function](../../standard-library/function-class.md)物件，或使用`auto`關鍵字，如下列範例所示。  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`call.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc call.cpp**  
  
## <a name="see-also"></a>請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [如何： 在資料管線中的使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [呼叫類別](../../parallel/concrt/reference/call-class.md)   
 [transformer 類別](../../parallel/concrt/reference/transformer-class.md)
