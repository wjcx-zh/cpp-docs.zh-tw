---
title: 編譯器命令列語法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825121a111d47de6b012aad444907363ad8c2a36
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-command-line-syntax"></a>編譯器命令列語法
CL 命令列使用下列語法：  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 下表描述 CL 命令的輸入。  
  
|進入|意義|  
|-----------|-------------|  
|*選項*|一或多個[CL 選項](../../build/reference/compiler-options.md)。 請注意，所有的選項會套用至所有指定的原始程式檔。 選項的指定方式是正斜線 （/） 或破折號 （-）。 如果選項需要引數，此選項的描述文件是否在選項與引數之間有一個空格。 選項名稱 （除了 /HELP 選項） 會區分大小寫。 請參閱[CL 選項的順序](../../build/reference/order-of-cl-options.md)如需詳細資訊。|  
|`file`|一或多個原始程式檔、.obj 檔案或程式庫的名稱。 CL 編譯原始程式檔，並將程式庫.obj 檔案的名稱傳遞至連結器。 請參閱[CL 檔名語法](../../build/reference/cl-filename-syntax.md)如需詳細資訊。|  
|*lib*|一或多個程式庫名稱。 CL 會將這些名稱傳遞至連結器。|  
|*命令檔*|包含多個選項和檔名的檔案。 請參閱[CL 命令檔](../../build/reference/cl-command-files.md)如需詳細資訊。|  
|*連結選擇*|一或多個[連結器選項](../../build/reference/linker-options.md)。 CL 會將這些選項傳遞至連結器。|  
  
 您可以指定任意數目的選項、 檔名及程式庫名稱，只要在命令列上的字元數不會超過 1024 個，取決於作業系統的限制。  
  
 Cl.exe 的傳回值的相關資訊，請參閱[的 cl.exe 的傳回值](../../build/reference/return-value-of-cl-exe.md)。  
  
> [!NOTE]
>  不保證 1024年個字元的命令列輸入的限制為未來的 Windows 版本中維持相同。  
  
## <a name="see-also"></a>另請參閱  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)