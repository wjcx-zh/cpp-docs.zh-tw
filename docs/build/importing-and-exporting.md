---
title: 匯入和匯出
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220636"
---
# <a name="importing-and-exporting"></a>匯入和匯出

您可以使用兩種方法，將公用符號匯入應用程式或從 DLL 匯出函式：

- 建立 DLL 時，請使用模組定義（.def）檔

- 在主要應用程式的函式定義中，使用關鍵字 **__declspec （dllimport）** 或 **__declspec （dllexport）**

## <a name="using-a-def-file"></a>使用 .def 檔案

模組定義（.def）檔案是一個文字檔，其中包含一或多個描述 DLL 各種屬性的模組語句。 如果您未使用 **__declspec （dllimport）** 或 **__declspec （dllexport）** 來匯出 DLL 的函式，則 DLL 需要 .def 檔案。

您可以使用 .def 檔案匯[入應用程式](importing-using-def-files.md)，或[從 DLL 匯出](exporting-from-a-dll-using-def-files.md)。

## <a name="using-__declspec"></a>使用 __declspec

您不需要使用 **__declspec （dllimport）** 讓您的程式碼正確編譯，但這麼做可讓編譯器產生更好的程式碼。 編譯器能夠產生更好的程式碼，因為它可以判斷函式是否存在於 DLL 中，這可讓編譯器產生程式碼，略過通常會出現在跨越 DLL 界限之函式呼叫中的間接取值層級。 不過，您必須使用 **__declspec （dllimport）** 匯入 DLL 中使用的變數。

使用適當的 .def 檔案匯出區段時，不需要 **__declspec （dllexport）** 。 已新增 **__declspec （dllexport）** 以提供簡單的方法，從 .exe 或 .dll 檔案匯出函式，而不使用 .def 檔案。

Win32 可攜性可執行檔案格式的設計，是要將必須觸及以修正匯入的頁數降至最低。 若要這樣做，它會將任何程式的所有匯入位址放在一個位置，稱為匯入位址資料表。 這可讓載入器在存取這些匯入時，只修改一或兩個頁面。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [從 DLL 匯出](exporting-from-a-dll.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
