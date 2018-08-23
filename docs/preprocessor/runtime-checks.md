---
title: runtime_checks |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs:
- C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b20ea9dd12bfe4daff8e2e440c96a41c220aa742
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42543093"
---
# <a name="runtimechecks"></a>runtime_checks
停用或還原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 設定。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>備註  
 
您無法啟用未使用編譯器選項啟用的執行階段檢查。 例如，如果您未指定`/RTCs`，並指定`#pragma runtime_checks( "s", restore)`將不會啟用堆疊框架驗證。  
  
**runtime_checks** pragma 必須出現在函式之外，並在出現該 pragma 後定義的第一個函式生效。 *還原*並*off*引數開啟選項中指定**runtime_checks**開啟或關閉。  
  
**Runtime_checks**可以是零個或多個參數下, 表所示。  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>runtime_checks Pragma 的參數  
  
|參數|執行階段檢查的類型|  
|--------------------|-----------------------------|  
|*s*|啟用堆疊 (框架) 驗證。|  
|*C*|將值指派給會造成資料損失的較小資料類型時回報。|  
|*u*|變數在定義之前即使用時回報。|  
  
這些是與所用的相同字母`/RTC`編譯器選項。 例如:   
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
使用 **runtime_checks** pragma 搭配空字串 (**""**) 是一種特殊形式的指示詞：  
  
- 當您使用*關閉*參數時，會設為 off 將上表中列出的執行階段錯誤檢查。  
  
- 當您使用*還原*參數，會將執行階段錯誤檢查重設為指定的`/RTC`編譯器選項。  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>另請參閱  
 
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   