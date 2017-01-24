---
title: "函式樣板具現化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式樣板, 執行個體化"
  - "執行個體化, 函式樣板"
  - "範本, 執行個體化"
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式樣板具現化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

先呼叫每種類型的函式樣板時，編譯器會建立具現化。  每次具現化都是一種為類型特製化樣板函式的版本。  每次為類型使用函式時，都會呼叫此具現化。  如果您有多個相同的具現化 \(即使分屬不同模組\)，可執行檔中只能有一個具現化複本。  
  
 任何引數和參數組合的函式樣板皆可進行函式引數轉換，前提是參數不可取決於該樣板引數。  
  
 以特定類型為引數宣告樣板，即可明確具現化該函式樣板。  例如，下列程式碼是可行的：  
  
```  
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## 請參閱  
 [函式樣板](../cpp/function-templates.md)