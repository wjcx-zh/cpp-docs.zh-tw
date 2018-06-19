---
title: 國際化策略 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e4d7b067daedcbc5ce065c096e561dbf932ac1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856592"
---
# <a name="internationalization-strategies"></a>國際化策略
根據您的目標作業系統和市場，您有數個國際化策略：  
  
-   您的應用程式會使用 Unicode。  
  
     使用 Unicode 特有的功能和所有字元都是 16 位元寬 （雖然您可以使用程式的某些部分中的 ANSI 字元的特殊用途）。 C 執行階段程式庫提供僅限 Unicode 程式設計函式、 巨集和資料類型。 MFC 已完全啟用 Unicode。  
  
-   您的應用程式會使用 MBCS，而且可以執行任何 Win32 平台上。  
  
     您使用 MBCS 特有的功能。 字串可以包含單一位元字元，雙位元組字元或兩者。 C 執行階段程式庫提供僅限 MBCS 程式設計函式、 巨集和資料類型。 MFC 會完全啟用 MBCS。  
  
-   您的應用程式的原始程式碼會寫入完整的可攜性，重新編譯使用的符號 **_UNICODE**或符號 **_MBCS**定義，您可以產生使用的版本。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
     您可以使用完全可攜 C 執行階段函式、 巨集和資料類型。 MFC 的彈性支援任何這些策略。  
  
 這些主題的其餘部分著重於撰寫完全可攜式程式碼，您可以建置為 Unicode 或 MBCS。  
  
## <a name="see-also"></a>另請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [地區設定和字碼頁](../text/locales-and-code-pages.md)