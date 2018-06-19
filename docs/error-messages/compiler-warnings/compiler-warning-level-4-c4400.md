---
title: 編譯器警告 （層級 4） C4400 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7164b323e5108b44ea40da699ffb906508f731a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299379"
---
# <a name="compiler-warning-level-4-c4400"></a>編譯器警告 (層級 4) C4400
'type': 不支援此類型的 const/volatile 限定詞  
  
 [Const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md)限定詞不適用於 common language runtime 類型的變數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4400。  
  
```  
// C4400.cpp  
// compile with: /clr /W4  
// C4401 expected  
using namespace System;  
#pragma warning (disable : 4101)  
int main() {  
   const String^ str;   // C4400  
   volatile String^ str2;   // C4400  
}  
```