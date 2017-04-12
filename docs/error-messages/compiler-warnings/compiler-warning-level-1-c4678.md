---
title: "編譯器警告 （層級 1） C4678 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: d35e60d60d194bc0ca68a116dc45b6d9864d9fe2
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4678"></a>編譯器警告 (層級 1) C4678
基底類別 'base_type' 比 'derived_type' 更難以存取  
  
公用類型衍生自私用類型。 如果在參考的組件中具現化公用類型，則無法存取私用基底類型成員。  
  
C4678 才可使用過時的編譯器選項**/clr:oldSyntax**。 就會發生錯誤時使用**/clr**具有較低的可存取的基底類別，其衍生的類別。  

