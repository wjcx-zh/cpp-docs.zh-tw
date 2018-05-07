---
title: 編譯器錯誤 C3139 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3139
dev_langs:
- C++
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06d63ef93c4924e0ee5e8808c5783ee5a0fb7f79
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3139"></a>編譯器錯誤 C3139
'struct': 無法匯出 UDT 沒有成員  
  
 您嘗試將套用[匯出](../../windows/export.md)屬性設定為空的 UDT （使用者定義型別）。 例如:   
  
```  
// C3139.cpp  
#include "unknwn.h"  
[emitidl];  
[module(name=xx)];  
  
[export] struct MyStruct {   // C3139 empty type  
};  
int main(){}  
```