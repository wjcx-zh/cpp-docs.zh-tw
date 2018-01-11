---
title: "支援 Unicode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 150f161b71efc07bc7b5a08d79e17fac0dea7931
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-unicode"></a>Unicode 的支援
Unicode 是支援所有字元集 (包括僅一個字元無法呈現的字元集) 的規格。 如果您針對國際市場進行程式設計，我們建議您使用 Unicode 或[多位元組字元集](../text/support-for-multibyte-character-sets-mbcss.md)(Mbcs)，或啟用您的程式，因此您可以藉著變更參數建置它。  
  
 寬字元是 2 個位元組的多語系字元碼。 在全球現代計算中使用的大部分字元 (包括技術符號和特殊發行字元)，可以根據 Unicode 規格，呈現為寬字元。 無法僅以一個寬字元呈現的字元可以使用 Unicode Surrogate 功能，以 Unicode 組呈現。 由於每一個寬字元都是以 16 位元固定大小呈現，因此使用寬字元可簡化使用國際字元集的程式設計。  
  
 寬字元字串，表示為**wchar_t []**陣列，並指向`wchar_t*`指標。 任何 ASCII 字元都可以寬字元呈現，方法是在該字元前附加字母 L。 例如，L '\0' 是結束寬 （16 位元） **NULL**字元。 同樣地，任何 ASCII 字串常值都可以寬字元字串常值呈現，方法是在 ASCII 常值前附加字母 L (L"Hello")。  
  
 一般而言，寬字元會比多位元組字元佔用更多的記憶體空間，但處理起來更快。 此外，在多位元組編碼中，一次只能呈現一個地區設定，而世界所有字元集都可由 Unicode 表示形式，同時呈現。  
  
 MFC 架構完全啟用 Unicode，MFC 透過使用可移植巨集，完成啟用 Unicode，如下表所示。  
  
### <a name="portable-data-types-in-mfc"></a>MFC 中的可移植資料型別  
  
|非可移植資料型別|由此巨集取代|  
|-----------------------------|----------------------------|  
|`char`|_**TCHAR**|  
|**char\***， **LPSTR （Win32 資料型別）**|`LPTSTR`|  
|**const char\*，LPCSTR （Win32 資料型別）**|`LPCTSTR`|  
  
 類別`CString`使用**_TCHAR**作為基礎，並提供建構函式和運算子，以便輕鬆轉換。 除了作業的基本單位是 16 位元的字元而非 8 位元的位元組之外，Unicode 的大部分字串作業都可以使用用於處理 Windows ANSI 字元集的相同邏輯，來進行撰寫。 與使用多位元組字元集不同，您無需 (且不應該) 將 Unicode 字元視為兩個不同的位元組。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [安裝 MFC 透過 Unicode 支援](../mfc/unicode-in-mfc.md)  
  
-   [在程式中啟用 Unicode](../text/international-enabling.md)  
  
-   [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 Unicode 來建立國際化的程式](../text/unicode-programming-summary.md)  
  
-   [了解 Unicode，包括如何使用 Unicode 讓我的程式更有效率地在 Windows 2000 上的好處](../text/benefits-of-character-set-portability.md)  
  
-   [使用 wmain，以便可以將寬字元引數傳遞至程式](../text/support-for-using-wmain.md)  
  
-   [請參閱 Unicode 程式設計摘要](../text/unicode-programming-summary.md)  
  
-   [深入了解位元組寬度可移植性的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [wmain 使用的支援](../text/support-for-using-wmain.md)