---
title: "連結器工具錯誤 LNK2027 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 554dac121c066dac4c05685be1b937298344a76a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2027"></a>連結器工具錯誤 LNK2027
無法解析的模組參考 ' module'  
  
 傳遞至連結器的檔案具有相依性都指定在模組上**/ASSEMBLYMODULE**或直接傳遞至連結器。  
  
 若要解決 LNK2027，執行下列其中一項：  
  
-   請勿傳遞至連結器檔案中包含模組相依性。  
  
-   指定的模組**/ASSEMBLYMODULE**。  
  
-   如果模組是 safe .netmodule，請直接將模組傳遞給連結器。  
  
 如需詳細資訊，請參閱[/ASSEMBLYMODULE （加入至組件的 MSIL 模組）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)和[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。