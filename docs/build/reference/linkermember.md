---
title: -LINKERMEMBER |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linkermember
dev_langs:
- C++
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac961f985de65bb7eea9a4ad0f5d10b75fbe60d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371495"
---
# <a name="linkermember"></a>/LINKERMEMBER
```  
/LINKERMEMBER[:{1|2}]  
```  
  
## <a name="remarks"></a>備註  
 此選項會顯示在文件庫中定義的公用符號。 指定 1 個引數以顯示符號順序物件，以及它們的位移。 指定要顯示位移和物件的索引編號 2 的引數，則列出依字母順序，以及每個物件索引的符號。 若要取得的兩個輸出，請指定 /LINKERMEMBER 沒有數字的引數。  
  
 只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項僅適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)