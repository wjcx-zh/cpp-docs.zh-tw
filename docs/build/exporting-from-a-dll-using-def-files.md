---
title: "使用 .DEF 檔從 DLL 匯出 | Microsoft Docs"
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
  - ".def 檔案 [C++], 自 DLL 匯出"
  - "def 檔案 [C++], 自 DLL 匯出"
  - "匯出 DLL [C++], DEF 檔案"
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 .DEF 檔從 DLL 匯出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模組定義 \(.def\) 檔是文字檔，包含一或多個模組陳述式，說明 DLL 的各種屬性 \(Attribute\)。  如果您不是使用 **\_\_declspec\(dllexport\)** 關鍵字來匯出 DLL 的函式，則 DLL 就需要 .def 檔。  
  
 最小的 .def 檔必須包含下列模組定義陳述式：  
  
-   檔案裡的第一個陳述式必須是 LIBRARY 陳述式。  這個陳述式會將 .def 檔識別為屬於某一個 DLL。  LIBRARY 陳述式會接在 DLL 名稱之後。  連結器會將這個名稱置於 DLL 的匯入程式庫。  
  
-   EXPORTS 陳述式會列出由 DLL 匯出的函式名稱，和選擇性的函式序數值。  您可以在函式名稱之後加入 @ 符號和數字，來為函式指派序數值。  您所指定的序數值必須介於範圍 1 到 N 之間，N 是指由 DLL 匯出的函式數目。  如果您是根據序數來匯出函式，請參閱[根據序數而不是名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及這個主題。  
  
 例如，包含可實作二進位搜尋樹狀結構的程式碼之 DLL 看起來可能會像下面這樣：  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 如果您使用 [MFC DLL 精靈](../mfc/reference/mfc-dll-wizard.md)來建立 MFC DLL，則精靈會為您建立基本架構的 .def 檔，並自動將它加入至專案。  將要匯出的函式名稱加入到這個檔案中。  對於非 MFC DLL，您必須自行建立 .def 檔，並且將它加入至專案。  
  
 如果您要在 C\+\+ 檔案裡匯出函式，您必須將裝飾名稱 \(Decorated Name\) 置於 .def 檔，或使用 extern "C"，以標準 C 連結定義匯出的函式。  如果您需要在 .def 檔中放置裝飾名稱，您可以使用 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具或使用連結器的 [\/MAP](../build/reference/map-generate-mapfile.md) 選項取得裝飾名稱。  請注意，由編譯器產生的裝飾名稱是編譯器特定的。  如果您將 Visual C\+\+ 編譯器所產生的裝飾名稱置於 .def 檔，則連結至您的 DLL 的應用程式也必須使用相同版本的 Visual C\+\+ 來建置，這樣在呼叫的應用程式中裝飾名稱才會符合 DLL 的 .def 檔中匯出的名稱。  
  
 如果您正在建置[擴充 DLL](../build/extension-dlls-overview.md)，並且使用 .def 檔來匯出，請將下列程式碼置於包含匯出的類別之標頭檔的開頭和結尾：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 這幾行程式碼可以確保內部要使用或加入到您的類別之 MFC 變數會從您的擴充 DLL 匯出 \(或匯入\)。  例如，使用 `DECLARE_DYNAMIC` 來衍生類別時會展開這個巨集，以便將 `CRuntimeClass` 成員變數加入您的類別。  若是移除這四行程式碼可能會造成 DLL 不正確地編譯或連結，或使用戶端應用程式在連結至 DLL 時發生錯誤。  
  
 建置 DLL 時，連結器會使用 .def 檔建立匯出 \(.exp\) 檔和匯入程式庫 \(.lib\) 檔。  接著連結器會使用匯出檔來建置 DLL 檔。  隱含連結 DLL 的可執行檔會在建置時連結至匯入程式庫。  
  
 請注意，MFC 本身會使用 .def 檔，以便從 MFCx0.dll 匯出函式和類別。  
  
## 您想要執行甚麼工作？  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [.def 檔](../build/reference/module-definition-dot-def-files.md)  
  
-   [模組定義陳述式的規則](../build/reference/rules-for-module-definition-statements.md)  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)