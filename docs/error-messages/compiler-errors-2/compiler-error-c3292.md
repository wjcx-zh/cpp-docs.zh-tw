---
title: "編譯器錯誤 C3292 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eddab20396122ed6b3b8f7c75ccda17ad2a0c684
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292
無法重新開啟 cli 命名空間  
  
 無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱[平台、 default 和 cli 命名空間](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3292：  
  
```  
// C3292.cpp  
// compile with: /clr /c  
namespace cli {};   // C3292  
```