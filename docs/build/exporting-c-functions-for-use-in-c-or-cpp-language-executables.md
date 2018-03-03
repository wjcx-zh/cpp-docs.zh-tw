---
title: "匯出 C 函式以用於 C 或 c + + 語言可執行檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 232cfb3a65dfe3e65eaa2eeef0a4a55e723b7f7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>匯出 C 函式以用於 C 或 C++ 語言可執行檔  
  
如果您在以 C 撰寫，您想要存取從 C 語言或 c + + 語言的模組，您應該使用的 DLL 函式**__cplusplus**前置處理器巨集來判斷哪一種語言編譯，，，然後將這些宣告如果 c + + 語言模組中使用 C 連結函式。 如果您使用這項技術，並提供您的 DLL 的標頭檔，這些函式可供 C 和 c + + 的使用者，且不會變更。  
  
下列程式碼會顯示可供 C 和 c + + 的用戶端應用程式的標頭檔：  
  
```h  
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
  
如果您要連結至 c + + 可執行的 C 函式的函式宣告的標頭檔具有不使用上述的技巧，c + + 原始程式檔中，執行下列命令以防止編譯器裝飾的 C 函式名稱：  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [裝飾的名稱](../build/reference/decorated-names.md)  
  
-   [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>請參閱  
 [從 DLL 匯出](../build/exporting-from-a-dll.md)