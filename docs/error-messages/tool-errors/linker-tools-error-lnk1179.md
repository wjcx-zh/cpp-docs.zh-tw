---
title: "連結器工具錯誤 LNK1179 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1179
dev_langs: C++
helpviewer_keywords: LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93b042e928331e369d64a45aa27f5f613ce9fc31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1179"></a>連結器工具錯誤 LNK1179
檔案無效或損毀： 重複的 COMDAT 'filename'  
  
 物件模組包含兩個或多個具有相同名稱的 Comdat。  
  
 這個錯誤可能因使用[/H](../../build/reference/h-restrict-length-of-external-names.md)，進而限制外部名稱的長度和[/Gy](../../build/reference/gy-enable-function-level-linking.md)的封裝中的 Comdat 函式。  
  
## <a name="example"></a>範例  
 下列程式碼，`function1`和`function2`是相同的前八個字元。 編譯**/Gy**和**/h8 編譯**會產生連結錯誤。  
  
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