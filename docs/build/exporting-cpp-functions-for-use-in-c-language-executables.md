---
title: 匯出 C++ 函式以用於 C 語言可執行檔
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195230"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>匯出 C++ 函式以用於 C 語言可執行檔

如果 DLL 中的函式是以 c + + 撰寫，而您想要從 C 語言模組存取，您應該使用 C 連結來宣告這些函式，而不是 c + + 連結。 除非另有指定，否則 c + + 編譯器會使用 c + + 型別安全命名（也稱為名稱裝飾）和 c + + 呼叫慣例，這可能很容易從 C 呼叫。

若要指定 C 連結， `extern "C"`請針對您的函式宣告指定。 例如：

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出 C 函式以用於 C 或 c + + 語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾名稱](reference/decorated-names.md)

- [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
