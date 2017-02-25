---
title: "complex 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "complex"
  - "std::complex"
  - "std.complex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex 類別"
  - "複數"
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# complex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述儲存型別 \[**型別**\] 兩個物件，代表複數的實數部分表示虛數一個  
  
## 語法  
  
```  
  
   template<class   
   Type  
   >  
class complex  
```  
  
## 備註  
 類別 \[**型別**\] 物件:  
  
-   沒有公用預設建構函式、解構函式、複製建構函式和指派運算子的一般行為。  
  
-   您可以指定整數或浮點數值，則型別轉換成與一般行為的這類值。  
  
-   定義算術運算子和數學函式，如有需要，為與一般行為的浮點型別定義。  
  
 特別是，細微的差異可能不存在於工作和預設建構之間遵循的複製建構。  在類別 \[**型別**\] 物件的作業都可能不會擲回例外狀況。  
  
 樣板的明確特製化將三個浮點型別的複雜存在分類。  在這個實作中，其他輸入 \[**型別**\] 的值為會將角色對實際計算的 **double** 和 **double** ，結果指派回型別 \[**型別**\]`.`儲存的物件  
  
### 建構函式  
  
|||  
|-|-|  
|[複雜](../Topic/complex::complex.md)|建構一個複數有指定的實數及虛數或做為其他複數複本。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/complex::value_type.md)|表示用於資料型別表示複數的實數及虛數型別。|  
  
### 成員函式  
  
|||  
|-|-|  
|[imag](../Topic/complex::imag.md)|擷取複數的虛數部分。|  
|[real](../Topic/complex::real.md)|擷取複數的實數部分。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*\=](../Topic/complex::operator*=.md)|將目標複數的因素，可能很複雜或是相同複數的實數及虛數部分。|  
|[operator\+\=](../Topic/complex::operator+=.md)|將數字加入至目標複數，增加的數目可能是複雜或型別相同將複數的實數及虛數部分。|  
|[operator\-\=](../Topic/complex::operator-=1.md)|從目標複數減去數字，減去的數目可能是複雜或型別相同將複數的實數及虛數部分。|  
|[operator\/\=](../Topic/complex::operator-=2.md)|由除數除以另一個目標複數，可能很複雜或是相同複數的實數及虛數部分。|  
|[operator\=](../Topic/complex::operator=.md)|將數字加入至目標複數，數字指定可能複雜或型別相同指派複數的實數及虛數部分。|  
  
## 需求  
 **Header**: \<複雜\>  
  
 **命名空間:** std  
  
## 請參閱  
 [complex Members](http://msdn.microsoft.com/zh-tw/d5c4466c-43a0-4817-aca1-9a5d492dae28)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)