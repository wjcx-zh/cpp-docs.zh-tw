---
title: "編譯器選項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler
- IPF Visual C++ compiler
- Itanium Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 490814f85199450d4261bf4071184b75b5ea10c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-options"></a>編譯器選項
cl.exe 是工具，可控制 Microsoft C 和 c + + 編譯器和連結器。 cl.exe 可以只在支援 Microsoft Visual Studio 的作業系統上執行。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。  
  
 編譯器會產生通用物件檔案格式 (COFF) 物件檔 (.obj)。 連結器會產生可執行檔 (.exe) 或動態連結程式庫 (Dll)。  
  
 請注意，所有的編譯器選項是區分大小寫。  
  
 若要編譯而不連結，請使用[/c](../../build/reference/c-compile-without-linking.md)。  
  
## <a name="finding-an-option"></a>尋找選項  
 若要尋找特定的編譯器選項，請參閱下列的清單：  
  
-   [依字母順序排列的編譯器選項](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)  
  
## <a name="specifying-options"></a>指定選項  
 每個編譯器選項的主題討論如何在開發環境中設定。 如需指定在開發環境以外的選項資訊，請參閱：  
  
-   [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)  
  
-   [CL 命令檔](../../build/reference/cl-command-files.md)  
  
-   [CL 環境變數](../../build/reference/cl-environment-variables.md)  
  
## <a name="related-build-tools"></a>相關的建置工具  
 使用[NMAKE](../../build/nmake-reference.md)建置輸出檔。  
  
 使用[BSCMAKE](../../build/reference/bscmake-reference.md)支援 類別瀏覽。  
  
 [連結器選項](../../build/reference/linker-options.md)也會影響您的程式的建置方式。  
  
## <a name="see-also"></a>另請參閱  
 [C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [快速編譯](../../build/reference/fast-compilation.md)   
 [CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)