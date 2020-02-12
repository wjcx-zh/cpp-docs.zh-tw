---
title: 如何：撰寫 parallel_for 迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5903114a12de46dc06929c83e9995b39d0136810
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141866"
---
# <a name="how-to-write-a-parallel_for-loop"></a>如何：撰寫 parallel_for 迴圈

這個範例示範如何使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)來計算兩個矩陣的乘積。

## <a name="example"></a>範例

下列範例顯示 `matrix_multiply` 函式，此函式會計算兩個方形矩陣的乘積。

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>範例

下列範例顯示 `parallel_matrix_multiply` 函式，此函式會使用 `parallel_for` 演算法平行執行外部迴圈。

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

這個範例只會平行處理外部迴圈，因為它會執行足夠的工作，以受益于平行處理的額外負荷。 如果您平行處理內部迴圈，將不會因為內部迴圈所執行的少量工作，而無法克服並行處理的額外負荷，而無法獲得效能提升。 因此，只平行處理外部迴圈是讓大多數系統上的並行處理好處最大化的最佳方式。

## <a name="example"></a>範例

下列更完整的範例會比較 `matrix_multiply` 函數與 `parallel_matrix_multiply` 函數的效能。

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

下列範例輸出適用於具有四個處理器的電腦。

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯器代碼，請複製該程式碼，然後將它貼入 Visual Studio 專案中，或貼入名為 `parallel-matrix-multiply.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-matrix-multiply.cpp .cpp**

## <a name="see-also"></a>另請參閱

[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)
