---
title: "EDITBIN 參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0ff9c0c58498361764dcc1b6c454c9b629d9bed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="editbin-reference"></a>EDITBIN 參考
Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE) 會修改通用物件檔案格式 (COFF) 的二進位檔案。 您可以使用 EDITBIN 來修改物件的檔案、 可執行檔，以及動態連結程式庫 (DLL)。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。  
  
 EDITBIN 不適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。 /GL 與所產生的二進位檔案的任何修改，就必須達到的編譯和連結。  
  
-   [EDITBIN 命令列](../../build/reference/editbin-command-line.md)  
  
-   [EDITBIN 選項](../../build/reference/editbin-options.md)  
  
## <a name="see-also"></a>請參閱  
 [C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)