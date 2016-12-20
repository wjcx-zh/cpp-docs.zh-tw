---
title: "noreturn | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noreturn_cpp"
  - "noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], noreturn"
  - "noreturn __declspec 關鍵字"
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noreturn
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 這個 `__declspec` 屬性會告知編譯器函式不會傳回。  因此，編譯器知道不可能執行到呼叫 **\_\_declspec\(noreturn\)** 函式之後的程式碼。  
  
 如果編譯器發現某個函式包含的控制路徑不會傳回值，則會產生警告 \(C4715\) 或錯誤訊息 \(C2202\)。  如果因為函式永不會傳回而無法到達控制路徑，您可以使用 **\_\_declspec\(noreturn\)** 來避免這個警告或錯誤。  
  
> [!NOTE]
>  將 **\_\_declspec\(noreturn\)** 加入至預期會傳回的函式可能會導致未定義的行為。  
  
## 範例  
 在下列範例中，**else** 子句不包含 return 陳述式。將 `fatal` 宣告為 **\_\_declspec\(noreturn\)** 可避免錯誤或警告訊息。  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)