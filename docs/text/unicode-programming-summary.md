---
title: Unicode 程式設計摘要
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 5095e1c58db3e5c35eb9215367f2fbb064bc228a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504695"
---
# <a name="unicode-programming-summary"></a>Unicode 程式設計摘要

若要利用 Unicode 的 MFC 和 C 執行時間支援，您需要：

- 定義 `_UNICODE` 。

   `_UNICODE`建立程式之前，請先定義符號。

- 指定進入點。

   在專案 [[屬性頁](../build/reference/property-pages-visual-cpp.md)] 對話方塊中，于 [**連結器**] 資料夾的 [ **Advanced** ] 頁面上，將**進入點**符號設定為 `wWinMainCRTStartup` 。

- 使用可移植的執行時間函數和類型。

   使用適當的 C 執行時間函數來處理 Unicode 字串。 您可以使用 `wcs` 一系列的函式，但您可能會想要使用可完全攜的 (啟用國際) `_TCHAR` 宏。 這些宏的開頭都是 `_tcs` ，它們會取代為函式系列的一個 `str` 。 這些函式會在*執行時間程式庫參考*的 [[國際化](../c-runtime-library/internationalization.md)] 區段中詳細說明。 如需詳細資訊，請參閱 [tchar 中的泛型文字](../text/generic-text-mappings-in-tchar-h.md)對應。

   使用 `_TCHAR` 與 [Unicode 支援](../text/support-for-unicode.md)中所述的相關可移植資料類型。

- 正確處理常值字串。

   Visual C++ 的編譯器會將常值字串解釋為下列程式碼：

    ```cpp
    L"this is a literal string"
    ```

   表示 Unicode 字元字串。 您可以使用相同的前置詞做為常值字元。 使用 `_T` 宏以一般方式撰寫常值字串的程式碼，因此它們會以 unicode 或 ANSI 字串的形式編譯為 unicode 字串， (包括不含 Unicode 的 MBCS) 。 例如，不要這樣撰寫：

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   使用：

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   `_UNICODE`若已定義，則 `_T` 會將常值字串轉譯為開頭前置的表單，否則 `_T` 會轉譯沒有 l 前置詞的字串。

    > [!TIP]
    >  `_T`宏與 `_TEXT` 宏相同。

- 請小心將字串長度傳遞給函式。

   某些函式需要字串中的字元數;有些則需要位元組數目。 例如，如果已 `_UNICODE` 定義，則下列對物件的呼叫 `CArchive` 將無法運作 (`str` 是 `CString`) ：

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   在 Unicode 應用程式中，長度會提供您的字元數，但不是正確的位元組數目，因為每個字元都是2個位元組寬。 相反地，您必須使用：

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   ，指定要寫入的正確位元組數目。

   不過，以字元為導向的 MFC 成員函式，而不是位元組導向的工作，不需要額外的編碼：

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` 接受多個字元，而不是位元組數。

- 使用 [fopen_s，_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) 開啟 Unicode 檔案。

總而言之，MFC 與執行時間程式庫提供下列 Unicode 程式設計支援：

- 除了資料庫類別成員函式之外，所有的 MFC 函式都具有 Unicode 功能，包括 `CString` 。 `CString` 也提供 Unicode/ANSI 轉換函數。

- 執行時間程式庫提供所有字串處理函數的 Unicode 版本。  (執行時間程式庫也會提供適用于 Unicode 或 MBCS 的可移植版本。 這些都是 `_tcs` 宏。 ) 

- tchar 提供可移植的資料類型，以及用 `_T` 來轉譯常值字串和字元的宏。 如需詳細資訊，請參閱 [tchar 中的泛型文字](../text/generic-text-mappings-in-tchar-h.md)對應。

- 執行時間程式庫提供寬字元版本的 `main` 。 使用 `wmain` 讓您的應用程式可感知 Unicode。

## <a name="see-also"></a>另請參閱

[Unicode 的支援](../text/support-for-unicode.md)
