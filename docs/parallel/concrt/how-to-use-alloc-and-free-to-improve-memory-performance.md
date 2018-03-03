---
title: "如何： 使用 Alloc 和 Free 改善記憶體效能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 984e39cbec3016a3baa747cfa382220a04db1bbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 改善記憶體效能

本文件示範如何使用[concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)和[concurrency:: free](reference/concurrency-namespace-functions.md#free)函式來改善記憶體效能。 它會比較所需時間，若要反轉平行陣列的元素的三種不同類型，每一個都會指定`new`和`delete`運算子。  

  
 `Alloc`和`Free`函式是最有用的當多個執行緒經常呼叫兩者`Alloc`和`Free`。 執行階段會保存不同的記憶體快取的每個執行緒。因此，runtime 負責管理記憶體，而不使用鎖定或記憶體屏障。  
  
## <a name="example"></a>範例  
 下列範例示範三種類型，每個指定`new`和`delete`運算子。 `new_delete`類別會使用全域`new`和`delete`運算子`malloc_free`類別會使用 C 執行階段[malloc](../../c-runtime-library/reference/malloc.md)和[可用](../../c-runtime-library/reference/free.md)函式，而`Alloc_Free`類別會使用並行執行階段`Alloc`和`Free`函式。  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## <a name="example"></a>範例  
 下列範例顯示 `swap` 和 `reverse_array` 函式。 `swap`函式交換指定的索引陣列的內容。 它會從暫存變數堆積配置記憶體。 `reverse_array`函式會建立一個大型陣列，並計算反向數次以平行方式，該陣列所需的時間。  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## <a name="example"></a>範例  
 下列範例所示`wmain`函式，以計算所需的時間`reverse_array`上作用的函式`new_delete`， `malloc_free`，和`Alloc_Free`型別，其中每個使用不同的記憶體配置方案。  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## <a name="example"></a>範例  
 完整的範例如下。  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 這個範例會產生下列輸出範例有四個處理器的電腦。  
  
```Output  
Took 2031 ms with new/delete.  
Took 1672 ms with malloc/free.  
Took 656 ms with Alloc/Free.  
```  
  
 在此範例中，型別，會使用`Alloc`和`Free`函式提供最佳的記憶體效能，因為`Alloc`和`Free`函式適用於經常配置和釋放記憶體，從多個區塊執行緒。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`allocators.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc allocators.cpp**  
  
## <a name="see-also"></a>請參閱  
 [記憶體管理函式](../../parallel/concrt/memory-management-functions.md)   
 [Alloc 函式](reference/concurrency-namespace-functions.md#alloc)   
 [Free 函式](reference/concurrency-namespace-functions.md#free)

