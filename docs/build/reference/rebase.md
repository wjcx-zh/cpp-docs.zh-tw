---
title: -REBASE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rebase
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a5e2b68768b01d71532c358a14c53d8a033e1ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377085"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>備註  
 這個選項會設定指定檔案的基底位址。 EDITBIN 會指派新的基底地址，無條件進位到最接近的 64 KB 的每個檔案的大小根據連續的位址空間中。 如需基底地址的詳細資訊，請參閱[基底位址](../../build/reference/base-base-address.md)（/ 基底） 連結器選項。  
  
 指定程式的可執行檔和 Dll 中的*檔案*上時進行計算的順序 EDITBIN 命令列引數。 您可以選擇性地指定一或多個*修飾詞*、 以逗號區隔 (**，**):  
  
|修飾詞|動作|  
|--------------|------------|  
|基底 **= * * * 位址*|提供的開始位址重新指派檔案的基底位址。 指定*位址*以十進位數或 C 語言表示法。 如果未指定基底，起始基底位址的預設值為 0x400000。 必須指定如果清單是使用的基底，和*位址*設定基底的位址範圍的結尾。|  
|BASEFILE|建立名為 COFFBASE 檔案。TXT、 是文字檔案中所連結的預期格式 / 基底選項。|  
|向下|會告知 EDITBIN 重新指派基底往下的從結束位址。 指定時，使用位於以下位址範圍的結尾可能最高的位址中的第一個檔案的順序重新指派檔案。 基底必須搭配清單，以確保足夠的位址空間為基礎的檔案。 若要判斷指定的檔案所需的位址空間，請執行 /REBASE EDITBIN 檔案並加入 64 KB 顯示的總大小。|  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)