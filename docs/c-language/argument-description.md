---
title: 引數描述 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f79f8648c2c0d12bf521c38e2db025a8841ab927
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061080"
---
# <a name="argument-description"></a>引數描述

**main** 與 **wmain** 函式中的 `argc` 參數是整數，負責指定要從命令列傳遞到程式的引數數目。 由於程式名稱會視為引數，因此 `argc` 的值至少會是一。

## <a name="remarks"></a>備註

`argv` 參數是以 null 終止之字串的指標陣列，表示程式引數。 陣列的每個元素都會指向傳遞至 **main** (或 **wmain**) 之引數的字串表示。 (如需陣列的詳細資訊，請參閱[陣列宣告](../c-language/array-declarations.md))。`argv` 參數可以宣告為 `char` 類型的指標陣列 (`char *argv[]`)，或是宣告為 `char` 類型指標的指標 (`char **argv`)。 對於 **wmain**，`argv` 參數可以宣告為 `wchar_t` 類型的指標陣列 (`wchar_t *argv[]`)，或宣告為 `wchar_t` 類型指標的指標 (`wchar_t **argv`)。

依照慣例，`argv`**[0]** 是對程式叫用的命令。  不過，您可以使用 [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) 來繁衍處理序，且如果您同時使用第一個與第二個引數 (`lpApplicationName` 與 `lpCommandLine`)，`argv`**[0]** 可能不是可執行檔名稱，請使用 [GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197) 來擷取可執行檔名稱。

最後一個指標 (`argv[argc]`) 是 **NULL**。 (如需取得環境變數資訊的替代方法，請參閱*執行階段程式庫參考*中的[getenv](../c-runtime-library/reference/getenv-wgetenv.md))。

**Microsoft 專屬**

`envp` 參數是以 null 終止之字串的陣列指標，表示使用者的環境變數中設定的值。 `envp` 參數可以宣告為 `char` 的指標陣列 (`char *envp[]`)，或是宣告為 `char` 指標的指標 (`char **envp`)。 在 **wmain** 函式中， `envp` 參數可以宣告為 `wchar_t` 的指標陣列 (`wchar_t *envp[]`)，或是宣告為 `wchar_t` 指標的指標 (`wchar_t **envp`)。 陣列的結尾會以 **NULL** \* 指標表示。 請注意，傳遞至 **main** 或 **wmain** 的環境區塊是目前環境的「凍結」複本。 如果您後續透過呼叫_**putenv** 或 `_wputenv` 變更環境，則目前環境 (如 `getenv`/`_wgetenv` 與 `_environ` 或 `_wenviron` 變數所傳回) 將會變更，不過 `envp` 所指向的區塊將不會變更。 `envp` 參數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[main 函式和程式執行](../c-language/main-function-and-program-execution.md)