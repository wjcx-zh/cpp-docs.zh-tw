---
title: "編譯器警告 （層級 4） C4295 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1424302c5c109ff79f35c922d1e5051b15655554
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4295"></a>編譯器警告 (層級 4) C4295
  
> '*陣列*': 陣列是太小無法包含結束的 null 字元  
  
 初始化陣列，但陣列中的最後一個字元不是 null。存取陣列可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
 下列範例會產生 C4295。 若要修正此問題，您可以宣告陣列大小更大，以保存終止 null 從初始設定式。  
  
```C  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```