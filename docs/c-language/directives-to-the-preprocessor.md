---
title: 前置處理器的指示詞
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234136"
---
# <a name="directives-to-the-preprocessor"></a>前置處理器的指示詞

「指示詞」會指示 C 前置處理器在編譯之前，於程式文字上執行特定動作。 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)已在《前置處理器參考》** 中完整說明。 這個範例會使用前置處理器指示詞 `#define`：

```
#define MAX 100
```

這個陳述式會指示編譯器在編譯前，將出現 `MAX` 的每一個位置取代為 `100`。 C 編譯器前置處理器指示詞包括：

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>請參閱

[原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)
