---
title: 啟用國際化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f4edcae610f17409c319c7b4bd39dc137e1211e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858698"
---
# <a name="international-enabling"></a>啟用國際化
大部分傳統的 C 和 c + + 程式碼可進行假設字元和字串操作，不適用於國際化應用程式。 MFC 和執行階段程式庫支援 MBCS 或 Unicode，仍會有您必須執行的工作。 若要引導您，本節會說明 Visual c + + 中的 「 國際啟用 」 的意義：  
  
-   Unicode 和 MBCS 會啟用透過 MFC 的函式參數清單中的可移植資料型別和傳回型別。 這些類型有條件地以適當的方式，根據您的組建是否定義符號定義 **_UNICODE**或符號 **_MBCS** （這表示 DBCS）。 不同版本的 MFC 程式庫會自動連結您的應用程式，您的組建定義取決於哪些這兩個符號。  
  
-   類別程式庫程式碼使用可攜式執行階段函式和其他方法，以確保正確 MBCS 或 Unicode 的行為。  
  
-   您仍必須處理特定種類的國際化工作程式碼中：  
  
    -   使用相同的可攜式執行階段函數可讓 MFC 可攜式下其中一個環境。  
  
    -   讓常值字串和字元移植下其中一個環境中，使用 **_T**巨集。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
    -   在 MBCS 下的字串時，請採取預防措施。 在 Unicode，則不需要這些預防措施。 如需詳細資訊，請參閱[MBCS 程式設計提示](../text/mbcs-programming-tips.md)。  
  
    -   請注意，如果您在應用程式中混用 ANSI （8 位元） 和 Unicode （16 位元） 字元。 很可能在使用中程式的某些部分的 ANSI 字元和 Unicode 字元，在其他項目，但您不能混合它們在相同的字串。  
  
    -   不要在您的應用程式的硬式編碼字串。 相反地，讓它們 STRINGTABLE 資源新增到應用程式的.rc 檔。 然後可以當地語系化應用程式而不需要變更程式碼的來源或重新編譯。 如需 STRINGTABLE 資源的詳細資訊，請參閱[字串編輯器](../windows/string-editor.md)。  
  
> [!NOTE]
>  歐洲和 MBCS 字元集具有某些字元，例如字元碼大於 0x80 重音字母。 因為大部分的程式碼使用帶正負號的字元，所以大於 0x80 這些字元都是帶正負號擴充時轉換成`int`。 這是陣列編製索引的問題，因為陣列外部的帶正負號擴充字元，為負數，編製索引。 使用 MBCS，例如日文，日文的語言也是唯一的。 因為字元可能會由 1 或 2 個位元組所組成，您應該一律在相同的時間來管理兩個位元組。  
  
## <a name="see-also"></a>另請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [國際化策略](../text/internationalization-strategies.md)