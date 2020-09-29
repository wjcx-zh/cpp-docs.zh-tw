---
title: 如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: 06418bc1a331a5c77653087434a5cc621f92e7d7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498553"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>如何：轉換使用削減變數的 OpenMP 迴圈來使用並行執行階段

這個範例示範如何轉換使用[縮減](../openmp/reference/openmp-clauses.md#reduction)子句的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp)迴圈，以使用並行執行階段。

OpenMP `reduction` 子句可讓您指定一或多個執行緒私用變數，這些變數會受限於平列區域結尾的縮減作業。 OpenMP 預先定義一組縮減運算子。 每個縮減變數都必須是純量 (例如、、 **`int`** **`long`** 和 **`float`**) 。 OpenMP 也針對如何在平列區域中使用縮減變數定義了幾項限制。

Parallel 模式程式庫 (PPL) 提供 [concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md) 類別，可提供可重複使用的執行緒區域儲存區，讓您可以執行更精細的計算，然後將這些計算合併為最終結果。 `combinable`類別是一種範本，可在純量和複雜類型上運作。 若要使用 `combinable` 類別，請在平行結構的主體中執行子計算，然後呼叫 [concurrency：：組合：：組合](reference/combinable-class.md#combine) 或 [concurrency：：組合：： combine_each](reference/combinable-class.md#combine_each) 方法來產生最終結果。 `combine`和 `combine_each` 方法各自都採用*組合*函式，以指定如何結合每個元素。 因此，此 `combinable` 類別不會限制為一組固定的縮減運算子。

## <a name="example"></a>範例

此範例會使用 OpenMP 和並行執行階段來計算前35個斐的數量詞的總和。

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

如需類別的詳細資訊 `combinable` ，請參閱 [平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="compiling-the-code"></a>編譯程式碼

請複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `concrt-omp-fibonacci-reduction.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令。

> **cl.exe/EHsc/openmp concrt-omp-fibonacci-reduction .cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)
