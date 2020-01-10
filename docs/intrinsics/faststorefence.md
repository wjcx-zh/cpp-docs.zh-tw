---
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: d11a20666612fe1bca22f5d46b93e898dae375f6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222186"
---
# <a name="__faststorefence"></a>__faststorefence

**Microsoft 專屬**

保證每個前一項記憶體參考 (包括載入和儲存記憶體參考) 在任何後續記憶體參考之前都為全域可見。

## <a name="syntax"></a>語法

```C
void __faststorefence();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__faststorefence`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

產生完整記憶體屏障指令序列, 可保證在內建之前發出的載入和儲存作業, 在繼續執行之前, 全域可見。 其效果與所有 x64 平台上的 `_mm_mfence` 內建很類似，但更快。

在 AMD64 平台上，這個常式所產生的指令，是比 `sfence` 指令更快的內存屏障 (Store Fence)。 針對時間關鍵程式碼，請在 AMD64 平台上只使用這個內建，而不是 `_mm_sfence`。 在 Intel x64 平台上，`_mm_sfence` 指令會更快。

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
