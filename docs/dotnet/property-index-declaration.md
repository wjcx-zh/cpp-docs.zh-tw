---
title: "屬性索引宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "預設的索引子"
  - "預設, 索引子"
  - "索引屬性, C++"
  - "索引子"
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 屬性索引宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，用於宣告索引屬性的語法已變更。  
  
 索引屬性的 Managed Extensions 語言支援有兩個主要缺點，第一個是無法提供類別層級的註標 \(Subscript\)，也就是說，必須提供名稱給所有的索引屬性，因此，可能會無法提供可直接套用至 `Vector` 或 `Matrix` 類別物件的 Managed 註標運算子。  第二個小缺點是，視覺上很難區分屬性與索引屬性的差別，只能藉由查看參數數目來區分。  最後，索引屬性會遭遇到與其他非索引屬性相同的問題，也就是，存取子並非被視為原子單位 \(Atomic Unit\)，而是區分成個別的方法。例如：  
  
```  
public __gc class Vector;  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value);  
   __property float get_Item( int r, int c );  
  
   __property void set_Row( int r, Vector* value );  
   __property Vector* get_Row( int r );  
};  
```  
  
 如您所見，索引子 \(Indexer\) 只會由其他參數來區別，以指定兩個或單一的維度 \(Dimension\) 索引。  在新語法中，索引子是由括號 \(\[,\]\) 後面加上索引子名稱來區別，並指示每個索引的數目及類型：  
  
```  
public ref class Vector {};  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 為了指示可直接套用至新語法中類別物件的類別層級索引子，便會重複使用 `default` 關鍵字代替明確的名稱。  例如：  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat …  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer …  
  
   property float default [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 在新語法中，當指定了預設的索引屬性時，就會保留下列兩個名稱：`get_Item` 和 `set_Item`。  這是因為這些是為預設索引屬性所產生的基礎名稱。  
  
 請注意，沒有簡單的索引語法類似於簡單的屬性語法。  
  
## 請參閱  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [如何：使用索引屬性](../misc/how-to-use-indexed-properties.md)