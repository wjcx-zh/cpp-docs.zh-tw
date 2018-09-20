---
title: OpenMP 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389443"
---
# <a name="openmp-directives"></a>OpenMP 指示詞

提供用於 OpenMP API 中的指示詞的連結。

Visual c + + 支援下列的 OpenMP 指示詞：

|指示詞|描述|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|指定的記憶體位置會以不可分割方式更新。|
|[barrier](../../../parallel/openmp/reference/barrier.md)|同步處理的小組中的所有執行緒在屏障的所有執行緒都暫停，直到所有執行緒都執行的屏障為止。|
|[critical](../../../parallel/openmp/reference/critical.md)|指定一次只在一個執行緒上執行的程式碼。|
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定所有執行緒都有相同的檢視，所有的共用物件的記憶體。|
|[for](../../../parallel/openmp/reference/for-openmp.md)|會導致完成的工作分割為個執行緒在平行區域內的迴圈。|
|[master](../../../parallel/openmp/reference/master.md)|指定只有主要 threadshould 執行的程式區段。|
|[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定應執行迴圈，例如循序迴圈平行化該程式碼。|
|[parallel](../../../parallel/openmp/reference/parallel.md)|定義在平行區域，也就是將多個執行緒以平行方式執行的程式碼。|
|[區段](../../../parallel/openmp/reference/sections-openmp.md)|識別要被所有執行緒之間的程式碼區段。|
|[single](../../../parallel/openmp/reference/single.md)|可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定在執行緒私用變數。|

## <a name="see-also"></a>另請參閱

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[子句](../../../parallel/openmp/reference/openmp-clauses.md)