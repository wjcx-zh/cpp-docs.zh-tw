---
title: Makefile 前置處理中的運算式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04a53e5e6fe45c2c846cae3fb9e973fe1c712107
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367264"
---
# <a name="expressions-in-makefile-preprocessing"></a>Makefile 前置處理中的運算式
**！如果**或 **！ELSE IF** `constantexpression` （以十進位或 C 語言標記） 的整數常數、 字串常數或命令所組成。 使用括號群組運算式。 運算式中使用 c-style 帶正負號長整數算術。數字是範圍-2147483648 到 2147483647 的 32 位元二補數格式。  
  
 運算式可以使用執行的運算子，常數值、 命令、 字串、 巨集，以及檔案系統路徑的結束代碼。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [Makefile 前置處理運算子](../build/makefile-preprocessing-operators.md)  
  
 [前置處理中執行程式](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>另請參閱  
 [Makefile 前置處理](../build/makefile-preprocessing.md)