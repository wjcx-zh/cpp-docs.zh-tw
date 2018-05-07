---
title: 連結器工具錯誤 LNK1179 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1179"></a>連結器工具錯誤 LNK1179
檔案無效或損毀： 重複的 COMDAT 'filename'  
  
 物件模組包含兩個或多個具有相同名稱的 Comdat。  
  
 這個錯誤可能因使用[/H](../../build/reference/h-restrict-length-of-external-names.md)，進而限制外部名稱的長度和[/Gy](../../build/reference/gy-enable-function-level-linking.md)的封裝中的 Comdat 函式。  
  
## <a name="example"></a>範例  
 下列程式碼，`function1`和`function2`是相同的前八個字元。 編譯 **/Gy**和 **/h8 編譯**會產生連結錯誤。  
  
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