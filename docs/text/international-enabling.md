---
title: "啟用國際化 | Microsoft Docs"
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
  - "全球化 [C++], 字元集"
  - "當地語系化 [C++], 字元集"
  - "MBCS [C++], 啟用"
  - "字串 [C++], 啟用國際化"
  - "Unicode [C++], 啟用"
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 啟用國際化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分傳統 C 和 C\+\+ 程式碼會對無法在國際應用程式裡作用得很好的字元和字串操作做假設。  雖然 MFC 和執行階段程式庫都支援 Unicode 或 MBCS，您仍然有一些工作要做。  為了引導您，本章節將會說明 Visual C\+\+ 中「啟用國際化」的意義：  
  
-   Unicode 和 MBCS 都是藉著 MFC 函式參數清單裡可移植的資料型別和傳回型別來啟用。  這些型別有條件的以適當方式定義，根據您的組建是定義 **\_UNICODE** 符號或 **\_MBCS** 符號 \(就是指 DBCS\)。  不同版本的 MFC 程式庫會自動與您的應用程式連結，視您的組建定義這兩個符號的哪一個而定。  
  
-   類別庫 \(Class Library\) 程式碼會使用可移植的執行階段函式和其他方法，確保正確的 Unicode 或 MBCS 行為。  
  
-   您仍然必須在您的程式碼裡處理某些國際化的工作：  
  
    -   使用讓 MFC 在任何環境下都是可移植的相同可移植執行階段函式。  
  
    -   藉著使用 **\_T** 巨集，讓常值 \(Literal\) 字串和字元在任何環境下都可以移植。  如需詳細資訊，請參閱 [TCHAR.H 裡泛用文字的對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
    -   在 MBCS 下解譯字串時，要採取一些措施。  這些措施在 Unicode 底下是不需要的。  如需詳細資訊，請參閱 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)。  
  
    -   如果您在應用程式裡混用 ANSI \(8 位元\) 和 Unicode \(16 位元\) 字元，請小心。  可以在一部分程式裡使用 ANSI 字元並且在其他部分使用 Unicode 字元，但是不能在同一個字串裡混和使用。  
  
    -   不要在應用程式中使用硬式編碼字串。  相反的，藉著將它們加入應用程式的 .rc 檔案，讓它們成為 STRINGTABLE 資源。  然後您的應用程式可以區域化，不需要更改或重新編譯原始程式碼。  如需 STRINGTABLE 資源的詳細資訊，請參閱[字串編輯器](../mfc/string-editor.md)。  
  
> [!NOTE]
>  歐語系和 MBCS 字元集有一些字元的字元碼大於 0x80，例如腔調字母 \(Accented Letter\)。  因為大多數的程式碼使用帶正負號的字元，這些大於 0x80 的字元在轉換成 `int` 時會作正負號延伸。  這對陣列索引會構成問題，因為負數的正負號延伸的字元，會在陣列的外部索引。  使用 MBCS 的語言，例如日文，也都是唯一的。  因為字元可能由 1 個或 2 個字元組所組成，應該一直同時管理兩個位元組。  
  
## 請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [國際化策略](../text/internationalization-strategies.md)