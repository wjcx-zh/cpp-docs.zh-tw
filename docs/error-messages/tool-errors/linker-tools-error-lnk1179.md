---
title: "連結器工具錯誤 LNK1179 | Microsoft Docs"
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
  - "LNK1179"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1179"
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1179
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案無效或損毀：重複的 COMDAT 'filename'  
  
 物件模組包含了兩個或多個具有相同名稱的 COMDAT。  
  
 使用了限制外部名稱 \(External Name\) 長度的 [\/H](../../build/reference/h-restrict-length-of-external-names.md)，和在 COMDAT 中封裝函式的 [\/Gy](../../build/reference/gy-enable-function-level-linking.md)，可能會產生這項錯誤。  
  
## 範例  
 在下列程式碼中，`function1` 和 `function2` 的前八個字元是相同的。  使用 **\/Gy** 和 **\/H8** 編譯會產生連結錯誤。  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```