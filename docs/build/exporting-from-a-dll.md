---
title: 從 DLL 匯出
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: e6a8555561fcf935b3968bd6cb6d19ec42a78563
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224015"
---
# <a name="exporting-from-a-dll"></a>從 DLL 匯出

DLL 檔案的配置與 .exe 檔案非常類似，但有一項重要的差異，也就是 DLL 檔案包含匯出資料表。 匯出資料表包含 DLL 匯出至其他可執行檔的每個函數名稱。 這些函式是 DLL 中的進入點;只有匯出資料表中的函數可以由其他可執行檔存取。 DLL 中的任何其他函數都是 DLL 的私用。 您可以使用[DUMPBIN](reference/dumpbin-reference.md)工具搭配/EXPORTS 選項來查看 DLL 的匯出資料表。

您可以使用兩種方法從 DLL 匯出函式：

- 建立模組定義（.def）檔案，並在建立 DLL 時使用 .def 檔案。 如果您想要[依序數而不是依名稱從 DLL 匯出](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)函式，請使用此方法。

- **`__declspec(dllexport)`** 在函數的定義中使用關鍵字。

使用任一種方法匯出函數時，請務必使用[__stdcall](../cpp/stdcall.md)呼叫慣例。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式以用於 C 或 c + + 語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [依序數而不是名稱從 DLL 匯出函式](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [決定要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [匯入至應用程式](importing-into-an-application.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](importing-and-exporting.md)
