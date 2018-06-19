---
title: 編譯器警告 （層級 4） C4564 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f0cf68eb75d420a0d23c04687d4f9492910b53f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293669"
---
# <a name="compiler-warning-level-4-c4564"></a>編譯器警告 (層級 4) C4564
方法 'method' 的類別 'class' 定義了不支援的預設參數 'parameter'  
  
 編譯器偵測到具有一或多個參數具有預設值的方法。 叫用方法時，將忽略參數的預設值明確指定這些參數的值。 如果未明確指定這些參數的值，c + + 編譯器會產生錯誤。  
  
 使用 Visual Basic 中建立下列.dll 的情況下，指定允許預設參數方法引數：  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 和使用 Visual Basic 中，以建立此.dll 檔的下列 c + + 範例  
  
```  
// C4564.cpp  
// compile with: /clr /W4 /WX  
#using <C4564.dll>  
  
int main() {  
   TestClass ^ myx = gcnew TestClass();   // C4564  
   myx->MyMethod(9);  
   // try the following line instead, to avoid an error  
   // myx->MyMethod(9, 1);  
}  
```