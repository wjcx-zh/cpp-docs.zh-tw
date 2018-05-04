---
title: Tools.ini 和 NMAKE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 860a334274a3a1a4ac9e11c3e7b5e9a0f136ecc0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE
NMAKE 讀取 Tools.ini 之前它會讀取 makefile，除非使用 /R。 它會尋找 Tools.ini 第一次在目前的目錄，然後初始化環境變數所指定的目錄中。 NMAKE 中的設定初始設定檔案區段的開頭`[NMAKE]`，而且可以包含任何 makefile 的資訊。 指定數字符號開頭的個別行上的註解 （#）。  
  
## <a name="see-also"></a>另請參閱  
 [執行 NMAKE](../build/running-nmake.md)