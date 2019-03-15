---
title: 匯出 C 函式以用於 C 或 C++ 語言可執行檔
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812430"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>匯出 C 函式以用於 C 或 C++ 語言可執行檔

如果您想要存取從 C 語言或 c + + 語言的模組，您應該使用以 C 撰寫的 DLL 中有函式 **__cplusplus**前置處理器巨集來判斷哪一種語言正在編譯，，，然後將這些宣告使用 C 連結，如果正在使用中，從 c + + 語言模組的函式。 如果您使用這項技術，並提供您的 DLL 的標頭檔，這些函式可供 C 和 c + + 的使用者，且不會變更。

下列程式碼會顯示可供 C 和 c + + 的用戶端應用程式的標頭檔：

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

如果您需要連結至 c + + 可執行檔的 C 函式，而且函式宣告的標頭檔並未使用上述的技術，在 c + + 原始程式檔中，執行下列命令以防止編譯器裝飾的 C 函式名稱：

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用.def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾的名稱](reference/decorated-names.md)

- [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
