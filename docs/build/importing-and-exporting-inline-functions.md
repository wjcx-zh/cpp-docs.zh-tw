---
title: 匯入和匯出內嵌函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431b7c3becffb4e5b2543984fd66cae0a1507738
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726553"
---
# <a name="importing-and-exporting-inline-functions"></a>匯入和匯出內嵌函式

匯入的函式可以定義為內嵌。 這個效果大致相同定義的標準函式內嵌。呼叫函式會展開為內嵌程式碼，如同巨集。 這是來說相當有用，因為一種支援 c + + DLL 中的類別而內嵌某些成員函式的效率。

匯入的內嵌函式的其中一個功能是您可以在 c + + 中取得它的位址。 編譯器會傳回位於 DLL 中內嵌函式副本的地址。 匯入的內嵌函式的另一個功能是，您可以初始化靜態區域資料，匯入的函式，不同於全域匯入資料。

> [!CAUTION]
>  提供匯入內嵌函式，因為它們可能會產生版本衝突時，應特別小心。 內嵌函式可展開成的應用程式程式碼;因此，如果您稍後重新撰寫函式，它不會更新除非重新編譯應用程式本身。 （一般來說，DLL 函式而不需重建使用它們的應用程式會更新。）

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [從 DLL 匯出](../build/exporting-from-a-dll.md)

- [匯出從 DLL 使用。DEF 檔](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](../build/importing-and-exporting.md)