---
title: "如何： 撰寫 parallel_for 迴圈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60ae6b7f496f86bde91801e486315587fb693436
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-a-parallelfor-loop"></a>如何：撰寫 parallel_for 迴圈
這個範例示範如何使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)來計算兩個矩陣的乘積。  
  
## <a name="example"></a>範例  
 下列範例所示`matrix_multiply`函式，以計算兩個方矩陣的乘積。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## <a name="example"></a>範例  
 下列範例所示`parallel_matrix_multiply`函式，以使用`parallel_for`演算法以平行方式執行外部迴圈。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 這個範例只是因為它會執行足夠受益於平行處理的額外負荷的工作會平行處理外部迴圈。 如果您平行處理內部迴圈，您將不會收到得到的效能因為少量內部迴圈執行的工作不會不克服平行處理的負荷。 因此，只平行處理外部迴圈是讓大多數系統上的並行處理好處最大化的最佳方式。  
  
## <a name="example"></a>範例  
 下列更完整的範例會比較的效能`matrix_multiply`函式與`parallel_matrix_multiply`函式。  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 下列範例輸出適用於具有四個處理器的電腦。  
  
```Output  
serial: 3853  
parallel: 1311  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將它複製然後將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`parallel-matrix-multiply.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 平行矩陣 multiply.cpp**  
  
## <a name="see-also"></a>請參閱  
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)


