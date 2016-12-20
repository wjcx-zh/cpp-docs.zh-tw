---
title: "complex&lt;double&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.complex<double>"
  - "complex<double>"
  - "std::complex<double>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "複雜 < 雙 > 函式"
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;double&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述可儲存皆為 **double** 類型之物件的有序對，第一個代表複數的實部，而第二個代表虛部。  
  
## 語法  
  
```  
template<>  
   class complex<double> {  
public:  
   constexpr complex(  
      double _RealVal = 0,   
      double _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr explicit complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### 參數  
 `_RealVal`  
 用於建構中複數實部的 **double** 類型值。  
  
 `_ImagVal`  
 用於建構中複數虛部的 **double** 類型值。  
  
 `_ComplexNum`  
 **float** 類型或 `long double` 類型的複數，其實部及虛部用於初始化建構中 **double** 類型之複數。  
  
## 傳回值  
 **double** 類型的複數。  
  
## 備註  
 針對 **double** 類型的複數類別之複數範本類別明確特製化，和範本類別的差異只在於其定義的建構函式。 允許從 **float** 到 **double** 的隱含轉換，但從 `long double` 轉換成 **double** 必須是**明確**的。**明確**使用時就無法使用指派語法將類型轉換初始化。  
  
 如需有關此樣板類別 `complex`, ，請參閱 [complex 類別](../standard-library/complex-class.md)。 如需範本類別 `complex` 的成員清單，請參閱  
  
## 範例  
  
```  
// complex_comp_dbl.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type double gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 4.0 , 5.0 );  
   complex <double> c2double ( c2float );  
   cout << "Implicit conversion from type float to type double,"  
        << "\n gives c2double = " << c2double << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 4.0 , 5.0 );  
   complex <double> c3double ( c3longdouble );  
   cout << "Explicit conversion from type float to type double,"  
        << "\n gives c3longdouble = " << c3longdouble << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3longdouble );  
   double argc3 = arg ( c3longdouble );  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
 **指定初始的真實及虛數部分，做為類型 double 提供 c1 \= \(4,5\) 的隱含轉換，從 float double 型別，可讓 c2double \= 從 float double 型別，可讓 c3longdouble \(4,5\) 明確轉換 \= \(4，5\) 的 c3 模數從使用 c3 復原︰ abs \(c3\) \= 6.40312 c3 引數從使用 c3 復原︰ 引數 \(c3\) \= 0.896055 弧度為單位，這是 51.3402 度。**   
## 需求  
 **標頭：**\<complex\>  
  
 **命名空間:** std  
  
## 請參閱  
 [complex 類別](../standard-library/complex-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)