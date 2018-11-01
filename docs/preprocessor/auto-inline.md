---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: a3e49941271ec294ddb69861d12e3451332770fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633336"
---
# <a name="autoinline"></a>auto_inline
排除的範圍中定義的任何函式所在**關閉**指定其視為自動內嵌展開的候選項目。

## <a name="syntax"></a>語法

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>備註

若要使用**auto_inline** pragma，將它放之前和之後 （不在） 函式定義。 pragma 會在顯示該 pragma 後的第一個函式定義生效。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)