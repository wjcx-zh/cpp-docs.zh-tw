---
title: 指定要延遲載入的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 986dab0621127c90097808025825930bf9974a7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549860"
---
# <a name="specifying-dlls-to-delay-load"></a>指定要延遲載入的 DLL

您可以指定哪些 Dll 延遲載入[/delayload](../../build/reference/delayload-delay-load-import.md):`dllname`連結器選項。 如果您不打算使用自己的 Helper 函式版本，您也必須連結您的程式與 delayimp.lib (適用於桌面應用程式) 或 dloadhelper.lib (適用於市集應用程式)。

延遲載入 DLL 的簡單範例如下：

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

建置專案的偵錯版本。 使用偵錯工具逐步執行程式碼，您會注意到只有在呼叫 `MessageBox` 時才會載入 user32.dll 。

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)