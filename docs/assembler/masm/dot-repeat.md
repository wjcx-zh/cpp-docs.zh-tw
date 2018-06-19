---
title: .重複 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3dadaa95cb4bf0ca4a17af32332d5b5471245
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052446"
---
# <a name="repeat"></a>.REPEAT
會產生重複的區塊執行的程式碼*陳述式*直到`condition`變得則為 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，會變成 true，當 CX 是零，可能會取代為[。直到](../../assembler/masm/dot-until.md)。 `condition`是選擇性的 with **。UNTILCXZ**。  
  
## <a name="syntax"></a>語法  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)