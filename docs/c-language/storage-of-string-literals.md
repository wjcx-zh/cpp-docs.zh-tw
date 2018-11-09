---
title: 字串常值的儲存
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: b6c266c1381cc7f4e505916a916f5a924a626792
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481220"
---
# <a name="storage-of-string-literals"></a>字串常值的儲存

常值字串的字元是依順序儲存在連續記憶體位置中。 字串常值內的逸出序列 (例如 **\\\\** 或 **\\"**) 會算是單一字元。 null 字元 (以 **\0** 逸出序列表示) 會自動附加至每個字串常值，而且做為字串常值結尾的標記。 (這會發生在[轉譯階段](../preprocessor/phases-of-translation.md) 7)。請注意，編譯器可能不會將兩個相同的字串儲存在兩個不同的位址。 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) 會強制編譯器將一份相同的字串放入可執行檔中。

## <a name="remarks"></a>備註

**Microsoft 專屬**

字串具有靜態儲存期。 如需儲存期的詳細資訊，請參閱[儲存類別](../c-language/c-storage-classes.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[C 字串常值](../c-language/c-string-literals.md)