---
title: "匯入和匯出內嵌函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6f8d159a1537cdfee02d45805632ba9ad4afa7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting-inline-functions"></a>匯入和匯出內嵌函式
匯入的函式可以定義為內嵌。 效果大致上是相同定義的標準函式內嵌。呼叫函式會展開到內嵌程式碼，很像巨集。 一種支援 c + + DLL 中某些其成員函式為了提高效率而內嵌類別，這是來說相當有用。  
  
 匯入的內嵌函式的其中一項功能是您可以在 c + + 中取得它的位址。 編譯器傳回的副本位於 DLL 中內嵌函式的位址。 匯入的內嵌函式的另一個功能是，您可以初始化靜態區域資料，匯入的函式，不同於全域匯入資料。  
  
> [!CAUTION]
>  您應該小心時提供匯入內嵌函式，因為它們可能會產生版本衝突。 內嵌函式展開成應用程式程式碼中。因此，如果您稍後重新撰寫函式，它就不會更新除非重新編譯應用程式本身。 （一般而言，DLL 函式而不需重建使用它們的應用程式會更新。）  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [匯出從 DLL 使用。DEF 檔案](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)