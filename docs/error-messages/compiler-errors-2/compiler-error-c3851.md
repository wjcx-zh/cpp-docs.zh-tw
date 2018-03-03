---
title: "編譯器錯誤 C3851 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5f0cca8f3c1dfc4b3b35d494ebf73459a74d03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3851"></a>編譯器錯誤 C3851
'char'：通用字元名稱不能指定基礎字元集中的字元  
  
 在編譯為 C++ 的程式碼中，您無法在字串或字元常值之外使用代表基礎來源字元集的通用字元名稱。 如需詳細資訊，請參閱 [Character Sets](../../cpp/character-sets2.md)。 在編譯為 C 的程式碼中，您無法針對 0x20 到 0x7f 範圍內的字元 (0x24('$')、0x40 ('@') 或 0x60 ('`') 除外) 使用通用字元名稱。  
  
 下列範例會產生 C3851，並顯示如何修正此問題：  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```