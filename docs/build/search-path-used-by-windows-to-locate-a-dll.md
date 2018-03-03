---
title: "搜尋 Windows 用來找出 DLL 的路徑。 |Microsoft 文件"
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
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53350ed473226c86dd4fefa93cff376a371dedf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="search-path-used-by-windows-to-locate-a-dll"></a>Windows 用來找出 DLL 的搜尋路徑
隱含和明確連結時，Windows 會先搜尋適用於 「 已知 Dll 」，例如 Kernel32.dll 和 User32.dll。 Windows 會搜尋下列順序中的 Dll:  
  
1.  適用於目前的處理序的可執行模組所在目錄。  
  
2.  目前的目錄。  
  
3.  Windows 系統目錄中。 **GetSystemDirectory**函式會擷取此目錄的路徑。  
  
4.  Windows 目錄。 **GetWindowsDirectory**函式會擷取此目錄的路徑。  
  
5.  在 PATH 環境變數所列的目錄。  
  
    > [!NOTE]
    >  不使用 LIBPATH 環境變數。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [如何以隱含方式連結到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [如何明確地連結到 DLL](../build/linking-an-executable-to-a-dll.md#linking-explicitly)  
  
-   [決定要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)