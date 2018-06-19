---
title: 設定連結器選項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18728994be3f44152a263fb8a6009728e33a42a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374917"
---
# <a name="setting-linker-options"></a>設定連結器選項
內部或外部的開發環境，可以設定連結器選項。 每個連結器選項的主題討論如何在開發環境中設定。 請參閱[連結器選項](../../build/reference/linker-options.md)如需完整清單。  
  
 當您在開發環境外部執行連結時，您可以指定輸入中一或多個方法：  
  
-   在[命令列](../../build/reference/linker-command-line-syntax.md)  
  
-   使用[命令檔](../../build/reference/link-command-files.md)  
  
-   在[環境變數](../../build/reference/link-environment-variables.md)  
  
 連結第一個程序中指定選項 LINK 環境變數，後面接著選項的命令列指定的順序和命令檔中。 如果選項隨不同的引數重複顯示，最後一個處理的優先順序較高。  
  
 選項會套用至整個建置;沒有選項可以套用至特定的輸入檔中。  
  
## <a name="see-also"></a>另請參閱  
 [C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [連結器選項](../../build/reference/linker-options.md)