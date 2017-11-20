---
title: "編譯器錯誤 C2865 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2865
dev_langs: C++
helpviewer_keywords: C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cbe54ebcae8753c0c5b6701ca839202ba7da533
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2865"></a>編譯器錯誤 C2865
'function': handle_or_pointer 的非法比較  
  
 您可以比較參考[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)管理只會針對相等的參考類型，以查看它們是否參考相同的物件 （= =） 或不同的物件或 (！ =)。  
  
 您無法比較它們的順序，因為.NET 執行階段可能會移動受管理的物件，在任何時間，變更測試的結果。