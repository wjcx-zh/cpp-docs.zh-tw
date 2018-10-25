---
title: Unicode 程式設計摘要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ac931aca05c9df6d5b201fdafb8872c1ee9c789
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080672"
---
# <a name="unicode-programming-summary"></a>Unicode 程式設計摘要

若要充分利用 Unicode 的 MFC 和 C 執行階段支援，您需要：

- 定義`_UNICODE`。

   定義符號`_UNICODE`之前建置您的程式。

- 指定進入點。

   在上**輸出**頁面**連結器**在專案的資料夾[屬性頁](../ide/property-pages-visual-cpp.md) 對話方塊中，將**進入點**符號`wWinMainCRTStartup`.

- 使用可攜式執行階段函式和類型。

   使用適當的 C 執行階段函式的 Unicode 字串處理。 您可以使用`wcs`系列函式，但您可能會偏好 （國際啟用），完全可攜式`_TCHAR`巨集。 這些巨集都會加上`_tcs`; 它們取代，其中第一，如`str`系列函式。 在將詳細說明這些函式[國際化](../c-runtime-library/internationalization.md)一節*執行階段程式庫參考*。 如需詳細資訊，請參閱 < [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

   使用`_TCHAR`和相關的可移植資料型別中所述[Unicode 支援](../text/support-for-unicode.md)。

- 正確地處理常值字串。

   Visual c + + 編譯器會解譯為自動程式化的常值字串：

    ```cpp
    L"this is a literal string"
    ```

   若要表示的 Unicode 字元字串。 您可以使用相同的前置詞的常值字元。 使用`_T`撰寫程式碼常值字串以一般方式，讓它們編譯成 Unicode 字串，在 Unicode 或 ANSI 字串 （包括 MBCS） 而不需要 Unicode 巨集。 比方說，而不是：

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   使用：

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   具有`_UNICODE`定義，`_T`轉譯在 L 前置詞表單的常值字串，否則為`_T`轉譯沒有 L 前置詞的字串。

    > [!TIP]
    >  `_T`巨集等同於`_TEXT`巨集。

- 請小心傳遞至函式的字串長度。

   有些函式想要字串; 中的字元的數其他人想要位元組的數目。 例如，如果`_UNICODE`定義，則下列呼叫來`CArchive`物件將無法運作 (`str`是`CString`):

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   Unicode 應用程式中，長度會給您的字元數，但不是正確數目的位元組，因為每一個字元是 2 個位元組寬。 相反地，您必須使用：

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   指定要寫入位元組的正確數目。

   不過，MFC 成員函式是字元導向，而不是位元組導向，使用不需要這額外的程式碼：

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` 接受字元，而不是數字中的位元組的數目。

- 使用[fopen_s，_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)開啟 Unicode 檔案。

若要總而言之，MFC 和執行階段程式庫會提供下列支援 Unicode 程式設計：

- 資料庫類別成員函式，除了所有 MFC 函式都都啟用 Unicode，包括`CString`。 `CString` 也提供 Unicode/ANSI 轉換函式。

- 執行階段程式庫提供所有字串處理函式的 Unicode 的版本。 （執行階段程式庫也提供適合的可攜式版本 MBCS 或 Unicode。 這些是`_tcs`巨集。)

- Tchar.h 會提供可移植資料型別和`_T`巨集來轉譯常值字串和字元。 如需詳細資訊，請參閱 < [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

- 執行階段程式庫提供的寬字元版本`main`。 使用`wmain`讓 Unicode 感知應用程式。

## <a name="see-also"></a>另請參閱

[Unicode 的支援](../text/support-for-unicode.md)