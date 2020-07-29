---
title: 引數描述
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: dd973c96c9056f6156976698dfc3695b00ebbbb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200864"
---
# <a name="argument-description"></a>引數描述

**main** 與 **wmain** 函式中的 `argc` 參數是整數，負責指定要從命令列傳遞到程式的引數數目。 由於程式名稱會視為引數，因此 `argc` 的值至少會是一。

## <a name="remarks"></a>備註

`argv` 參數是以 null 終止之字串的指標陣列，表示程式引數。 陣列的每個元素都會指向傳遞至 **main** (或 **wmain**) 之引數的字串表示。 （如需陣列的詳細資訊，請參閱[陣列](../c-language/array-declarations.md)宣告）。`argv`參數可以宣告為類型的指標陣列 **`char`** （），或是宣告為 `char *argv[]` 類型指標的指標 **`char`** （ `char **argv` ）。 針對**wmain**， `argv` 參數可以宣告為類型的指標陣列（），或是宣告為類型指標的 **`wchar_t`** `wchar_t *argv[]` 指標 **`wchar_t`** （ `wchar_t **argv` ）。

依照慣例，`argv`**[0]** 是對程式叫用的命令。  不過，您可以使用[CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)來產生處理常式，而且如果您同時使用第一個和第二個引數（ `lpApplicationName` 和 `lpCommandLine` ）， `argv` **[0]** 可能不是可執行檔名稱，請使用[GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)來抓取可執行檔名稱。

最後一個指標 (`argv[argc]`) 是 **NULL**。 (如需取得環境變數資訊的替代方法，請參閱*執行階段程式庫參考*中的[getenv](../c-runtime-library/reference/getenv-wgetenv.md))。

**Microsoft 特定的**

`envp` 參數是以 null 終止之字串的陣列指標，表示使用者的環境變數中設定的值。 `envp`參數可以宣告為的指標陣列（），或是宣告為指標的 **`char`** `char *envp[]` 指標 **`char`** （ `char **envp` ）。 在**wmain**函式中， `envp` 參數可以宣告為的指標陣列（），或是宣告為指標的 **`wchar_t`** `wchar_t *envp[]` 指標 **`wchar_t`** （ `wchar_t **envp` ）。 陣列的結尾會以 **NULL** \* 指標表示。 請注意，傳遞至 **main** 或 **wmain** 的環境區塊是目前環境的「凍結」複本。 如果您後續透過呼叫 _**putenv**或變更環境 `_wputenv` ，則目前環境（如 `getenv` / `_wgetenv` 和 `_environ` 或變數所傳回 `_wenviron` ）將會變更，但所指向的區塊 `envp` 不會變更。 `envp` 參數在 C 中可與 ANSI 相容，但是在 C++ 中則不相容。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[main 函式和程式執行](../c-language/main-function-and-program-execution.md)
