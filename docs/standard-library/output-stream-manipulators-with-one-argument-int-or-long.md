---
title: "具有單一引數 (int 或 long) 的輸出資料流操作工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸出資料流, int 或 long 引數操作工具"
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 具有單一引數 (int 或 long) 的輸出資料流操作工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從類別庫為建立參數型操作工具提供一組巨集。  有一個 `int` 或 `long` 引數的操作工具是特殊案例。  若要建立接受單一 `int` 或 `long` 引數的輸出資料流操作工具 \(例如 `setw`\)，您必須使用 \_Smanip 巨集，在 \<iomanip\>定義。  這個範例定義插入空白的指定數目的資料流上 `fillblank` 操作工具:  
  
## 範例  
  
```  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## 請參閱  
 [具有引數的自訂操作工具](../standard-library/custom-manipulators-with-arguments.md)