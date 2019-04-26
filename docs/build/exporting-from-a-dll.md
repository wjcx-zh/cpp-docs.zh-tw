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
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196738"
---
# <a name="exporting-from-a-dll"></a>從 DLL 匯出

DLL 檔案具有.exe 檔，但有一個重要的差異非常類似的版面配置-DLL 檔案包含匯出表。 匯出資料表包含每個函式的 DLL 匯出到其他可執行檔的名稱。 這些函式是 DLL; 進入點匯出表中的函數可以存取其他可執行檔。 在 DLL 中的任何其他函式是私用 dll。 可以使用檢視的 dll 匯出表[DUMPBIN](reference/dumpbin-reference.md)工具搭配 /EXPORTS 選項。

您可以使用兩種方法從 DLL 匯出函式：

- 建立模組定義 (.def) 檔並建置 DLL 時，使用.def 檔。 如果您想要使用此方法[從您的 DLL 匯出函式，根據序數而不是名稱](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

- 使用關鍵字 **__declspec （dllexport)** 函式的定義中。

當匯出函式使用任一方法，請務必使用[__stdcall](../cpp/stdcall.md)呼叫慣例。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用.def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [匯出C++函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式，以用於 C 或C++-語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [依序數，而不是依名稱從 DLL 匯出函式](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [匯入應用程式](importing-into-an-application.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](importing-and-exporting.md)
