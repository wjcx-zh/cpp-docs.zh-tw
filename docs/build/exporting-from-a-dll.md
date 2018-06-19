---
title: 從 DLL 匯出 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07efe3d73b3f78dfb30e85ffad6434e2907c36c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367949"
---
# <a name="exporting-from-a-dll"></a>從 DLL 匯出  
  
DLL 檔案具有相似的.exe 檔，但有一個重要差異配置 — DLL 檔案包含匯出表。 匯出資料表包含每個函式的 DLL 匯出到其他可執行檔的名稱。 這些函式是 DLL; 的進入點只匯出表中的函數可以透過其他可執行檔。 在 DLL 中的任何其他函式是私用的 dll。 可以使用檢視的 dll 匯出表[DUMPBIN](../build/reference/dumpbin-reference.md)工具搭配 /EXPORTS 選項。  
  
 您可以使用兩種方法從 DLL 匯出函式：  
  
-   建立模組定義 (.def) 檔，並建置 DLL 時，使用.def 檔。 如果您想要使用此方法[依序數，而不是依名稱，從您的 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
-   使用關鍵字 **__declspec （dllexport)** 函式的定義中。  
  
 當使用何種方法匯出函式，請務必使用[__stdcall](../cpp/stdcall.md)呼叫慣例。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [依序數，而不是依名稱從 DLL 匯出函式](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [決定要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [匯入應用程式](../build/importing-into-an-application.md)  
  
-   [匯入和匯出內嵌函式](../build/importing-and-exporting-inline-functions.md)  
  
-   [交互匯入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>另請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)