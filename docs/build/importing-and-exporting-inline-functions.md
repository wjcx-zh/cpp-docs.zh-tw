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
ms.openlocfilehash: ed523d84228124d4a8d99e443c0c744f362f1c56
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822037"
---
# <a name="importing-and-exporting-inline-functions"></a>匯入和匯出內嵌函式

匯入的函式可以定義為內嵌。 這個效果大致相同定義的標準函式內嵌。呼叫函式會展開為內嵌程式碼，如同巨集。 這是來說相當有用，因為一種支援 c + + DLL 中的類別而內嵌某些成員函式的效率。

匯入的內嵌函式的其中一個功能是您可以在 c + + 中取得它的位址。 編譯器會傳回位於 DLL 中內嵌函式副本的地址。 匯入的內嵌函式的另一個功能是，您可以初始化靜態區域資料，匯入的函式，不同於全域匯入資料。

> [!CAUTION]
>  提供匯入內嵌函式，因為它們可能會產生版本衝突時，應特別小心。 內嵌函式可展開成的應用程式程式碼;因此，如果您稍後重新撰寫函式，它不會更新除非重新編譯應用程式本身。 （一般來說，DLL 函式而不需重建使用它們的應用程式會更新。）

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [從 DLL 匯出](exporting-from-a-dll.md)

- [匯出從 DLL 使用。DEF 檔](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式，以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](importing-and-exporting.md)
