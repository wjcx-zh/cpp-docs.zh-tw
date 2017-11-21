---
title: "編譯器錯誤 C2585 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2585
dev_langs: C++
helpviewer_keywords: C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb0720c7fa9cde9a735c4353bb6bf1d8714ff0fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2585"></a>編譯器錯誤 C2585
明確轉換為 'type' 模稜兩可  
  
 類型轉換可能會產生多個結果。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  從多個繼承的類別或結構類型轉換。 如果型別繼承一次以上相同的基底類別，則轉換函數或運算子必須使用範圍解析 (`::`) 來指定要在轉換中使用繼承的類別。  
  
2.  轉換運算子和建構函式已經定義產生相同的轉換。