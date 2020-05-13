---
title: 匯入和匯出內嵌函式
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328508"
---
# <a name="importing-and-exporting-inline-functions"></a>匯入和匯出內嵌函式

匯入的函式可以定義為內嵌。 效果大致上與定義標準函式內嵌相同;函式的呼叫會展開為內嵌程式碼，非常類似于宏。 這主要是用來在 DLL 中支援 c + + 類別的方法，其中可能會內嵌部分成員函式以提高效率。

匯入的內嵌函式的其中一項功能是，您可以在 c + + 中採用其位址。 編譯器會傳回位於 DLL 中內嵌函式複本的位址。 匯入的內嵌函式的另一項功能是，您可以初始化匯入函式的靜態本機資料，不同于全域匯入的資料。

> [!CAUTION]
> 在提供匯入的內嵌函式時，您應該小心，因為它們可能會產生版本衝突的可能性。 內嵌函式會展開為應用程式代碼;因此，如果您稍後重寫函式，除非重新編譯應用程式本身，否則不會更新該函式。 （一般來說，可以更新 DLL 函式，而不需要重建使用它們的應用程式）。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [從 DLL 匯出](exporting-from-a-dll.md)

- [使用從 DLL 匯出。DEF 檔案](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>請參閱

[匯入和匯出](importing-and-exporting.md)
