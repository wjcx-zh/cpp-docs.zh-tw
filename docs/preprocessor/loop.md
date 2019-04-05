---
title: 迴圈
ms.date: 10/18/2018
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: a1640881d98073381a941478f4b78177a95698d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023162"
---
# <a name="loop"></a>迴圈

控制 auto-parallelizer 考量迴圈程式碼的方式，及/或從 auto-vectorizer 排除迴圈的考量。

## <a name="syntax"></a>語法

```
#pragma loop( hint_parallel(n) )
#pragma loop( no_vector )
#pragma loop( ivdep )
```

### <a name="parameters"></a>參數

*hint_parallel(n)*<br/>
此迴圈應平行處理跨編譯器的提示*n*執行緒，其中*n*正整數常值或零。 如果*n*為零，在執行階段使用的執行緒數目上限。 這是提供給編譯器的提示，而不是一個命令，因此，並不保證迴圈會進行平行處理。 如果迴圈具有資料相依性或結構問題 (例如，在迴圈主體之外使用純量的迴圈存放區)，則不會對迴圈進行平行處理。

編譯器會忽略此選項，除非[/Qpar](../build/reference/qpar-auto-parallelizer.md)編譯器參數指定。

*no_vector*<br/>
預設會開啟 auto-vectorizer 並嘗試向量化其評估為可從中受益的所有迴圈。 指定這個 pragma 可針對後方的迴圈停用 auto-vectorizer。

*ivdep*<br/>
編譯器的提示，忽略此迴圈的向量相依性。 搭配使用這*hint_parallel*。

## <a name="remarks"></a>備註

若要使用**迴圈**pragma，將它放到前立即 — 不在 — 迴圈定義。 pragma 生效範圍為其後方迴圈的範圍。 您可以任何順序對迴圈套用多個 pragma，不過，您必須在個別的 pragma 陳述式中加以說明。

## <a name="see-also"></a>另請參閱

[自動平行處理和自訂向量化](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)