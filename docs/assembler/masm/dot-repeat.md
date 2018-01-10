---
title: ".重複 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .REPEAT
dev_langs: C++
helpviewer_keywords: .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46d6502b0fe69a81dd092c97c5d651a32a7fca5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="repeat"></a>.REPEAT
會產生重複的區塊執行的程式碼*陳述式*直到`condition`變得則為 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，會變成 true，當 CX 是零，可能會取代為[。直到](../../assembler/masm/dot-until.md)。 `condition`是選擇性的 with **。UNTILCXZ**。  
  
## <a name="syntax"></a>語法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)