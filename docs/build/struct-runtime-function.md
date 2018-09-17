---
title: 結構 RUNTIME_FUNCTION |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718233"
---
# <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION

以資料表為基礎的例外狀況處理的配置堆疊空間，或呼叫另一個函式 （例如，非分葉函式） 的所有函式需要資料表項目。 函式表項目具有格式：

|||
|-|-|
|ULONG|函式的起始位址|
|ULONG|函式結束位址|
|ULONG|回溯資訊位址|

RUNTIME_FUNCTION 結構必須是在記憶體中的對齊的 DWORD。 所有位址都是相對的映像，也就是它們與包含的函式表項目之映像的起始位址的 32 位元位移。 這些項目會經過排序，並放在 PE32 + 映像的.pdata 區段。 針對動態產生的函式 [JIT 編譯器]，執行階段支援這些函式必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 提供此資訊給作業系統。 若要這樣做會導致不可靠的例外狀況處理和偵錯的處理序。

## <a name="see-also"></a>另請參閱

[回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)