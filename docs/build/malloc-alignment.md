---
title: malloc 對齊
ms.date: 11/04/2016
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
ms.openlocfilehash: 436033d4e99d42d0a1a9366377f928bc402ac974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533545"
---
# <a name="malloc-alignment"></a>malloc 對齊

[malloc](../c-runtime-library/reference/malloc.md)保證會傳回已適當對齊的儲存具有基本對齊，以及任何物件配置的記憶體無法容納的記憶體。 A*基本對齊*是小於或等於沒有對齊規格的實作所支援的最大對齊的對齊方式。 (在 Visual c + + 中，這是所需的對齊方式`double`，或 8 個位元組。 在以 64 位元平台為目標的程式碼中，則為 16 個位元組)。比方說，四個位元組的配置會在支援任何四個位元組或較小物件的界限上對齊。

Visual c + + 允許具有型別*延伸對齊*，也稱為*過度對齊*型別。 例如，SSE 類型[__m128](../cpp/m128.md)並`__m256`，和使用宣告的型別`__declspec(align( n ))`其中`n`大於 8，擁有延伸對齊。 不保證記憶體對齊在適合需要擴充的對齊之物件的界限上`malloc`。 若要為過度對齊類型配置記憶體，請使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)和相關函式。

## <a name="see-also"></a>另請參閱

[堆疊使用方式](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)