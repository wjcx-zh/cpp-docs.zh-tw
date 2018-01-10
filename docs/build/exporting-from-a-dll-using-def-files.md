---
title: "使用.DEF 檔從 DLL 匯出 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15806c3e40d45588ec27f1351e583fc5e8e897e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 .DEF 檔從 DLL 匯出
將模組定義 (.def) 檔是文字檔，其中包含描述各種屬性之 DLL 的一個或多個模組陳述式。 如果您不使用**__declspec （dllexport)**關鍵字匯出的 DLL 函式，DLL 需要.def 檔。  
  
 最小的.def 檔案必須包含下列模組定義陳述式：  
  
-   檔案中的第一個陳述式必須是文件庫陳述式。 此陳述式會識別為屬於 DLL 的.def 檔案。 程式庫陳述式後面的 DLL 名稱。 連結器會將此名稱的 DLL 匯入程式庫中。  
  
-   匯出陳述式會列出名稱以及選擇性地由 DLL 匯出的函式的值。 您遵循函式的名稱，與指派函式的序數值 at 符號 (@) 和數字。 當您指定的序數值時，它們必須在範圍 1 到 N，其中 N 是由 DLL 匯出的函式數目。 如果您想要依序數匯出函式，請參閱[從根據序數而非依名稱的 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主題。  
  
 例如，包含要實作的二進位搜尋樹狀結構的程式碼的 DLL 會看起來可能如下所示：  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 如果您使用[MFC DLL 精靈](../mfc/reference/mfc-dll-wizard.md)若要建立 MFC DLL，精靈會為您建立基本架構.def 檔和自動將它加入至您的專案。 新增到這個檔案匯出的函式的名稱。 針對非 MFC Dll，您必須自行建立.def 檔，並將它加入至您的專案。  
  
 如果您要匯出的 c + + 檔案中的函式，您必須是.def 檔案中放置裝飾的名稱，或將匯出的函式，C + + 定義使用 extern"C"。 如果您需要在.def 檔中放置裝飾的名稱，您可以取得其使用[DUMPBIN](../build/reference/dumpbin-reference.md)工具或使用連結器[對應](../build/reference/map-generate-mapfile.md)選項。 請注意，由編譯器產生的裝飾的名稱特定編譯器。 如果您將放入.def 檔案中由 Visual c + + 編譯器產生的裝飾的名稱，建立應用程式連結到您的 DLL 必須也使用相同版本的 Visual c + + 呼叫的應用程式中的裝飾的名稱中的 DLL.de 名稱相符f 檔案。  
  
 如果您要建置[擴充 DLL](../build/extension-dlls-overview.md)，然後匯出使用.def 檔，將下列程式碼放在開頭和結尾包含匯出的類別標頭檔：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 這行程式確保 MFC 變數會在內部使用，或加入至您的類別會從您的 MFC 擴充 DLL 匯出 （或匯入）。 例如，若是衍生類別使用`DECLARE_DYNAMIC`，巨集會展開至新增`CRuntimeClass`成員變數加入至類別。 遺漏這些四行可能會導致您編譯或不正確地連結或用戶端應用程式連結至 DLL 時造成錯誤的 DLL。  
  
 當建置 DLL，連結器會使用.def 檔建立的匯出 (.exp) 檔案和匯入程式庫 (.lib) 檔案。 連結器接著會使用來建置的 DLL 檔案的匯出檔案。 如果可執行檔會在建置時，隱含地連結至要匯入程式庫 DLL 連結。  
  
 請注意，MFC 會使用.def 檔，在從 MFCx0.dll 匯出函式和類別。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [.def 檔案](../build/reference/module-definition-dot-def-files.md)  
  
-   [模組定義陳述式的規則](../build/reference/rules-for-module-definition-statements.md)  
  
-   [裝飾的名稱](../build/reference/decorated-names.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)