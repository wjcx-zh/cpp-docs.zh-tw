---
title: "編譯器警告 （層級 4） C4001 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4001
dev_langs: C++
helpviewer_keywords: C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3b5c3d82bef81ee84514b39a0ce8ab07ad6e6c36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4001"></a>編譯器警告 （層級 4） C4001
使用非標準的擴充 '單行註解'  

> [!NOTE] 
> 因為單行註解中 C99 標準 Visual Studio 2017 版本 15.5 已移除這個警告。
  
 單行註解是標準 c + + 和 C 啟動與 C99 標準。 嚴格的 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，C 的檔案，其中包含單行註解，產生 C4001 由於非標準的擴充功能的使用方式。 由於單行註解是標準 c + + 中，C 的檔案，其中包含單行註解不會產生 C4001 編譯搭配 Microsoft 擴充功能 (/Ze) 時。  
  
## <a name="example"></a>範例  
 若要停用警告，請取消註解[#pragma warning(disable:4001)](../../preprocessor/warning.md)。  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```