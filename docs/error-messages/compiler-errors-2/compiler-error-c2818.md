---
title: "編譯器錯誤 C2818 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 02c1b8e67679e7b8ce69b202c3ddef899439095d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818
多載 'operator ->' 透過類型 'type' 遞迴應用  
  
 類別成員存取運算子的重新定義包含遞迴`return`陳述式。 若要重新定義`->`運算子遞迴時，您必須移動到個別的函式呼叫運算子的遞迴常式覆寫函式。
