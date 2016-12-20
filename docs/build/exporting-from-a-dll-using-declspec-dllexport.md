---
title: "使用 __declspec(dllexport) 從 DLL 匯出 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dllexport"
  - "__declspec"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllexport) 關鍵字 [C++]"
  - "匯出指示詞 [C++]"
  - "匯出 DLL [C++], __declspec(dllexport) 關鍵字"
  - "名稱 [C++], DLL 匯出依據"
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 __declspec(dllexport) 從 DLL 匯出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 在 Visual C\+\+ 的 16 位元編譯器 \(Compiler\) 版本中引入 **\_\_export**，讓編譯器可自動產生匯出名稱並將他們置於 .lib 檔中。  接著就可以像靜態 .lib 檔一樣，使用這個 .lib 檔連結至 DLL。  
  
 在新版本的編譯器中，您可以使用 **\_\_declspec\(dllexport\)** 關鍵字匯出 DLL 的資料、函式、類別或類別成員函式。  **\_\_declspec\(dllexport\)** 會將匯出指示詞加入至物件檔，這樣您就不需用到 .def 檔。  
  
 這種便利性在嘗試匯出修飾 C\+\+ 函式名稱時最為明顯。  因為名稱裝飾 \(Name Decoration\) 並無標準規格，所以匯出函式的名稱在不同編譯器版本之間可能會有所變更。  如果您使用 **\_\_declspec\(dllexport\)**，則只需要在命名慣例變更時重新編譯 DLL 和相依的 .exe 檔。  
  
 許多匯出指示詞 \(例如，序數、NONAME 和 PRIVATE\) 只能用於 .def 檔，因此指定這些屬性時一定要有 .def 檔。  不過使用 .def 檔之外還使用 **\_\_declspec\(dllexport\)**，並不會造成組建錯誤。  
  
 若要匯出函式，請在指定關鍵字情況下，使 **\_\_declspec\(dllexport\)** 關鍵字務必出現在呼叫慣例關鍵字左邊。  例如：  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 若要匯出所有在類別的公開資料成員和成員函式，關鍵字必須以下列方式出現在類別名稱左邊：  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` 無法套用至使用 `__clrcall` 呼叫慣例的函式。  
  
 在建置 DLL 時，您通常會建立標頭檔 \(Header File\)，包含要匯出之函式的原型和\/或類別，並在標頭檔的宣告中加入 **\_\_declspec\(dllexport\)**。  若要使程式更容易讀取，請為 **\_\_declspec\(dllexport\)** 定義巨集，並在每個輸出的符號使用巨集：  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **\_\_declspec\(dllexport\)** 會將函式名稱儲存在 DLL 的匯出表。  如果您要最佳化表格的大小，請參閱[根據序數而不是名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
> [!NOTE]
>  將 DLL 原始程式碼從 Win16 移植到 Win32 時，請將每個 **\_\_export** 執行個體取代為 **\_\_declspec\(dllexport\)**。  
  
 請搜尋整個 Win32 Winbase.h 標頭檔做為參考。  其中包含了 **\_\_declspec\(dllimport\)** 的用法範例。  
  
## 您想要執行甚麼工作？  
  
-   [使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式以用於 C 或 C\+\+ 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [\_\_declspec 關鍵字](../cpp/declspec.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)