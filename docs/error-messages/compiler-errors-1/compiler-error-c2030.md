---
title: "編譯器錯誤 C2030 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: b38e76d73cf6e933145d8d382b653b8a5ed1892e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2030"></a>編譯器錯誤 C2030
具有 'protected private' 可及性的解構函式不可以是宣告為 'sealed' 之類別的成員  
  
 宣告為 `sealed` 的 Windows 執行階段類別不能有受保護的私用解構函式。 sealed 類型只允許公用虛擬和私用非虛擬解構函式。 如需詳細資訊，請參閱[Ref 類別與結構](http://msdn.microsoft.com/Library/3d736b82-0bf0-48cf-bac1-cc9d110b70d1)。  
  
 若要修正這個錯誤，請變更解構函式的存取範圍。
