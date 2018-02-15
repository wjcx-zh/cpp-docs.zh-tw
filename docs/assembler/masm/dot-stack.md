---
title: .STACK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 140afd2edc8a0cdb540adc7e12bf97662d5d6084
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="stack"></a>.STACK
當搭配[。模型](../../assembler/masm/dot-model.md)，定義堆疊區段 （使用堆疊的區段名稱）。 選擇性`size`指定堆疊 （預設值是 1,024） 的位元組數目。 `.STACK`指示詞就會自動關閉堆疊陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)