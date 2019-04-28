---
title: __faststorefence
ms.date: 11/04/2016
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: a0c8027f443a475b03521920e2e036e7ed4eaafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349000"
---
# <a name="faststorefence"></a>__faststorefence

**Microsoft 專屬**

保證每個前一項記憶體參考 (包括載入和儲存記憶體參考) 在任何後續記憶體參考之前都為全域可見。

## <a name="syntax"></a>語法

```
void __faststorefence();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__faststorefence`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

產生完整記憶體屏障指令序列，保證這個內建之前發出的載入和儲存作業，到繼續執行為止都為全域可見。 其效果與所有 x64 平台上的 `_mm_mfence` 內建很類似，但更快。

在 AMD64 平台上，這個常式所產生的指令，是比 `sfence` 指令更快的內存屏障 (Store Fence)。 針對時間關鍵程式碼，請在 AMD64 平台上只使用這個內建，而不是 `_mm_sfence`。 在 Intel x64 平台上，`_mm_sfence` 指令會更快。

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)