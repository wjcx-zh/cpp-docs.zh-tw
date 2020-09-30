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
ms.openlocfilehash: 4dcf46e6bdde66a303afc2c4ec94fc8aefdd5e5d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506649"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>匯出 C 函式以用於 C 或 C++ 語言可執行檔

如果您在以 C 撰寫的 DLL 中有您想要從 C 語言或 c + + 語言模組存取的函式，您應該使用 **__cplusplus** 預處理器宏來判斷所要編譯的語言，然後使用 c 連結來宣告這些函式（如果從 c + + 語言模組使用的話）。 如果您使用這項技術並提供 DLL 的標頭檔，C 和 c + + 使用者就可以使用這些函式，而不會有任何變更。

下列程式碼顯示 C 和 c + + 用戶端應用程式可使用的標頭檔：

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

如果您需要將 C 函式連結到 c + + 可執行檔，但函式宣告標頭檔未使用上述技術，請在 c + + 原始程式檔中執行下列動作，以防止編譯器裝飾 C 函式名稱：

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec (dllexport) 從 DLL 匯出 ](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [決定要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾名稱](reference/decorated-names.md)

- [使用 extern 指定連結](../cpp/extern-cpp.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
