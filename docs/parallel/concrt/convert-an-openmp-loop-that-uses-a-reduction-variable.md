---
title: HOW TO：轉換使用削減變數來使用並行執行階段的 OpenMP 迴圈
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: d75e115bdb1d13c9e8f45ed67d0f3993eac1b387
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257315"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>HOW TO：轉換使用削減變數來使用並行執行階段的 OpenMP 迴圈

此範例示範如何將轉換 OpenMP[平行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[如](../../parallel/openmp/reference/for-openmp.md)使用迴圈[減少](../../parallel/openmp/reference/reduction.md)子句來使用並行執行階段。

OpenMP`reduction`子句可讓您指定一或多個執行緒私用變數進行減少作業在平行區域結尾處。 OpenMP 會預先定義一組縮減的運算子。 每個削減變數必須是純量 (例如`int`， `long`，和`float`)。 OpenMP 也會定義削減變數在平行區域中的使用方式的幾項限制。

平行模式程式庫 (PPL) 提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，可提供可讓您執行細部運算，然後將這些運算合併成最終的可重複使用的執行緒本機儲存體結果。 `combinable`類別是純量和複雜類型所做的範本。 若要使用`combinable`類別，執行子計算的平行建構內，然後呼叫[concurrency::combinable::combine](reference/combinable-class.md#combine)或是[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)方法，以產生最終的結果。 `combine`並`combine_each`每個方法會採用*結合函式*，指定如何結合每對元素。 因此，`combinable`類別不會套用至一組固定的削減運算子。

## <a name="example"></a>範例

此範例會使用 OpenMP 與並行執行階段計算前 35 費式數列數字的總和。

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

此範例會產生下列輸出。

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

如需詳細資訊`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`concrt-omp-fibonacci-reduction.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc /openmp concrt-omp-fibonacci-reduction.cpp**

## <a name="see-also"></a>另請參閱

[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)
