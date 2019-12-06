---
title: main：程式啟動
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857433"
---
# <a name="main-program-startup"></a>main：程式啟動

名為**main**的特殊函數是所有 C 和C++程式的開始執行點。 如果您要撰寫遵守 Unicode 程式設計模型的程式碼，您可以使用 `wmain`，這是**主要**的寬字元版本。

編譯器不會預先定義**main**函式。 必須在程式文字中提供這個函式。

**Main**的宣告語法為

```cpp
int main();
```

或者可以選擇

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 專屬**

`wmain` 的宣告語法如下：

```cpp
int wmain( );
```

或者可以選擇

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

您也可以使用在 tchar 中定義的 `_tmain`。 除非已定義 _UNICODE，否則 `_tmain` 會解析為**main** 。 在此情況下，`_tmain` 會解析成 `wmain`。

或者，可以將**main**和 `wmain` 函式宣告為傳回**void** （無傳回值）。 如果您將**main**或 `wmain` 宣告為傳回**void**，則無法使用[return](../cpp/return-statement-in-program-termination-cpp.md)語句將結束代碼傳回至父進程或作業系統。 若要在**main**或 `wmain` 宣告為**void**時傳回結束代碼，您必須使用[exit](../cpp/exit-function.md)函式。

**結束 Microsoft 專屬**

`argc` 和 `argv` 的類型是由語言定義。 `argc`、`argv` 和 `envp` 都是傳統名稱，但編譯器不需使用。 如需詳細資訊和範例，請參閱[引數定義](../cpp/argument-definitions.md)。

## <a name="see-also"></a>請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[使用 wmain 取代 main](../cpp/using-wmain-instead-of-main.md)<br/>
[main 函式限制](../cpp/main-function-restrictions.md)<br/>
[剖析 C++ 命令列引數](../cpp/parsing-cpp-command-line-arguments.md)
