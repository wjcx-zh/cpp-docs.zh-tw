---
title: "嚴重錯誤 C1197 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1197
dev_langs: C++
helpviewer_keywords: C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1658e55a9298df703051b856bb9b10dd02d8cc68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1197"></a>嚴重錯誤 C1197
無法參考 'mscorlib.dll_1'，因為程式已經參考 'mscorlib.dll_2'  
  
 編譯器會對應至 common language runtime 的版本。  不過，嘗試參考來自較舊版本的通用語言執行階段檔案的版本。  
  
 若要解決這個錯誤，只能參考來自隨附的 common language runtime 的版本，與您使用編譯的 Visual c + + 版本的檔案。  
  
## <a name="example"></a>範例  
 下列範例會產生 C1197:  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```