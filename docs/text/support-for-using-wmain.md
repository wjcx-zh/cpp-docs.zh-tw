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
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491191"
---
# <a name="support-for-using-wmain"></a>wmain 使用的支援

Visual C++支援定義**wmain**函式, 並將寬字元引數傳遞至您的 Unicode 應用程式。 您可以使用類似于 `main`的格式, 將正式參數宣告為 wmain。 然後您可以傳遞寬字元引數以及 (選擇性的) 一個指向程式的寬字元環境指標。 **wmain** 的 `argv` 與 `envp` 參數都是 `wchar_t*` 類型。 例如：

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> MFC Unicode 應用程式`wWinMain`會使用做為進入點。 在此情況下`CWinApp::m_lpCmdLine` , 是 Unicode 字串。 請務必使用`wWinMainCRTStartup` [/ENTRY](../build/reference/entry-entry-point-symbol.md)連結器選項設定。

如果您的程式使用 **main** 函式，則多位元組字元環境就會在程式啟動時由執行階段程式庫建立。 環境的寬字元複本只有在需要時才建立 (例如，藉著呼叫 `_wgetenv` 或 `_wputenv` 函式)。 在第一次呼叫`_wputenv` `_wgetenv`時, 或在第一次呼叫時, 如果 MBCS 環境已經存在, 則會建立對應的寬字元字串環境。 然後, `_wenviron`全域變數會指向該環境, 這是通用變數的寬字元版本`_environ` 。 此時, 環境的兩個複本 (MBCS 和 Unicode) 會同時存在, 並在程式的整個生命週期中由執行時間系統維護。

同樣的，如果您的程式使用 **wmain** 函式，寬字元環境在程式啟動時建立，並且由 `_wenviron` 全域變數指著。 在第一次呼叫`_putenv`或`getenv` `_environ`時, 會建立 MBCS (ASCII) 環境, 並由全域變數指向。

## <a name="see-also"></a>另請參閱

[Unicode 的支援](../text/support-for-unicode.md)<br/>
[Unicode 程式設計摘要](../text/unicode-programming-summary.md)<br/>
[WinMain 函式](/windows/win32/api/winbase/nf-winbase-winmain)
