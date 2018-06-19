---
title: 編譯器錯誤 C3666 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3666
dev_langs:
- C++
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4672cad0f1c0b67b58233c6394e98324a9c32aaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264809"
---
# <a name="compiler-error-c3666"></a>編譯器錯誤 C3666
'constructor': 覆寫規範 'keyword' 不允許在建構函式  
  
 在建構函式，使用了覆寫規範，並不允許。 如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3666。  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```