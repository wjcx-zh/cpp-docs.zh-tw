---
title: "編譯器警告 (層級 1) C4742 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4742
dev_langs: C++
helpviewer_keywords: C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da12d4d1e5e8b6f9be6c21601e04f08d1b269cec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4742"></a>編譯器警告 (層級 1) C4742
'var' 有 'file1' 和 'file2' 在不同的對齊： 和號碼  
  
 外部變數已被參考，或在兩個檔案中定義的那些檔案中有不同的對齊。 當編譯器發現的就會發出這個警告`__alignof`中變數*file1*不同於`__alignof`中變數*file2*。 這可能使用不相容的類型時宣告變數在不同的檔案，或使用不相符造成`#pragma pack`不同檔案中。  
  
 若要解決這個警告，請使用相同的類型定義，或使用不同的變數名稱。  
  
 如需詳細資訊，請參閱[套件](../../preprocessor/pack.md)和[__alignof 運算子](../../cpp/alignof-operator.md)。  
  
## <a name="example"></a>範例  
 這是定義類型的第一個檔案。  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4742。  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```