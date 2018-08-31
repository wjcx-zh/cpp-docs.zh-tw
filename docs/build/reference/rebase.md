---
title: -REBASE |Microsoft Docs
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
ms.openlocfilehash: 686306316e6950ba62ea7c44522b95f4d935be0b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216170"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>備註  
 這個選項會設定指定檔案的基底位址。 EDITBIN 會指派新的基底地址，無條件進位到最接近 64 KB 的每個檔案的大小根據連續的位址空間。 如需基底地址的詳細資訊，請參閱[基底位址](../../build/reference/base-base-address.md)（/ 基底） 連結器選項。  
  
 指定程式的可執行檔和中的 Dll*檔案*EDITBIN 命令列中的順序將依據的為引數。 您可以選擇性地指定一或多個*修飾詞*，每個以逗號分隔 (**，**):  
  
|修飾詞|動作|  
|--------------|------------|  
|**基底 =**<em>位址</em>|提供的起始位址重新指派基底位址的檔案。 指定*地址*以十進位數或 C 語言表示法。 如果未指定基底，啟動基底地址的預設值為 0x400000。 如果清單已使用的基底必須指定，並*地址*設定的基底的位址範圍的結尾。|  
|**BASEFILE**|建立名為 COFFBASE 的檔案。TXT，這是文字檔案中所連結的預期的格式/基底選項。|  
|**向下**|會告知 EDITBIN 重新指派基底位址則是往下的從結束位址。 指定時，使用位於以下位址範圍的結尾可能最高的位址中的第一個檔案的順序重新指派檔案。 基底必須搭配下，以確保足夠的位址空間為基礎的檔案。 若要判斷指定的檔案所需的位址空間，/REBASE EDITBIN 執行的檔案，並加入顯示的總大小 64KB。|  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)