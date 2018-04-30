---
title: INSTR |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- InStr
dev_langs:
- C++
helpviewer_keywords:
- INSTR directive
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dd640aafe78f99f50d98569792d0c1c5ef330ee
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="instr"></a>INSTR
尋找第一個出現*textitem2*中*textitem1*。  
  
## <a name="syntax"></a>語法  
  
```  
  
name  
 INSTR [[position,]] textitem1, textitem2  
```  
  
## <a name="remarks"></a>備註  
 啟動*位置*是選擇性的。 每個文字項目可以是常值的字串常數前面加上`%`，或巨集函式所傳回的字串。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)