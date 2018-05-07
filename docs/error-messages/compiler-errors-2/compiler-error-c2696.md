---
title: 編譯器錯誤 C2696 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2696"></a>編譯器錯誤 C2696
無法建立暫存物件的 managed 型別 'type'  
  
若要參考`const`在未受管理的程式會導致編譯器呼叫建構函式，並在堆疊上建立暫存物件。 不過，managed 的類別永遠不會在堆疊上建立。  
  
C2696 才可使用過時的編譯器選項 **/clr:oldSyntax**。  
