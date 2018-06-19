---
title: exit 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5767f6b08b4adcd3d1a8d367c6286a746eeecec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412526"
---
# <a name="exit-function"></a>exit 函式
**結束**函式，在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。  
  
 做為引數所提供的值**結束**傳回作業系統做為程式的傳回碼或結束代碼。 依照慣例，傳回碼為零，表示程式順利完成。  
  
> [!NOTE]
>  您可以使用常數`EXIT_FAILURE`和`EXIT_SUCCESS`，定義在\<stdlib.h >，以指示成功或失敗的程式。  
  
 發出`return`陳述式從**主要**函式相當於呼叫**結束**函式傳回的值做為其引數。  
  
 如需詳細資訊，請參閱[結束](../c-runtime-library/reference/exit-exit-exit.md)中*執行階段程式庫參考*。  
  
## <a name="see-also"></a>另請參閱  
 [程式終止](../cpp/program-termination.md)