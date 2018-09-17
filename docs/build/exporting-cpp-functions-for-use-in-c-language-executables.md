---
title: 匯出 c + + 函式以用於 C 語言可執行檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdc8dc0f853faf0649581d535cb631c232e8276
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709939"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>匯出 C++ 函式以用於 C 語言可執行檔

如果您想要存取從 C 語言的模組，您應該宣告具有 C 連結，而不是 c + + 連結的這些函式，以 c + + 撰寫的 DLL 中有函式。 C + + 命名 （也稱為名稱裝飾） 的型別安全和 c + + 呼叫慣例，很難從 C.呼叫，除非另有指定，會使用 c + + 編譯器

若要指定 C 連結，請指定`extern "C"`函式宣告。 例如: 

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](../build/importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [裝飾的名稱](../build/reference/decorated-names.md)

- [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](../build/exporting-from-a-dll.md)