---
title: 使用 .DEF 檔從 DLL 匯出
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078527"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 .DEF 檔從 DLL 匯出

模組定義或 DEF 檔案（* .def）是一個文字檔，其中包含一或多個描述 DLL 各種屬性的模組語句。 如果您未使用 **__declspec （dllexport）** 關鍵字來匯出 DLL 的函式，則 DLL 需要 DEF 檔案。

最小的 DEF 檔案必須包含下列模組定義語句：

- 檔案中的第一個語句必須是 LIBRARY 語句。 這個語句會將 DEF 檔案識別為屬於 DLL。 LIBRARY 語句後面接著 DLL 的名稱。 連結器會將此名稱置於 DLL 的匯入程式庫中。

- 匯出語句會列出 DLL 所匯出之函式的名稱和（選擇性）序數值。 您可以在函式的名稱後面加上 @ 符號和數位，以將序數值指派給函數。 當您指定序數值時，它們必須在1到 N 的範圍內，其中 N 是 DLL 匯出的函式數目。 如果您想要依序數匯出函式，請參閱[依序數而不是依名稱](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)和本主題匯出函式。

例如，包含用來執行二進位搜尋樹狀結構之程式碼的 DLL 可能如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果您使用[MFC Dll Wizard](../mfc/reference/mfc-dll-wizard.md)來建立 mfc dll，則 Wizard 會為您建立基本架構 DEF 檔案，並自動將其新增至您的專案。 新增要匯出至此檔案的函式名稱。 若是非 MFC Dll，請自行建立 DEF 檔案，並將它新增至您的專案。 然後移至 **專案** > **屬性** > **連結器** > **輸入** > **模組定義**檔，然後輸入 DEF 檔案的名稱。 針對每個設定和平臺重複此步驟，或選取 [設定] = [**所有**設定] 和 [**平臺 = 所有平臺**]，一次執行所有動作。

如果您要匯出檔案中C++的函式，您必須將裝飾名稱放在 DEF 檔案中，或使用 Extern "C" 以標準 C 連結定義匯出的函式。 如果您需要將裝飾名稱放在 DEF 檔案中，您可以使用[DUMPBIN](../build/reference/dumpbin-reference.md)工具或使用連結器[/MAP](../build/reference/map-generate-mapfile.md)選項來取得它們。 請注意，編譯器所產生的裝飾名稱是編譯器特有的。 如果您將 Microsoft C++編譯器（MSVC）所產生的裝飾名稱放入 DEF 檔案中，則連結至 DLL 的應用程式也必須使用相同的 MSVC 版本來建立，如此一來，呼叫應用程式中的裝飾名稱就會符合 DLL DEF 檔案中的匯出名稱。

> [!NOTE]
> 以 Visual Studio 2015 建立的 DLL 可供以 Visual Studio 2017 或 Visual Studio 2019 建立的應用程式使用。

如果您要建立[擴充功能 DLL](../build/extension-dlls-overview.md)，並使用 DEF 檔案匯出，請將下列程式碼放在標頭檔的開頭和結尾，其中包含已匯出的類別：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

這些行會確保內部使用的 MFC 變數或新增至類別的 MFC 變數，會從您的 MFC 延伸模組 DLL 匯出（或匯入）。 例如，使用 `DECLARE_DYNAMIC`衍生類別時，宏會展開以將 `CRuntimeClass` 成員變數新增至您的類別。 省略這四行，可能會導致您的 DLL 編譯或連結錯誤，或在用戶端應用程式連結至 DLL 時發生錯誤。

建立 DLL 時，連結器會使用 DEF 檔案來建立匯出（.exp）檔案和匯入程式庫（.lib）檔案。 連結器接著會使用匯出檔案來建立 DLL 檔案。 建立時，會隱含連結至 DLL 連結的可執行檔。

請注意，MFC 本身會使用 DEF 檔案，從 MFCx0 匯出函式和類別。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出C++函數以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式以用於 C 或C++語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [.def 檔案](reference/module-definition-dot-def-files.md)

- [模組定義語句的規則](reference/rules-for-module-definition-statements.md)

- [裝飾名稱](reference/decorated-names.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
