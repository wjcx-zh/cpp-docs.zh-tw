---
title: "編譯器錯誤 C2696 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 70ccaf34a0191f0bd69c95d2cb110f6e6542a6d1
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2696"></a>編譯器錯誤 C2696
無法建立暫存物件的 managed 型別 'type'  
  
若要參考`const`在未受管理的程式會導致編譯器呼叫建構函式，並在堆疊上建立暫存物件。 不過，managed 的類別永遠不會在堆疊上建立。  
  
C2696 才可使用過時的編譯器選項**/clr:oldSyntax**。  

