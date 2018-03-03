---
title: "編譯器警告 （層級 1） C4678 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7648101a0862aa2006feff73a5ebe32bd0f424a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4678"></a>編譯器警告 (層級 1) C4678
基底類別 'base_type' 比 'derived_type' 更難以存取  
  
公用類型衍生自私用類型。 如果在參考的組件中具現化公用類型，則無法存取私用基底類型成員。  
  
C4678 才可使用過時的編譯器選項**/clr:oldSyntax**。 就會發生錯誤時使用**/clr**以擁有較少存取的基底類別，其衍生的類別。  
