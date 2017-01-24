---
title: "property (C++) | Microsoft Docs"
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
  - "property_cpp"
  - "Property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], property"
  - "property __declspec 關鍵字"
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# property (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 這個屬性可以套用至類別或結構定義中的非靜態「虛擬資料成員」。  編譯器會將這些「虛擬資料成員」的參考變更為函式呼叫，將它們視為資料成員。  
  
## 語法  
  
```  
  
      __declspec( property( get=get_func_name ) ) declarator  
__declspec( property( put=put_func_name ) ) declarator  
__declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## 備註  
 當編譯器查看成員選取運算子 \(「**.**」或「**\-\>**」\) 右側以此屬性宣告的資料成員時，會視此類運算式為左值或右值來決定將作業轉換成 **get** 或 **put** 函式。  在更複雜的內容 \(例如「`+=`」\) 中，同時執行 **get** 和 **put** 即可重寫。  
  
 在類別或結構定義中也可以使用這個屬性宣告空陣列。  例如：  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 上述陳述式表示可以同時使用 `x[]` 和一個或多個陣列索引。  在這種情況下，`i=p->x[a][b]` 會轉換為 `i=p->GetX(a, b)`，而 `p->x[a][b] = i` 則會轉換為 `p->PutX(a, b, i);`  
  
 **END Microsoft 特定的**  
  
## 範例  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)