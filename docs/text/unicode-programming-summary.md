---
title: "Unicode 程式設計摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode [C++], MFC 與 C 執行階段函式"
  - "Unicode [C++], 程式設計"
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Unicode 程式設計摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用 MFC 和 C 執行階段對 Unicode 的支援，您需要：  
  
-   定義 **\_UNICODE**。  
  
     在建置您的程式之前定義 **\_UNICODE**  符號。  
  
-   指定進入點。  
  
     在專案的[屬性頁](../ide/property-pages-visual-cpp.md)對話方塊中的 \[連結器\] 資料夾的 \[輸出\] 頁面裡，請將 \[進入點\] 符號設定為 **wWinMainCRTStartup**。  
  
-   使用可移植的執行階段函式和型別。  
  
     使用適當的 C 執行階段函式來處理 Unicode 字串。  您可以使用 **wcs** 函式家族，但是可能較喜歡完全可移植的 \(已國際化\) **\_TCHAR** 巨集。  這些巨集是以 **\_tcs** 作字首；它們一對一的取代 **str** 函式家族。  這些函式會在《執行階段程式庫參考》的[國際化](../c-runtime-library/internationalization.md)章節裡有詳細說明。  如需詳細資訊，請參閱 [TCHAR.H 裡泛用文字的對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
     使用 **\_TCHAR** 和 [Unicode 的支援](../text/support-for-unicode.md)裡說明的相關可移植的資料型別。  
  
-   適當的處理常值字串。  
  
     Visual C\+\+ 編譯器將編碼的常值字串解譯為：  
  
    ```  
    L"this is a literal string"  
    ```  
  
     來指 Unicode 字元的字串。  您可以對常值字元使用相同的前置詞。  使用 **\_T** 巨集來對常值字串普遍地編碼，使其可在 Unicode 之下編譯為 Unicode 字串，或為沒有 Unicode 的 ANSI 字串 \(包括 MBCS\)。  例如，不使用：  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     使用：  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     定義 **\_UNICODE** 之後，**\_T** 將常值字串轉譯成以 L 為前置字元的形式，否則，**\_T** 將字串轉譯成沒有 L 前置字元的字串。  
  
    > [!TIP]
    >  **\_T** 巨集與 `_TEXT` 巨集相同。  
  
-   傳遞字串長度到函式時請小心。  
  
     有些函式想要字串裡的字元數目；其他的則要位元組數目。  例如，如果 **\_UNICODE** 有定義，下列對 `CArchive` 物件的呼叫將不會作用 \(`str` 是 `CString`\)：  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     在 Unicode 應用程式裡，長度會給您字元的數目而不是正確的位元組數目，因為每一個字元為 2 個位元組寬。  反而，您必須使用：  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     指定要撰寫的正確位元組數目。  
  
     但是，以字元而非位元組為主的 MFC 成員函式，使用時不需要這行額外的程式碼：  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` 使用幾個字元，而不是幾個位元組。  
  
-   使用 [fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) 開啟 Unicode 檔案。  
  
 簡要說來，MFC 和執行階段程式庫可以為 Windows 2000 下的 Unicode 程式設計提供下列支援：  
  
-   除了資料庫類別成員函式之外，所有的 MFC 函式都支援 Unicode，包括 `CString`。  `CString` 同時也提供 Unicode\/ANSI 型別轉換函式。  
  
-   執行階段程式庫可以提供所有字串處理函式的 Unicode 版本 \(此種執行階段程式庫也提供適合 Unicode 或 MBCS 的可移植版本。  這些是 **\_tcs** 巨集\)。  
  
-   Tchar.h 提供可移植的資料型別和 **\_T** 巨集來轉譯常值字串和字元。  如需詳細資訊，請參閱 [TCHAR.H 裡泛用文字的對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   執行階段程式庫可以提供 **main** 的寬字元版本。  使用 **wmain** 讓您的應用程式具備 Unicode 感知的特性。  
  
## 請參閱  
 [Unicode 的支援](../text/support-for-unicode.md)