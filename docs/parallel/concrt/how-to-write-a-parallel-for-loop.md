---
title: HOW TO：撰寫 parallel_for 迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: d6ac30a5de0ff45adad1064aeab708e6a84f5e9f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283588"
---
# <a name="how-to-write-a-parallelfor-loop"></a>HOW TO：撰寫 parallel_for 迴圈

此範例示範如何使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)來計算兩個矩陣的乘積。

## <a name="example"></a>範例

下列範例所示`matrix_multiply`函式，計算兩個正方形矩陣的乘積。

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>範例

下列範例所示`parallel_matrix_multiply`函式，以使用`parallel_for`演算法以平行方式執行外部迴圈。

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

此範例只是因為它會執行足夠的工作，才會受益於平行處理的負荷會平行處理外部迴圈。 如果您平行處理內部迴圈，您不會收到提升效能因為少量內部迴圈執行的工作不會不克服平行處理的額外負荷。 因此，只平行處理外部迴圈是讓大多數系統上的並行處理好處最大化的最佳方式。

## <a name="example"></a>範例

下列更完整的範例會比較的效能`matrix_multiply`函式與`parallel_matrix_multiply`函式。

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`parallel-matrix-multiply.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行矩陣 multiply.cpp**

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)
