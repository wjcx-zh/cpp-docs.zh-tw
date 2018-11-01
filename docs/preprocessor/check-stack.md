---
title: check_stack
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 93ded20bde98cc4e7b0fc15fd8332195d38f2543
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451983"
---
# <a name="checkstack"></a>check_stack
指示編譯器關閉堆疊探查，如果`off`(或`-`) 指定，或若要關閉堆疊探查，如果`on`(或`+`) 指定。

## <a name="syntax"></a>語法

```
#pragma check_stack([ {on | off}] )
#pragma check_stack{+ | -}
```

## <a name="remarks"></a>備註

如果未指定引數，根據預設值處理堆疊探查。 這個 pragma 會在顯示該 pragma 後在定義的第一個函式生效。 堆疊探查不是巨集，也不是產生內嵌的函式。

如果您未指定的引數**check_stack** pragma，堆疊檢查還原成命令列上指定的行為。 如需詳細資訊，請參閱 <<c0> [ 編譯器參考](../build/reference/compiler-options.md)。 之間的互動`#pragma check_stack`而[/Gs](../build/reference/gs-control-stack-checking-calls.md)下表摘要說明選項。

### <a name="using-the-checkstack-pragma"></a>使用 check_stack pragma

|語法|使用<br /><br /> /Gs 選項編譯？|動作|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|是|關閉後續函式的堆疊檢查|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|否|開啟後續函式的堆疊檢查|
|`#pragma check_stack(on)`<br /><br /> 或 `#pragma check_stack +`|是或否|開啟後續函式的堆疊檢查|
|`#pragma check_stack(off)`<br /><br /> 或 `#pragma check_stack -`|是或否|關閉後續函式的堆疊檢查|

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)