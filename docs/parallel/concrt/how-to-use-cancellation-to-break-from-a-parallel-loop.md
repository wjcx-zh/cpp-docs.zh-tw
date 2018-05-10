---
title: 如何： 使用取消來中斷平行迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1b5153c225c3bb3a67be4265cf8303da2121c2b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>如何：使用取消來中斷平行迴圈
這個範例將示範如何使用取消來實作基本的平行搜尋演算法。  
  
## <a name="example"></a>範例  

 下列範例會使用取消來搜尋陣列中的項目。 `parallel_find_any`函式使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法和[concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函式來搜尋包含指定的值的位置。 當平行迴圈找到值時，它會呼叫[concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel)方法來取消後續工作。  


  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  

 [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法會並行運作。 因此，它不會執行作業以預先決定的順序。 如果陣列包含多個執行個體，結果可以是值的任何一個其位置。  

  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`parallel-array-search.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 平行陣列 search.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)   
 [cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)
