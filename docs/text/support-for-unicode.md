---
title: "Unicode 的支援 | Microsoft Docs"
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
  - "字元集 [C++], Unicode"
  - "全球化 [C++], 字元集"
  - "當地語系化 [C++], 字元集"
  - "可移植資料類型 [MFC]"
  - "Unicode [C++]"
  - "Unicode [C++], 安裝支援"
  - "寬字元 [C++], 關於寬字元"
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Unicode 的支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Unicode 是支援所有字元集 \(包括僅一個字元無法呈現的字元集\) 的規格。  如果您針對國際市場進行程式設計，建議您使用 Unicode 或 [多位元組字元集](../text/support-for-multibyte-character-sets-mbcss.md) \(MBCSs\)，或者啟用您的程式，以便您可以透過變更參數，針對其中任何一種格式，建置您的程式。  
  
 寬字元是 2 個位元組的多語系字元碼。  在全球現代計算中使用的大部分字元 \(包括技術符號和特殊發行字元\)，可以根據 Unicode 規格，呈現為寬字元。  無法僅以一個寬字元呈現的字元可以使用 Unicode Surrogate 功能，以 Unicode 組呈現。  由於每一個寬字元都是以 16 位元固定大小呈現，因此使用寬字元可簡化使用國際字元集的程式設計。  
  
 寬字元字串會以 **wchar\_t\[\]** 陣列呈現，且由 `wchar_t*` 指標指向。  任何 ASCII 字元都可以寬字元呈現，方法是在該字元前附加字母 L。  例如，L'\\0' 是結束寬 \(16 位元\) **NULL** 字元。  同樣地，任何 ASCII 字串常值都可以寬字元字串常值呈現，方法是在 ASCII 常值前附加字母 L \(L"Hello"\)。  
  
 一般而言，寬字元會比多位元組字元佔用更多的記憶體空間，但處理起來更快。  此外，在多位元組編碼中，一次只能呈現一個地區設定，而世界所有字元集都可由 Unicode 表示形式，同時呈現。  
  
 MFC 架構完全啟用 Unicode，MFC 透過使用可移植巨集，完成啟用 Unicode，如下表所示。  
  
### MFC 中的可移植資料型別  
  
|非可移植資料型別|由此巨集取代|  
|--------------|------------|  
|`char`|\_**TCHAR**|  
|**char\***, **LPSTR \(Win32 資料型別\)**|`LPTSTR`|  
|**const char\*, LPCSTR \(Win32 資料型別\)**|`LPCTSTR`|  
  
 類別 `CString` 使用 **\_TCHAR** 作為其基底，並提供建構函式和運算子，以便輕鬆轉換。  除了作業的基本單位是 16 位元的字元而非 8 位元的位元組之外，Unicode 的大部分字串作業都可以使用用於處理 Windows ANSI 字元集的相同邏輯，來進行撰寫。  與使用多位元組字元集不同，您無需 \(且不應該\) 將 Unicode 字元視為兩個不同的位元組。  
  
## 您想要怎麼做？  
  
-   [透過 MFC 安裝 Unicode 支援](../mfc/unicode-in-mfc.md)  
  
-   [在程式中啟用 Unicode](../text/international-enabling.md)  
  
-   [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 Unicode 來建立國際化程式](../text/unicode-programming-summary.md)  
  
-   [了解 Unicode 的好處，包括使用 Unicode 會如何讓程式在 Windows 2000 上更有效率](../text/benefits-of-character-set-portability.md)  
  
-   [使用 wmain，以便可以將寬字元引數傳遞至程式](../text/support-for-using-wmain.md)  
  
-   [請參閱 Unicode 程式設計的摘要](../text/unicode-programming-summary.md)  
  
-   [了解位元組寬度可移植性的一般文字對應](../text/generic-text-mappings-in-tchar-h.md)  
  
## 請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [wmain 使用的支援](../text/support-for-using-wmain.md)