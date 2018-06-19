---
title: EXTERNDEF |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b010f52f91a04388f34052fcc5c374690cff13df
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052696"
---
# <a name="externdef"></a>EXTERNDEF
定義一或多個外部變數、 標籤或符號呼叫*名稱*其型別是`type`。  
  
## <a name="syntax"></a>語法  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>備註  
 如果*名稱*定義在模組中，它會被視為[公用](../../assembler/masm/public-masm.md)。 如果*名稱*參考在模組中，它會被視為[EXTERN](../../assembler/masm/extern-masm.md)。 如果*名稱*是未參考，則會忽略它。 `type`可以[ABS](../../assembler/masm/operator-abs.md)，哪些匯入*名稱*為常數。 通常用在 include 檔。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)