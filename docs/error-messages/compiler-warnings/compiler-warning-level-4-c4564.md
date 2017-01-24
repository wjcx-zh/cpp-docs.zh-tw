---
title: "編譯器警告 (層級 4) C4564 | Microsoft Docs"
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
  - "C4564"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4564"
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4564
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

方法 'method' \(屬於 class 'class'\) 定義了不支援的預設參數 'parameter'  
  
 編譯器偵測到方法有一個或更多有預設值的參數。  叫用該方法時，這些參數的預設值會被忽略；請明確指定這些參數的值。  如果您不明確指定這些參數的值，C\+\+ 編譯器會產生錯誤。  
  
 下列用 Visual Basic 建立的 .dll 可允許方法引數上的預設參數：  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 及下列會使用 Visual Basic 建立的 .dll 之 C\+\+ 範例。  
  
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