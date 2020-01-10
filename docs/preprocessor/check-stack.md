---
title: check_stack pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 4c976692ec36cedcb73825ee0cc7093736a3a3dc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216134"
---
# <a name="check_stack-pragma"></a>check_stack pragma

指示編譯器在指定**off** (或 **-** ) 時關閉堆疊探查, 或**在指定 on** (或 **+** ) 時開啟堆疊探查。

## <a name="syntax"></a>語法

> **#pragma check_stack (** [{ **on**  |  **off** }] **)** \
> **#pragma check_stack**{ **+**  |  **-** }

## <a name="remarks"></a>備註

這個 pragma 會在顯示該 pragma 後在定義的第一個函式生效。 堆疊探查不是巨集，也不是產生內嵌的函式。

如果您未提供**check_stack** pragma 的引數, 堆疊檢查會還原成在命令列上指定的行為。 如需詳細資訊，請參閱[編譯器選項](../build/reference/compiler-options.md)。 下表摘要說明`#pragma check_stack`和[/gs](../build/reference/gs-control-stack-checking-calls.md)選項的互動。

### <a name="using-the-check_stack-pragma"></a>使用 check_stack pragma

|語法|使用<br /><br /> /Gs 選項編譯？|動作|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|是|關閉後續函式的堆疊檢查|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|否|開啟後續函式的堆疊檢查|
|`#pragma check_stack(on)`<br /><br /> 或`#pragma check_stack +`|是或否|開啟後續函式的堆疊檢查|
|`#pragma check_stack(off)`<br /><br /> 或`#pragma check_stack -`|是或否|關閉後續函式的堆疊檢查|

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
