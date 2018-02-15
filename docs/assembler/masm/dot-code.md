---
title: .CODE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de0a9b8930c04929b05b02931a1f796d28a78099
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="code"></a>.CODE
當搭配[。模型](../../assembler/masm/dot-model.md)，表示程式碼區段的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`name`|指定名稱的程式碼區段的選擇性參數。 預設名稱是很小，很小，壓縮和一般 _TEXT[模型](../../assembler/masm/dot-model.md)。 預設名稱是*modulename*_TEXT 其他模型。|  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)