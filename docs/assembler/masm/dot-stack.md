---
title: .堆疊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="stack"></a>.STACK
當搭配[。模型](../../assembler/masm/dot-model.md)，定義堆疊區段 （使用堆疊的區段名稱）。 選擇性`size`指定堆疊 （預設值是 1,024） 的位元組數目。 `.STACK`指示詞就會自動關閉堆疊陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)