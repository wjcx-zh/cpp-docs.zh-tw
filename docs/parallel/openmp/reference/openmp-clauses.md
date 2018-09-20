---
title: OpenMP 子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd0a8f66f9b0d027671629998597955b3aa69e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378322"
---
# <a name="openmp-clauses"></a>OpenMP 子句

提供給子句在 OpenMP API 中使用的連結。

Visual c + + 支援下列 OpenMP 子句：

|子句|描述|
|------------|-----------------|
|[copyin](../../../parallel/openmp/reference/copyin.md)|可讓執行緒存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。|
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|指定一或多個變數，應該在所有執行緒之間共用。|
|[default](../../../parallel/openmp/reference/default-openmp.md)|指定在平行區域不限範圍變數的行為。|
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|指定每個執行緒都應該有自己的執行個體的變數，並以變數的值，應該先初始化變數，因為它存在於之前平行建構。|
|[if](../../../parallel/openmp/reference/if-openmp.md)|指定以平行方式或以序列時，是否執行迴圈。|
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|指定封入內容變數的版本，設定等於私用版本的任何執行緒執行的最後一個反覆項目 （for 迴圈建構） 或最後一節 （#pragma 區段）。|
|[nowait](../../../parallel/openmp/reference/nowait.md)|覆寫隱含指示詞中的屏障。|
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|在執行緒小組設定執行緒的數目。|
|[排序](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|需要平行[for](../../../parallel/openmp/reference/for-openmp.md)陳述式如果[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)指示詞是在迴圈中使用。|
|[private](../../../parallel/openmp/reference/private-openmp.md)|指定每個執行緒都應該有自己的執行個體的變數。|
|[reduction](../../../parallel/openmp/reference/reduction.md)|指定一或多個變數為私用的每個執行緒減少作業在平行區域結尾處的主旨。|
|[schedule](../../../parallel/openmp/reference/schedule.md)|適用於[針對](../../../parallel/openmp/reference/for-openmp.md)指示詞。|
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|指定一或多個變數，應該在所有執行緒之間共用。|

## <a name="see-also"></a>另請參閱

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[指示詞](../../../parallel/openmp/reference/openmp-directives.md)