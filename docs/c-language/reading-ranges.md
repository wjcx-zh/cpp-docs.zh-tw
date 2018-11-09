---
title: 讀取範圍
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: b5c6a6baf43b8786fbd0301e4b89ea856d839606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604098"
---
# <a name="reading-ranges"></a>讀取範圍

**ANSI 4.9.6.2**：解譯虛線 (-) 字元，該字元不是 `fscanf` 函式中 % [ 轉換之 scanlist 中的第一個字元，也不是最後一個字元

下面這行

```
fscanf( fileptr, "%[A-Z]", strptr);
```

會將範圍 A-Z 中任何數目的字元讀取到 `strptr` 所指向的字串中。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)