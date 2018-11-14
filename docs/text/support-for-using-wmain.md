---
title: wmain 使用的支援
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4dabb10bc4e0a53b0ad86f72ef7ddc5a5559cc21
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331915"
---
# <a name="support-for-using-wmain"></a>wmain 使用的支援

Visual c + + 支援定義**wmain**函式，並將寬字元引數傳遞至您的 Unicode 應用程式。 宣告型式參數**wmain**，使用格式類似於`main`。 然後您可以傳遞寬字元引數以及 (選擇性的) 一個指向程式的寬字元環境指標。 **wmain** 的 `argv` 與 `envp` 參數都是 `wchar_t*` 類型。 例如: 

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> MFC Unicode 應用程式使用`wWinMain`做為進入點。 在此情況下，`CWinApp::m_lpCmdLine`是 Unicode 字串。 請務必設定`wWinMainCRTStartup`具有[/ENTRY](../build/reference/entry-entry-point-symbol.md)連結器選項。

如果您的程式使用 **main** 函式，則多位元組字元環境就會在程式啟動時由執行階段程式庫建立。 環境的寬字元複本只有在需要時才建立 (例如，藉著呼叫 `_wgetenv` 或 `_wputenv` 函式)。 在第一次呼叫`_wputenv`，或在第一個呼叫`_wgetenv`如果 MBCS 環境已經存在，會建立對應的寬字元字串環境。 環境則指向`_wenviron`全域變數，也就是寬字元版本的`_environ`全域變數。 到目前為止，兩個複本 （MBCS 和 Unicode） 環境的同時存在，且會由執行階段系統維護程式的生命週期。

同樣的，如果您的程式使用 **wmain** 函式，寬字元環境在程式啟動時建立，並且由 `_wenviron` 全域變數指著。 在第一個呼叫建立 MBCS (ASCII) 環境`_putenv`或是`getenv`和所指的`_environ`全域變數。

## <a name="see-also"></a>另請參閱

[Unicode 的支援](../text/support-for-unicode.md)<br/>
[Unicode 程式設計摘要](../text/unicode-programming-summary.md)<br/>
[WinMain 函式](https://msdn.microsoft.com/library/windows/desktop/ms633559)