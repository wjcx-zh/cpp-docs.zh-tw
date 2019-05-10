---
title: 使用 .DEF 檔從 DLL 匯出
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 92a140c6491e9e3f0d356509862dee39ebe3fae6
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220778"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 .DEF 檔從 DLL 匯出

模組定義或定義檔 (*.def) 是文字檔案，包含描述的 dll 的各種屬性的一或多個模組陳述式。 如果您不使用 **__declspec （dllexport)** 關鍵字匯出 DLL 的函式，則 DLL 就需要.DEF 檔案。

最小的.DEF 檔必須包含下列模組定義陳述式：

- 在檔案中的第一個陳述式必須是 LIBRARY 陳述式。 此陳述式會識別為屬於某一個 DLL DEF 檔案。 LIBRARY 陳述式後面的 DLL 名稱。 連結器會將這個名稱置於 DLL 的匯入程式庫。

- EXPORTS 陳述式會列出名稱並選擇性地由 DLL 匯出的函式序數值。 您所使用的函式的名稱之後指派函式的序數值 at 符號 (@) 和數字。 當您指定序數的值時，它們必須位於範圍 1 到 N，其中 N 是由 DLL 匯出的函式數目。 如果您想要依序數匯出函式，請參閱[從根據序數而非依名稱的 DLL 匯出函式](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及這個主題。

例如，包含實作二進位搜尋樹狀結構的程式碼的 DLL 會看起來可能如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果您使用[MFC DLL 精靈](../mfc/reference/mfc-dll-wizard.md)若要建立 MFC DLL，精靈會為您建立基本架構的.DEF 檔案並自動將它新增至您的專案。 新增到這個檔案匯出的函式的名稱。 針對非 MFC Dll，自行建立.DEF 檔，並將它新增至您的專案。 然後移至**專案** > **屬性** > **連結器** > **輸入** > **模組定義檔**輸入 DEF 檔案的名稱。 針對每個組態與平台，重複此步驟，或選取全部一次執行**組態 = 所有組態**，並**平台都 = 所有平台**。

如果您要匯出函式中的C++檔案中，您必須在.DEF 檔中放置裝飾的名稱，或使用 extern"C"來定義您匯出的函式，C + +。 如果您需要在.DEF 檔中放置裝飾的名稱，您可以取得其使用[DUMPBIN](../build/reference/dumpbin-reference.md)工具或使用連結器[/typedefs/ 對應](../build/reference/map-generate-mapfile.md)選項。 編譯器所產生的裝飾的名稱是編譯器特定的附註。 如果您將 Microsoft 所產生的裝飾的名稱C++DEF 檔案至編譯器 (MSVC) 連結至您的 DLL 的應用程式必須也使用來建置相同版本的 MSVC，使呼叫的應用程式中的裝飾的名稱符合中匯出的名稱DLL 的.DEF 檔。 

> [!NOTE]
> 使用 Visual Studio 2015 建置的 DLL 可供使用 Visual Studio 2017 或 Visual Studio 2019 建置應用程式。

如果您要建置[延伸模組 DLL](../build/extension-dlls-overview.md)，並匯出使用.DEF 檔案，將下列程式碼的開頭和結尾標頭檔包含匯出的類別：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

這幾行可讓您確保在內部使用，或加入至您的類別，MFC 變數會從您的 MFC 擴充 DLL 匯出 （或匯入）。 例如，若是衍生類別，使用`DECLARE_DYNAMIC`，巨集會展開成新增`CRuntimeClass`成員變數加入您的類別。 離開這四行程式碼可能會導致您的 DLL，若要編譯或連結不正確，或用戶端應用程式連結至 DLL 時，會造成錯誤。

當建置 DLL 時，連結器會使用 DEF 檔，若要建立匯出 (.exp) 檔和匯入程式庫 (.lib) 檔案。 連結器接著會使用來建置的 DLL 檔案的匯出檔案。 如果可執行檔會在建置時，隱含地連結到匯入程式庫的 DLL 連結。

請注意，MFC 本身就會使用.DEF 檔，以便從 MFCx0.dll 匯出函式和類別。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用 __declspec （dllexport） 從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [匯出C++函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式，以用於 C 或C++-語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [.def 檔](reference/module-definition-dot-def-files.md)

- [模組定義陳述式的規則](reference/rules-for-module-definition-statements.md)

- [裝飾的名稱](reference/decorated-names.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
