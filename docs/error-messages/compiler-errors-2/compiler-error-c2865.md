---
title: "編譯器錯誤 C2865 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 3bb55d094e00400c57617857aa1ac29677f1b72a
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2865"></a>編譯器錯誤 C2865
'function': 不合法的 handle_or_pointer 的比較  
  
 您可以比較參考[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)或受管理的相等性只以查看它們參考相同物件 （= =） 或不同的物件的參考型別 (！ =)。  
  
 您無法比較它們的順序，因為.NET 執行階段可能會移動受管理的物件，在任何時間，變更測試的結果。
