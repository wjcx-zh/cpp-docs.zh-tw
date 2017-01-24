---
title: "決定要使用哪一個匯出方法 | Microsoft Docs"
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
  - "__declspec(dllexport) 關鍵字 [C++]"
  - "def 檔案 [C++], 自 DLL 匯出"
  - "匯出 DLL [C++], 方法比較"
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 決定要使用哪一個匯出方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以以兩種方式匯出檔案─ .def 檔或 `__declspec(dllexport)` 關鍵字。  為了協助您決定哪個方式為您的 DLL 較好，請考慮下列問題：  
  
-   您計畫之後匯出多個函式嗎?  
  
-   您的 DLL 只被您可以重建的應用程式所使用或是被您無法重建的應用程式所使用─例如由協力廠商所建立的應用程式？  
  
## 使用 .def 檔的優缺點  
 在 .def 檔裡匯出函式，可以讓您控制匯出序數。  當您將匯出函式加入至您的 DLL 時，您可以將較高的序數值 \(比其他的匯出函式高\) 指派給它們。  當您這樣做時，使用隱含連結的應用程式就不需要重新連結包含新函式的匯入程式庫。  這是很方便的，如果您設計 DLL 供多個應用程式使用，因為您可以加入新的功能也可確保它繼續正常與已經與它的應用程式一起使用。  例如，使用 .def 檔建立 MFC DLL。  
  
 對使用 .def 檔的另一個優點是您可以使用 `NONAME` 屬性來匯出函式。  這只放序數在 DLL 的匯出表中。  對於具大量匯出函式的 DLL，使用 `NONAME` 屬性可以降低 DLL 檔的大小。  如需如何撰寫模組定義陳述式的詳細資訊，請參閱 [模組定義陳述式的規則](../build/reference/rules-for-module-definition-statements.md)。  如需序數匯出的詳細資訊，請參閱 [根據序數而不是名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
 使用 .def 檔的主要缺點是，如果要匯出 C\+\+ 檔中的函式，則必須在 .def 檔中放置裝飾名稱 \(Decorated Name\)，或是使用 extern "C"，以 C 連結來定義匯出的函式，避免 Visual C\+\+ 編譯器所做的名稱裝飾。  
  
 如果您需要在 .def 檔中放置裝飾名稱，您可以使用 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具或使用連結器的 [\/MAP](../build/reference/map-generate-mapfile.md) 選項取得裝飾名稱。  由編譯起產生的裝飾名稱是編譯器特定的；因此如果您將編譯器產生的裝飾名稱放入 .def 檔案中，連結 DLL 的應用程式必也會使用編譯器的相同版本的，以便呼叫的應用程式中的裝飾名稱與 DLL 的 def 檔案中的輸出名稱符合。  
  
## 使用 \_\_declspec\(dllexport\) 的優缺點  
 使用 `__declspec(dllexport)` 很方便，因為您不必花費心思維護 .def 檔和取得匯出之函式的裝飾名稱。  不過，匯出的這個方法的用處會受限於您願意重建的連結應用程式數目。  如果您使用新的匯出重建 DLL，您也必須重建應用程式，因為匯出 C\+\+ 函式的裝飾名稱，在您使用不同版本的編譯器重建它時可能會變更。  
  
### 您想要執行甚麼工作？  
  
-   [使用 .DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)