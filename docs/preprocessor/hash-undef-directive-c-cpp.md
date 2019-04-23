---
title: '#undef 指示詞 (C /C++)'
ms.date: 11/04/2016
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 4f4f5ce244be6d7f4e13d7a2abc5d21232c08d9d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039003"
---
# <a name="undef-directive-cc"></a>#undef 指示詞 (C/C++)
移除 (取消定義) 先前使用 `#define` 建立的名稱。

## <a name="syntax"></a>語法

```
#undef
identifier
```

## <a name="remarks"></a>備註

**#Undef**指示詞會移除目前的定義*識別項*。 因此，後續發生次數*識別碼*前置處理器會忽略。 若要使用巨集定義中移除 **#undef**，提供巨集*識別項*; 未提供參數清單。

您也可以套用 **#undef**指示詞加入沒有先前定義的識別項。 這樣可確保識別項處於未定義狀態。 巨集取代不會執行內 **#undef**陳述式。

**#Undef**指示詞通常會與配對`#define`指示詞，以建立區域在原始程式中的識別項具有特殊意義。 例如，原始程式的特定函式可以使用資訊清單常數，以定義不會影響程式其他部分的環境特定值。 **#Undef**指示詞也可以搭配`#if`控制原始程式的條件式編譯指示詞。 請參閱[#if、 #elif、 #else 和 #endif 指示詞](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)如需詳細資訊。

在下列範例中， **#undef**指示詞會移除符號常數和巨集的定義。 請注意，其中只會提供巨集的識別項。

```
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft 專屬**

巨集可以是從命令列中使用未定義`/U`選項，後面是未定義的巨集名稱。 發出此命令的效果就相當於一連串`#undef`*巨集名稱*檔案的開頭的陳述式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)