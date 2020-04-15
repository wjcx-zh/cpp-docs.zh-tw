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

導入的函數可以定義為內聯函數。 效果與內聯定義標準函數大致相同;對函數的調用將擴展到內聯代碼中,就像宏一樣。 這主要用作支援 DLL 中 C++類的方法,這些類可能會內聯其某些成員函數的效率。

匯入的內聯函數的一個功能是,您可以在C++中獲取其位址。 編譯器返回駐留在 DLL 中的內聯函數副本的位址。 匯入的內聯函數的另一個功能是,您可以初始化導入函數的靜態本地數據,這與全域導入的數據不同。

> [!CAUTION]
> 在提供導入的內聯函數時,應小心謹慎,因為它們可能會造成版本衝突。 內聯函數將擴展到應用程式代碼中;因此,如果以後重寫函數,則不會更新該函數,除非重新編譯應用程式本身。 (通常,DLL 函數可以更新,而無需重新生成使用它們的應用程式。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [從 DLL 匯出](exporting-from-a-dll.md)

- [使用從 DLL 匯出。DEF 檔案](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(出口)從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用AFX_EXT_CLASS匯出及匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出C++函數,用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [確定要使用的匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](importing-and-exporting.md)
