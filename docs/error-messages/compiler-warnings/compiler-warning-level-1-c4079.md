---
title: 編譯器警告 （層級 1） C4079 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4079
dev_langs:
- C++
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc6c58649c16365d1bbeb22dcf0676947d5d8ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276564"
---
# <a name="compiler-warning-level-1-c4079"></a>編譯器警告 （層級 1） C4079
未預期的語彙基元 'token'  
  
 Pragma 引數清單中，就會發生未預期的分隔符號語彙基元。 已忽略 pragma 的其餘部分。  
  
 下列範例會產生 C4079:  
  
```  
// C4079.cpp  
// compile with: /W1  
#pragma warning(disable : 4081)  
#pragma pack(c,16)   // C4079  
  
int main() {  
}  
```