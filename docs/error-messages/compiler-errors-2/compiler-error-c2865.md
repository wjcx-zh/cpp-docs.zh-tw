---
title: 編譯器錯誤 C2865 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246212"
---
# <a name="compiler-error-c2865"></a>編譯器錯誤 C2865
'function': handle_or_pointer 的非法比較  
  
 您可以比較參考[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)管理只會針對相等的參考類型，以查看它們是否參考相同的物件 （= =） 或不同的物件或 (！ =)。  
  
 您無法比較它們的順序，因為.NET 執行階段可能會移動受管理的物件，在任何時間，變更測試的結果。