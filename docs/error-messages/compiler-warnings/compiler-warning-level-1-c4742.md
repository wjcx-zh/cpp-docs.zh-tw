---
title: "編譯器警告 (層級 1) C4742 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4742"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4742"
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4742
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' 在 'file1' 和 'file2' 中有不同的對齊: number 和 number  
  
 在兩個檔案中參考或定義的外部變數在這兩個檔案中有不同的對齊。  當編譯器發現在 *file1* 中變數的 `__alignof` 與在 *file2* 中變數的 `__alignof` 不同，就會發出這項警告。  造成這種情況的原因可能是：在不同檔案中宣告變數時，使用了不相容的型別，或是在不同檔案中使用了不相符的 `#pragma pack`。  
  
 若要解除這項警告，請使用相同的型別定義，或使用不同的變數名稱。  
  
 如需詳細資訊，請參閱[pack](../../preprocessor/pack.md)與[\_\_alignof 運算子](../../cpp/alignof-operator.md)。  
  
## 範例  
 這是定義型別的第一個檔案。  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## 範例  
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