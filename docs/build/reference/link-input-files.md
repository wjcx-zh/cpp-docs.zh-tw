---
title: "連結輸入檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0cae9498d2c9b49e52cf56991d2425de39d7e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="link-input-files"></a>LINK 輸入檔
您可以提供連結器與包含物件、 匯入和標準程式庫、 資源、 模組定義和輸入的命令檔。 連結不使用副檔名來做出假設檔案的內容。 相反地，連結會檢查每個輸入的檔案，以判斷它是何種檔案。  
  
 在命令列上的物件檔中出現在命令列的順序處理。 程式庫按順序搜尋命令列，但請注意下列： 當將結合在目的檔從程式庫中搜尋該文件庫中第一次，然後從命令列和下列的程式庫，無法解析的符號，[/DEFAULTLIB （指定預設程式庫）](../../build/reference/defaultlib-specify-default-library.md)指示詞，然後將命令列的開頭的任何程式庫。  
  
> [!NOTE]
>  連結不再接受分號 （或任何其他字元），做為回應檔案和順序檔案中的註解的開頭。 分號只有辨識為在模組定義檔 (.def) 的註解的開頭。  
  
 連結會使用下列類型的輸入檔：  
  
-   [.obj 檔案](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [.netmodule 檔](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib 檔案](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.exp 檔案](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def 檔案](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb 檔案](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [.res 檔](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [.exe 檔案](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [.txt 檔案](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk 檔案](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)