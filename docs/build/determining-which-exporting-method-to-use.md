---
title: 決定要使用哪一個匯出方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03c88cee3504d8efef8f9ca19073ed06b66f6aeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="determining-which-exporting-method-to-use"></a>決定要使用哪一個匯出方法
您可以使用兩種方式匯出檔案：.def 檔或 `__declspec(dllexport)` 關鍵字。 為了協助您決定針對您的 DLL 使用哪種方式較好，請考慮下列問題：  
  
-   您打算稍後要匯出多個函式嗎？  
  
-   您的 DLL 只由您可以重建的應用程式所使用，或是由您無法重建的應用程式所使用 (例如，由協力廠商所建立的應用程式)？  
  
## <a name="pros-and-cons-of-using-def-files"></a>使用 .def 檔的優缺點  
 在 .def 檔裡匯出函式，可以讓您控制匯出序數。 當您將匯出函式加入至 DLL 時，可以將較高的序數值 (比其他的匯出函式高) 指派給它們。 當您這樣做時，使用隱含連結的應用程式就不需要重新連結包含新函式的匯入程式庫。 如果您正在設計可供多個應用程式使用的 DLL，這會很方便，因為您可以加入新的功能，也可確保它繼續與已倚賴它的應用程式一起正常運作。 例如，使用 .def 檔建立 MFC DLL。  
  
 使用 .def 檔的另一個優點是您可以使用 `NONAME` 屬性來匯出函式。 這麼做只會將序數放在 DLL 的匯出表中。 對於具有大量匯出函式的 DLL，使用 `NONAME` 屬性可以降低 DLL 檔的大小。 如需如何撰寫的模組定義陳述式的資訊，請參閱[模組定義陳述式的規則](../build/reference/rules-for-module-definition-statements.md)。 序數匯出的相關資訊，請參閱[從根據序數而非依名稱的 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
 使用 .def 檔的缺點是，如果要匯出 C++ 檔案中的函式，則必須在 .def 檔中放置裝飾名稱 (Decorated Name)，或是使用 extern "C" 來定義匯出的函式，避免由 Visual C++ 編譯器進行名稱裝飾。  
  
 如果您.def 檔案中放置裝飾的名稱，您可以取得其使用[DUMPBIN](../build/reference/dumpbin-reference.md)工具或使用連結器[對應](../build/reference/map-generate-mapfile.md)選項。 由編譯起產生的裝飾名稱是編譯器特有的名稱，因此如果您將編譯器產生的裝飾名稱放入 .def 檔案中，連結 DLL 的應用程式必須也是使用相同版本的編譯器建置，以便所呼叫應用程式中的裝飾名稱與 DLL 的 .def 檔案中的輸出名稱相符。  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>使用 __declspec （dllexport） 的優缺點  
 使用 `__declspec(dllexport)` 很方便，因為您不必花費心思在維護 .def 檔和取得匯出函式的裝飾名稱上。 不過，這種匯出方法的用處會受限於您願意重建連結應用程式的數目。 如果您使用新的匯出重建 DLL，您也必須重建應用程式，因為匯出 C++ 函式的裝飾名稱，在您使用不同版本的編譯器重建它時可能會變更。  
  
### <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [匯出從 DLL 使用。DEF 檔案](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
-   [裝飾的名稱](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>另請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)