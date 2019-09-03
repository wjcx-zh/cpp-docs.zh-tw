---
title: '#undef 指示詞 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220212"
---
# <a name="undef-directive-cc"></a>#undef 指示詞 (CC++/)

移除 (取消定義) 先前使用 `#define` 建立的名稱。

## <a name="syntax"></a>語法

> **#undef***識別碼*

## <a name="remarks"></a>備註

**#Undef**指示詞會移除目前的*識別碼*定義。 因此, 預處理器會忽略後續出現的*識別碼*。 若要使用 **#undef**移除巨集定義, 請只提供宏*識別碼*, 而不指定參數清單。

您也可以將 **#undef**指示詞套用至沒有先前定義的識別碼。 這樣可確保識別項處於未定義狀態。 宏取代不會在 **#undef**語句內執行。

**#Undef**指示詞通常會與`#define`指示詞配對, 以在來來源程式中建立識別碼有特殊意義的區域。 例如，原始程式的特定函式可以使用資訊清單常數，以定義不會影響程式其他部分的環境特定值。 **#Undef**指示詞也會與`#if`指示詞搭配運作, 以控制來來源程式的條件式編譯。 如需詳細資訊, 請參閱[#if、#elif、#else 和 #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)指示詞。

在下列範例中, **#undef**指示詞會移除符號常數和宏的定義。 請注意，其中只會提供巨集的識別項。

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft 專屬**

您可以從命令列使用`/U`選項來定義宏, 後面接著要定義的宏名稱。 發出此命令的效果相當於檔案開頭的一系列`#undef` *宏名稱*語句。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)
