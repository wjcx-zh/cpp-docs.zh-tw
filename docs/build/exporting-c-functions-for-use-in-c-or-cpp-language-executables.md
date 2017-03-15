---
title: "匯出 C 函式以用於 C 或 C++ 語言可執行檔 | Microsoft Docs"
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
  - "__cplusplus 巨集"
  - "匯出 DLL [C++], C++ 可執行檔中的 C 函式"
  - "匯出函式 [C++], C++ 可執行檔中的 C 函式"
  - "函式 [C], C 或 C++ 可執行檔和"
  - "函式 [C], 匯出"
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 匯出 C 函式以用於 C 或 C++ 語言可執行檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果 DLL 中有使用 C 撰寫且要從 C 語言或 C\+\+ 語言模組存取的函式，則您應該使用 **\_\_cplusplus** 前置處理器巨集，判斷要編譯哪種語言，接著如果要從 C\+\+ 語言模組使用，則用 C 連結來宣告這些函式。  如果您在您的 DLL 使用了這個技術並提供標頭檔，那麼就可以不用變更這些函式來提供 C 和 C\+\+ 使用者。  
  
 下列程式碼顯示了 C 和 C\+\+ 用戶端應用程式可以使用的標頭檔：  
  
```  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 如果您需要將 C 函式連結至 C\+\+ 可執行檔，而且函式宣告標頭檔尚未使用上述技術，請在 C\+\+ 原始程式檔中執行下列程式碼來避免編譯器裝飾 C 函式名稱：  
  
```  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## 您想要執行甚麼工作？  
  
-   [使用 .def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [裝飾名稱](../build/reference/decorated-names.md)  
  
-   [連結規格](http://msdn.microsoft.com/zh-tw/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)  
  
## 請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)