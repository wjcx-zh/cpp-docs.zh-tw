---
title: "編譯器錯誤 C2696 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2696
dev_langs: C++
helpviewer_keywords: C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4d6efbf8dcf10d1608bb1a54b843a49d42cb22a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2696"></a>編譯器錯誤 C2696
無法建立暫存物件的 managed 型別 'type'  
  
若要參考`const`在未受管理的程式會導致編譯器呼叫建構函式，並在堆疊上建立暫存物件。 不過，managed 的類別永遠不會在堆疊上建立。  
  
C2696 才可使用過時的編譯器選項**/clr:oldSyntax**。  
