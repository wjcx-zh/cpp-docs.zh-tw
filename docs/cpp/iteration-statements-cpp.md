---
title: 反覆運算陳述式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: b4176e8265759ae569275bdae5304b0b10c29fc1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227383"
---
# <a name="iteration-statements-c"></a>反覆運算陳述式 (C++)

反覆項目陳述式會使陳述式 (或複合陳述式) 依據某種迴圈終止準則執行零次或多次。 當這些語句是複合陳述式時，它們會依序執行，但當遇到[break](../cpp/break-statement-cpp.md)語句或[continue](../cpp/continue-statement-cpp.md)語句時除外。

C + + 提供四個反復專案語句： [while](../cpp/while-statement-cpp.md)、 [do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)和[範圍架構的](../cpp/range-based-for-statement-cpp.md)。 每一個都會反復執行，直到其終止運算式評估為零（false），或直到迴圈終止是使用語句來強制執行為止 **`break`** 。 下表摘要說明這些陳述式及它們的動作，而且每一個陳述式會在後續章節中詳細討論。

### <a name="iteration-statements"></a>反覆運算陳述式

|引數|評估位置|初始化|[遞增]|
|---------------|------------------|--------------------|---------------|
|**`while`**|迴圈頂端|否|否|
|**`do`**|迴圈底部|否|否|
|**`for`**|迴圈頂端|是|是|
|**範圍架構的 for**|迴圈頂端|是|是|

反覆項目陳述式的陳述式部分不可以是宣告。 不過，它可以是包含宣告的複合陳述式。

## <a name="see-also"></a>另請參閱

[C + + 語句總覽](../cpp/overview-of-cpp-statements.md)
