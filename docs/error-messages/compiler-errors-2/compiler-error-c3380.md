---
title: "編譯器錯誤 C3380 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: fbc75caa22d3c46b5a7a487662119a43b27eaf2b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3380"></a>編譯器錯誤 C3380
'class' : 組件存取規範無效 - 只能使用 'public' 或 'private'  
  
 套用至受管理的類別或結構時[公用](../../cpp/public-cpp.md)和[私人](../../cpp/private-cpp.md)關鍵字指出是否會透過組件中繼資料中公開的類別。 只有`public`或`private`可以套用至編譯的程式中的類別[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 `ref`和`value`關鍵字，搭配使用時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，表示為 managed 類別 (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
 下列範例會產生 C3380：  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  

