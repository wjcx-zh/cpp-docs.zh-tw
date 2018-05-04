---
title: 傾印延遲載入匯入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13f832f0ea7aaf7b766141ce7df4f83f21e1cdca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dumping-delay-loaded-imports"></a>傾印延遲載入的匯入
可傾印延遲載入匯入使用[dumpbin /imports](../../build/reference/imports-dumpbin.md) ，而且顯示稍有不同的資訊比標準匯入。 它們會隔離到其專有的區段的傾印 /imports，明確地標示為延遲載入匯入。 如果卸載映像中出現資訊時，會被記下。 如果沒有出現的繫結資訊，以及匯入的繫結位址加註目標 DLL 的日期/時間戳記。  
  
## <a name="see-also"></a>另請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)