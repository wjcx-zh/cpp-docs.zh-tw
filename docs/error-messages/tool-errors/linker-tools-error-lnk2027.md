---
title: 連結器工具錯誤 LNK2027 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156310a0d21651b9fd2ee6002ace419db4996681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2027"></a>連結器工具錯誤 LNK2027
無法解析的模組參考 ' module'  
  
 傳遞至連結器的檔案具有相依性都指定在模組上 **/ASSEMBLYMODULE**或直接傳遞至連結器。  
  
 若要解決 LNK2027，執行下列其中一項：  
  
-   請勿傳遞至連結器檔案中包含模組相依性。  
  
-   指定的模組 **/ASSEMBLYMODULE**。  
  
-   如果模組是 safe .netmodule，請直接將模組傳遞給連結器。  
  
 如需詳細資訊，請參閱[/ASSEMBLYMODULE （加入至組件的 MSIL 模組）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)和[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。