---
title: 匯入和匯出 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee3ffe33dbb99f1f9b4124e2695d2e56dbe5544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="importing-and-exporting"></a>匯入和匯出
您可以匯入應用程式公用符號，或使用兩種方法從 DLL 匯出函式：  
  
-   建置 DLL 時使用模組定義 (.def) 檔  
  
-   使用關鍵字 **__declspec （dllimport)** 或 **__declspec （dllexport)** 主應用程式中的函式定義中  
  
## <a name="using-a-def-file"></a>使用.def 檔  
 將模組定義 (.def) 檔是文字檔，其中包含描述各種屬性之 DLL 的一個或多個模組陳述式。 如果您未使用 **__declspec （dllimport)** 或 **__declspec （dllexport)** DLL 匯出的 DLL 函式，需要.def 檔。  
  
 您可以使用.def 檔案[匯入應用程式](../build/importing-using-def-files.md)或[從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)。  
  
## <a name="using-declspec"></a>使用 __declspec  
 Visual c + + 使用 **__declspec （dllimport)** 和 **__declspec （dllexport)** 取代 **__export**先前在 16 位元版本的 Visual c + + 中使用的關鍵字。  
  
 您不需要使用 **__declspec （dllimport)** 您的程式碼編譯是否正確，但這樣會讓編譯器將產生更好的程式碼。 編譯器就能夠產生更好的程式碼，因為它可判斷函式中是否存在 DLL，可讓編譯器產生的一般會跨越 DLL 界限的函式呼叫中的間接取值層級會略過的程式碼。 不過，您必須使用 **__declspec （dllimport)** 匯入 DLL 中使用的變數。  
  
 使用適當的.def 檔案 EXPORTS 區段中， **__declspec （dllexport)** 並非必要。 **__declspec （dllexport)** 已加入至提供一個簡單的方式，從.exe 或.dll 檔案匯出函式，而不使用.def 檔。  
  
 Win32 可攜式執行檔格式被為了將必須接觸修正匯入的頁面數目降到最低。 若要這樣做，就會將稱為 「 匯入位址表格的一個位置的任何程式的所有匯入位址。 這可讓要存取這些匯入時修改只需要一個或兩個頁面的載入器。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [匯入應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)