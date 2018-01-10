---
title: "編譯器警告 （層級 4） C4205 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4205
dev_langs: C++
helpviewer_keywords: C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fd40764ea6a37acf11a43fb08ffad80e4c1bd8c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4205"></a>編譯器警告 (層級 4) C4205
使用非標準擴充： 函式範圍中的靜態函式宣告  
  
 搭配 Microsoft 擴充功能 (/Ze) 下**靜態**函式可以宣告為另一個函式內。 此函式會指定全域範圍。  
  
## <a name="example"></a>範例  
  
```  
// C4205.c  
// compile with: /W4  
void func1()  
{  
   static int func2();  // C4205  
};  
  
int main()  
{  
}  
```  
  
 這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。