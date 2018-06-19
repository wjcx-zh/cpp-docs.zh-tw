---
title: 編譯器錯誤 C2010 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2010
dev_langs:
- C++
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c1f1a042881420c85670020e05ded3684a91268
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163929"
---
# <a name="compiler-error-c2010"></a>編譯器錯誤 C2010
'character': 未預期在巨集型式參數清單  
  
 在巨集定義的型式參數清單中不正確地使用了該字元。 移除以解決此錯誤的字元。  
  
 下列範例會產生 C2010:  
  
```  
// C2010.cpp  
// compile with: /c  
#define mymacro(a|) (2*a)   // C2010  
#define mymacro(a) (2*a)   // OK  
```