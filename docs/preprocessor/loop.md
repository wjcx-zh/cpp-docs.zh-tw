---
title: loop pragma
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 013540ffe120f42c15538ce86661753b9cf9416f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220856"
---
# <a name="loop-pragma"></a>loop pragma

控制自動平行化工具如何考慮迴圈程式碼, 或排除自動向量化工具所考慮的迴圈。

## <a name="syntax"></a>語法

> **#pragma 迴圈 (hint_parallel (** *n* **))** \
> **#pragma 迴圈 (no_vector)** \
> **#pragma 迴圈 (ivdep)**

### <a name="parameters"></a>參數

**hint_parallel (** *n* **)** \
對編譯器的提示, 此迴圈應該跨*n*個執行緒平行處理, 其中*n*是正整數常值或零。 如果*n*為零, 則會在執行時間使用執行緒的最大數目。 這是編譯器的提示, 而不是命令。 並不保證會平行處理迴圈。 如果迴圈具有資料相依性或結構性問題, 則不會平行處理。 例如, 如果儲存到用於迴圈主體之外的純量, 則不會平行處理。

除非指定了[/Qpar](../build/reference/qpar-auto-parallelizer.md)編譯器參數, 否則編譯器會忽略此選項。

**no_vector**\
根據預設, 自動向量化工具會嘗試向量化其評估的所有迴圈, 以從中獲益。 指定此 pragma 可停用下列迴圈的自動向量化工具。

**ivdep**\
提示, 讓編譯器忽略此迴圈的向量相依性。 將此選項與**hint_parallel**搭配使用。

## <a name="remarks"></a>備註

若要使用**迴圈**pragma, 請將它放在迴圈定義的正後方, 而不是。 pragma 生效範圍為其後方迴圈的範圍。 您可以任何順序對迴圈套用多個 pragma，不過，您必須在個別的 pragma 陳述式中加以說明。

## <a name="see-also"></a>另請參閱

[自動平行處理和自動向量化](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
