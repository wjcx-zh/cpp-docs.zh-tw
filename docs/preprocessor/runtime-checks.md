---
title: "runtime_checks |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs: C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee68bfc7ddace32432f64d4325d9a4c669e0819b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="runtimechecks"></a>runtime_checks
停用或還原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 設定。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>備註  
 您無法啟用未使用編譯器選項啟用的執行階段檢查。 例如，如果您未指定 /RTC，則指定 `#pragma runtime_checks( "s", restore)` 不會啟用堆疊框架驗證。  
  
 **runtime_checks** pragma 必須出現在函式之外，並在出現該 pragma 後定義的第一個函式生效。 **restore** 和 **off** 引數可開啟或關閉在 *runtime_checks* 中指定的選項。  
  
 *runtime_checks* 可以是下表所示的零個或多個參數。  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>runtime_checks Pragma 的參數  
  
|參數|執行階段檢查的類型|  
|--------------------|-----------------------------|  
|**秒**|啟用堆疊 (框架) 驗證。|  
|**C**|將值指派給會造成資料損失的較小資料類型時回報。|  
|**u**|變數在定義之前即使用時回報。|  
  
 這些是與搭配 /RTC 編譯器選項使用的相同字母。 例如：  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 使用 **runtime_checks** pragma 搭配空字串 (**""**) 是一種特殊形式的指示詞：  
  
-   當您使用 **off** 參數時，會將上表中所列的執行階段錯誤檢查關閉。  
  
-   當您使用 **restore** 參數時，會將執行階段錯誤檢查重設為您使用 /RTC 編譯器選項指定的內容。  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
