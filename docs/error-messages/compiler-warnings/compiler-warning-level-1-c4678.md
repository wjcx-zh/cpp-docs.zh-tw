---
title: 編譯器警告 （層級 1） C4678 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4678"></a>編譯器警告 (層級 1) C4678
基底類別 'base_type' 比 'derived_type' 更難以存取  
  
公用類型衍生自私用類型。 如果在參考的組件中具現化公用類型，則無法存取私用基底類型成員。  
  
C4678 才可使用過時的編譯器選項 **/clr:oldSyntax**。 就會發生錯誤時使用 **/clr**以擁有較少存取的基底類別，其衍生的類別。  
