---
title: complex&lt;double&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- complex/std::complex<double>
dev_langs:
- C++
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d82fccaa98dd0591cf8d7b3a9fcabb9e78f7d88
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;
描述的物件儲存類型的物件的排序的配對，**雙 **第一個代表第二個複數的實數部分代表虛部。  
  
## <a name="syntax"></a>語法  
  
```
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```  
  
#### <a name="parameters"></a>參數  
 `RealVal`  
 要建構之複數實數部分的 **double** 類型值。  
  
 `ImagVal`  
 要建構之複數虛數部分的 **double** 類型值。  
  
 `complexNum`  
 **float** 類型或 `long double` 類型的複數，其實數及虛數部分用於初始化要建構之 **double** 類型的複數。  
  
## <a name="return-value"></a>傳回值  
 **double** 類型的複數。  
  
## <a name="remarks"></a>備註  
 **double** 類型 complex 類別的 complex 範本類別明確特製化，其與範本類別的差異只在於所定義的建構函式。 允許從 **float** 到 **double** 的隱含轉換，但從 `long double` 轉換成 **double** 必須是**明確**的。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。  
  
 如需 `complex` 範本類別的詳細資訊，請參閱 [complex 類別](../standard-library/complex-class.md)。 如需範本類別 `complex` 的成員清單，請參閱  
  
## <a name="example"></a>範例  
  
```cpp  
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
\* Output:   
Specifying initial real & imaginary parts,  
 as type double gives c1 = (4,5)  
Implicit conversion from type float to type double,  
 gives c2double = (4,5)  
Explicit conversion from type float to type double,  
 gives c3longdouble = (4,5)  
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312  
Argument of c3 is recovered from c3 using:  
 arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭**：\<complex>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [complex 類別](../standard-library/complex-class.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



