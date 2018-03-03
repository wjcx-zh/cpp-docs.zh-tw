---
title: "如何： 使用 combinable 結合集合 |Microsoft 文件"
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
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbd36e9536707bc639e8f80cc019b7fda18f793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用可組合的類別結合集合
本主題示範如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別來計算一組質數。  
  
## <a name="example"></a>範例  
 下列範例會計算一組質數兩次。 每個計算儲存中的結果[std::bitset](../../standard-library/bitset-class.md)物件。 此範例先循序計算組，然後再計算以平行方式設定。 這個範例也會將執行這兩項計算所需的時間列印到主控台。  
  
 這個範例會使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法和`combinable`物件來產生執行緒區域集合。 然後它會使用[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)方法，將合併成最終集合執行緒區域集合。  

  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 下列範例輸出適用於具有四個處理器的電腦。  
  
```Output  
serial time: 312 ms  
 
parallel time: 78 ms  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`parallel-combine-primes.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 平行結合 primes.cpp**  
  
## <a name="see-also"></a>請參閱  
 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)   
 [combinable:: combine_each 方法](reference/combinable-class.md#combine_each)


