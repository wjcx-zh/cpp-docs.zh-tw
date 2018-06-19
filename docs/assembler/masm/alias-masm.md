---
title: 別名 (MASM) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b14e1c41a448d0cb7014dabc50a42305249938f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049163"
---
# <a name="alias-masm"></a>ALIAS (MASM)
**別名**指示詞建立函式的替代名稱。  這可讓您建立多個名稱，為函式，或建立文件庫可讓連結器 (LINK.exe) 將舊的函式對應至新的函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>參數  
 `actual-name`  
 函式或程序的實際名稱。  角括號是必要的。  
  
 `alias`  
 其他名稱或別名名稱。  角括號是必要的。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)