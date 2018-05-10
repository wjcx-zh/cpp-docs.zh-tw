---
title: Unicode 程式設計摘要 |Microsoft 文件
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a378d46c517dfc0fbb5857ad54bc31f4c34287b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="unicode-programming-summary"></a>Unicode 程式設計摘要
若要充分利用 Unicode 的 MFC 與 C 執行階段支援，您需要：  
  
-   定義 **_UNICODE**。  
  
     定義符號 **_UNICODE**之前建置您的程式。  
  
-   指定進入點。  
  
     在**輸出**連結器資料夾在專案中的頁[屬性頁](../ide/property-pages-visual-cpp.md)對話方塊方塊中，將進入點符號設定**wWinMainCRTStartup**。  
  
-   使用可攜式執行階段函式和類型。  
  
     使用適當的 C 執行階段函式的 Unicode 字串處理。 您可以使用**wcs**系列的函式，但您可能會偏好 （國際啟用） 完全可攜式 **_TCHAR**巨集。 這些巨集所有前面會加上 **_tcs**; 它們取代，其中一個、 為**str**系列的函式。 這些函式中有詳細說明[國際化](../c-runtime-library/internationalization.md)區段*執行階段程式庫參考*。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
     使用 **_TCHAR**和相關的可移植資料類型中所述[支援 Unicode](../text/support-for-unicode.md)。  
  
-   正確處理常值字串。  
  
     Visual c + + 編譯器會解譯常值字串編碼為：  
  
    ```  
    L"this is a literal string"  
    ```  
  
     若要表示為 Unicode 字元字串。 您可以使用相同的前置詞的常值字元。 使用 **_T**編寫程式碼常值字串以一般方式，讓它們編譯成 Unicode 底下的 Unicode 字串，或為 ANSI 字串 （包括 MBCS） 沒有 Unicode 巨集。 例如，而不是：  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     使用：  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     與 **_UNICODE**定義， **_T**轉譯常值字串以 L 前置詞的表單，否則 **_T**轉譯沒有 L 前置詞的字串。  
  
    > [!TIP]
    >  **_T**巨集等同於`_TEXT`巨集。  
  
-   請小心傳遞至函式的字串長度。  
  
     某些函式想要字串; 字串中的字元的數其他需要位元組的數目。 例如，如果 **_UNICODE**定義，則下列呼叫`CArchive`物件將無法運作 (`str`是`CString`):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     在 Unicode 應用程式中，長度會給您的字元數，但不是正確數目的位元組，因為每一個字元是 2 個位元組寬。 相反地，您必須使用：  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     指定要寫入位元組的數目正確。  
  
     不過，MFC 成員函式是以字元而非位元組導向，使用未執行此額外的程式碼：  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` 接受字元，而不是數字中的位元組的數目。  
  
-   使用[fopen_s、 _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)若要開啟 Unicode 檔案。  
  
 若要總而言之，MFC 和執行階段程式庫會提供下列支援 Unicode 程式設計：  
  
-   資料庫類別成員函式，除了所有 MFC 函式都都啟用 Unicode，包括`CString`。 `CString` 也提供 Unicode/ANSI 轉換函式。  
  
-   執行階段程式庫提供所有字串處理函式的 Unicode 的版本。 （執行階段程式庫也提供適合的可攜式版本 MBCS 或 Unicode。 這些是 **_tcs**巨集。)  
  
-   Tchar.h 會提供可移植資料型別和 **_T**巨集來轉譯常值字串和字元。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   執行階段程式庫提供的寬字元版本的**主要**。 使用**wmain**讓 Unicode 感知應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [Unicode 的支援](../text/support-for-unicode.md)