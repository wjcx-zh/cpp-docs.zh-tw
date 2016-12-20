---
title: "complex&lt;float&gt; | Microsoft Docs"
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
  - "std::complex<float>"
  - "std.complex<float>"
  - "complex<float>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex<float> 函式"
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;float&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述可儲存皆為 **float** 類型之物件的有序對，第一個代表複數的實部，而第二個代表虛部。  
  
## 語法  
  
```  
template<>  
   class complex<float> {  
public:  
   constexpr complex(  
      float _RealVal = 0,   
      float _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<float>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### 參數  
 `_RealVal`  
 用於建構中複數實部的 **float** 類型值。  
  
 `_ImagVal`  
 用於建構中複數虛部的 **float** 類型值。  
  
 `_ComplexNum`  
 **double** 類型或 `long double` 類型的複數，其實部及虛部用於初始化建構中 **float** 類型的複數。  
  
## 傳回值  
 **float** 類型的複數。  
  
## 備註  
 針對 **float** 類型的複數類別之複數範本類別明確特製化，和此範本類別的差異只在於其定義的建構函式。  允許從 **float** 到 **double** 的隱含但較不安全的轉換，但從 **float** 轉換成 `long double` 必須是**明確**的。  **明確**使用時，就無法使用指派語法將類型轉換初始化。  
  
 如需範本類別 `complex` 的詳細資訊，請參閱 [complex 類別](../standard-library/complex-class.md)。  如需範本類別 `complex` 的成員清單，請參閱  
  
## 範例  
  
```  
// complex_comp_flt.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <float> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type double  
   complex <double> c2double ( 1.0 , 3.0 );  
   complex <float> c2float ( c2double );  
   cout << "Implicit conversion from type double to type float,"  
        << "\n gives c2float = " << c2float << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 3.0 , 4.0 );  
   complex <float> c3float ( c3longdouble );  
   cout << "Explicit conversion from type long double to type float,"  
        << "\n gives c3float = " << c3float << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3float);  
   double argc3 = arg ( c3float);  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
  **Specifying initial real & imaginary parts,**  
 **as type float gives c1 \= \(4,5\)**  
**Implicit conversion from type double to type float,**  
 **gives c2float \= \(1,3\)**  
**Explicit conversion from type long double to type float,**  
 **gives c3float \= \(3,4\)**  
**The modulus of c3 is recovered from c3 using: abs \( c3 \) \= 5**  
**Argument of c3 is recovered from c3 using:**  
 **arg \( c3 \) \= 0.927295 radians, which is 53.1301 degrees.**   
## 需求  
 **標頭：**\<complex\>  
  
 **命名空間:** std  
  
## 請參閱  
 [complex 類別](../standard-library/complex-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)