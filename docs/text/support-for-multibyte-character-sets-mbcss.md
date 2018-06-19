---
title: 針對多位元組字元集 (Mbcs) 支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b0381b570cbf9e900d44ac075876e63b6be14a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863630"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>多位元組字元集 (MBCS) 的支援
多位元組字元集 (Multibyte Character Set，MBCS) 是支援字元集的舊方法，例如不能以單一位元組表示的日文和中文。 如果您進行新開發，除了使用者看不見的系統字串之外，您應該對所有文字字串使用 Unicode。 MBCS 是舊版技術，不建議用於新開發。  
  
 最常見的 MBCS 實作是雙位元組字元集 (DBCS)。 一般而言，Visual C++ 尤其是 MFC，已完全支援 DBCS。  
  
 如需範例，請參閱 MFC 原始程式碼檔案。  
  
 對於其語言使用大型字元集的市場中使用的平台，Unicode 的最佳替代方案是 MBCS。 MFC 使用可國際語系化的資料類型和 C 執行階段函式來支援 MBCS。 您應該在您的相同程式碼中執行相同動作。  
  
 在 MBCS 下，字元會以 1 或 2 個位元組編碼。 在 2 個位元組的字元中，第一個或前導位元組表示它和下一個位元組會解譯成一個字元。 第一個位元組來自一個範圍的字碼，保留供做為前導位元組使用。 哪個範圍的位元組可以做為前導位元組，取決於使用中的字碼頁。 例如，日文的字碼頁 932 使用範圍 0x81 到 0x9F 來當做前導位元組，但韓文字碼頁 949 使用不同的範圍。  
  
 請在您的 MBCS 程式設計中考慮以下所有項目。  
  
 環境中的 MBCS 字元  
 MBCS 字元可出現在字串中，例如檔案和目錄名稱。  
  
 編輯作業  
 MBCS 應用程式中的編輯作業，應該可對字元而不是位元組運作。 插入號不應分割字元，而向右鍵應該能右移一個字元，依此類推。 **刪除**應該刪除字元;**復原**該重新插入。  
  
 字串處理  
 在使用 MBCS 的應用程式中，字串處理會造成特殊的問題。 在單一字串中會混用這兩種寬度的字元；因此，您必須記得檢查前導位元組。  
  
 執行階段程式庫支援  
 C 執行階段程式庫和 MFC 支援單一位元組、MBCS 和 Unicode 程式設計。 單一位元組字串處理與`str`系列的執行階段函式，MBCS 字串使用對應的處理`_mbs`函式，而 Unicode 字串會使用對應的處理*wcs*函式。 MFC 類別成員函式實作會使用可攜式執行階段，在正確的情況下，其會將函式對應至函式的正常 `str` 系列、MBCS 函式或 Unicode 函式，如「MBCS/Unicode 可攜性」中所述。  
  
 MBCS/Unicode 可攜性  
 使用 Tchar.h 標頭檔，您可以從相同來源建置單一位元組、MBCS 和 Unicode 應用程式。 Tchar.h 會定義巨集前面加上 *_tcs* ，其對應至`str`， `_mbs`，或*wcs*函式，視需要。 若要建立 MBCS，請定義符號 **_MBCS**。 若要建置 Unicode，定義符號 **_UNICODE**。 根據預設， **_MBCS** MFC 應用程式的定義。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
> [!NOTE]
>  如果您同時定義行為是未定義 **_UNICODE**和 **_MBCS**。  
  
 Mbctype.h 和 Mbstring.h 標頭檔會定義 MBCS 特有的函式和巨集，在某些情況下您可能需要。 例如，`_ismbblead` 會告訴您在字串中的特定位元組是否為前導位元組。  
  
 國際可攜性，程式碼將程式與[Unicode](../text/support-for-unicode.md)或多位元組字元集 (Mbcs)。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [在程式中啟用 MBCS](../text/international-enabling.md)  
  
-   [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 MBCS 來建立國際化的程式](../text/mbcs-programming-tips.md)  
  
-   [請參閱 MBCS 程式設計的摘要](../text/mbcs-programming-tips.md)  
  
-   [深入了解位元組寬度可移植性的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>另請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [Visual C++ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)