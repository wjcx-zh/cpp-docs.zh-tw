---
title: "signal 常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs: C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fddb279acfbb6d8841ac17a27cd43de205dc9dbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="signal-constants"></a>signal 常數
## <a name="syntax"></a>語法  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>備註  
 `sig` 引數必須是下面所列的其中一個資訊清單常數 (在 SIGNAL.H 中定義)。  
  
 `SIGABRT`  
 異常終止。 預設動作終止呼叫程式，結束代碼 3。  
  
 `SIGABRT_COMPAT`  
 與 SIGABRT 相同。 針對與其他平台的相容性。  
  
 `SIGFPE`  
 浮點數錯誤，例如溢位、除數為零，或是無效的作業。 預設動作終止呼叫程式。  
  
 `SIGILL`  
 不合法的指令。 預設動作終止呼叫程式。  
  
 `SIGINT`  
 CTRL+C 中斷。 預設動作終止呼叫程式，結束代碼 3。  
  
 `SIGSEGV`  
 不合法的儲存體存取。 預設動作終止呼叫程式。  
  
 `SIGTERM`  
 終止傳送給程式的要求。 預設動作終止呼叫程式，結束代碼 3。  
  
 `SIG_ERR`  
 指出已發生錯誤之訊號的傳回類型。  
  
## <a name="see-also"></a>另請參閱  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [全域常數](../c-runtime-library/global-constants.md)