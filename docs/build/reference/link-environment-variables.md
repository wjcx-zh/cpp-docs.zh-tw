---
title: LINK 環境變數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076e427e50520651f30cde20c764ff1124a6f953
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372694"
---
# <a name="link-environment-variables"></a>LINK 環境變數

LINK 工具使用下列環境變數：  
  
-   連結和\_連結\_，如果定義。 LINK 工具前面加上 LINK 環境變數中定義的引數選項和附加選項和引數中定義\_連結\_環境變數，以處理前的命令列引數。  
  
-   LIB (若已定義)。 搜尋的物件、 程式庫或在命令列上，或藉由指定其他檔案時，LINK 工具會使用 LIB 路徑[/基底](../../build/reference/base-base-address.md)選項。 它也會使用 LIB 路徑來尋找物件中指定的 .pdb 檔案。 LIB 變數可以包含一或多個以分號分隔的路徑規格。 一個路徑必須指向 Visual C++ 安裝的 \lib 子目錄。  
  
-   PATH，如果該工具必須執行 CVTRES，但在 LINK 本身的相同目錄中找不到檔案。 (LINK 需要 CVTRES 才能連結 .res 檔案。)PATH 必須指向 Visual C++ 安裝的 \bin 子目錄。  
  
-   TMP，在連結 OMF 或 .res 檔案時指定目錄。  
  
## <a name="see-also"></a>另請參閱  

[設定連結器選項](../../build/reference/setting-linker-options.md)   
[連結器選項](../../build/reference/linker-options.md)   
[在命令列上建置 C/C++ 程式碼](../../build/building-on-the-command-line.md)  
[設定命令列建置的路徑及環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
