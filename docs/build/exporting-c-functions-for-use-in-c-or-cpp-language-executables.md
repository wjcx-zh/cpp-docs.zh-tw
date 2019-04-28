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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273569"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>匯出 C 函式以用於 C 或 C++ 語言可執行檔

如果您有 DLL 中的函式撰寫在 C 中，您想要從 C 語言存取或C++語言的模組，您應該使用 **__cplusplus**前置處理器巨集來判斷哪一種語言正在編譯，，，然後將這些宣告使用 C 連結函式，如果使用從C++語言的模組。 如果您使用這項技術，並提供您的 DLL 的標頭檔，這些函式可供 C 和C++且不會變更的使用者。

下列程式碼會顯示可供 C 標頭檔和C++用戶端應用程式：

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

如果您需要連結 C 函式，以您C++可執行檔和函式宣告的標頭檔不使用上述的技術，在C++原始程式檔，請執行下列命令以防止編譯器裝飾的 C 函式名稱：

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

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾的名稱](reference/decorated-names.md)

- [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
