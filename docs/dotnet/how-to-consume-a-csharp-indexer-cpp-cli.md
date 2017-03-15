---
title: "如何：使用 C# 索引子 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++, 索引子"
  - "索引子, 使用 C#"
ms.assetid: 5a11850c-a1a2-4a0a-b95e-f6dc5a87f439
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C# 索引子 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 不包含索引子 \(Indexer\)，但是有索引屬性。  若要使用 C\# 索引子，請將索引子當做索引屬性來存取。  
  
 如需索引子的詳細資訊，請參閱：  
  
-   [索引子](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md)  
  
-   [如何：使用索引屬性](../misc/how-to-use-indexed-properties.md)  
  
## 範例  
 下列 C\# 程式會定義索引子。  
  
```  
// consume_cs_indexers.cs  
// compile with: /target:library  
using System;  
public class IndexerClass {  
   private int [] myArray = new int[100];   
   public int this [int index] {   // Indexer declaration  
      get {  
         // Check the index limits.  
         if (index < 0 || index >= 100)  
            return 0;  
         else  
            return myArray[index];  
      }  
      set {  
         if (!(index < 0 || index >= 100))  
            myArray[index] = value;  
      }  
   }  
}  
/*  
// code to consume the indexer  
public class MainClass {  
   public static void Main() {  
      IndexerClass b = new IndexerClass();  
  
      // Call indexer to initialize elements 3 and 5  
      b[3] = 256;  
      b[5] = 1024;  
      for (int i = 0 ; i <= 10 ; i++)   
         Console.WriteLine("Element #{0} = {1}", i, b[i]);  
   }  
}  
*/  
```  
  
## 範例  
 這個 Visual C\+\+ 程式會使用此索引子。  
  
```  
// consume_cs_indexers_2.cpp  
// compile with: /clr  
#using "consume_cs_indexers.dll"  
using namespace System;  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->default[0] = 21;  
   for (int i = 0 ; i <= 10 ; i++)  
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);  
}  
```  
  
  **項目 \#0 \= 21**  
**項目 \#1 \= 0**  
**項目 \#2 \= 0**  
**項目 \#3 \= 0**  
**項目 \#4 \= 0**  
**項目 \#5 \= 0**  
**項目 \#6 \= 0**  
**項目 \#7 \= 0**  
**項目 \#8 \= 0**  
**項目 \#9 \= 0**  
**項目 \#10 \= 0**   
## 請參閱  
 [與其他 .NET 程式設計語言間的互通性](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)