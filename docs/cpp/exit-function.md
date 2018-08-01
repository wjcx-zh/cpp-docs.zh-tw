---
title: exit 函式 |Microsoft Docs
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
ms.openlocfilehash: ce4272ecfee4b3d02d8bf79f7816200a392c9735
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404824"
---
# <a name="exit-function"></a>exit 函式
**結束**函式，在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。  
  
 提供做為引數的值**結束**會傳回到作業系統與程式的傳回碼或結束程式碼。 依照慣例，傳回碼為零，表示程式順利完成。  
  
> [!NOTE]
>  您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS、 中定義的常數\<stdlib.h >，以指出成功或失敗的程式。  
  
 發出**會傳回**陳述式，從`main`函式相當於呼叫**結束**函式傳回的值作為其引數。  
  
 如需詳細資訊，請參閱 <<c0> [ 結束](../c-runtime-library/reference/exit-exit-exit.md)中*執行階段程式庫參考*。  
  
## <a name="see-also"></a>另請參閱  
 [程式終止](../cpp/program-termination.md)