---
title: -HIGHENTROPYVA |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 122f524db9af10449ce809e5a8de78148d04d431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="highentropyva"></a>/HIGHENTROPYVA
指定可執行映像是否支援高熵 64 位元位址空間配置隨機載入 (ASLR)。  
  
```  
  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>備註  
 此選項會修改 .dll 檔或 .exe 檔的標頭，以指示是否支援 64 位元位址的 ASLR。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行映像的區段重訂基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。  
  
 根據預設，連結器會為 64 位元可執行映像設定此選項。 若要設定這個選項， [/DYNAMICBASE](../../build/reference/dynamicbase.md)也必須設定選項。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [/DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Windows ISV 軟體安全性防禦措施](http://msdn.microsoft.com/library/bb430720.aspx)