---
title: "discrete_distribution 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbd82957b213a88792d7dba8a7e7dc17b8b28bb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="discretedistribution-class"></a>discrete_distribution 類別
產生散整數分佈，其中有統一寬度間隔，且每個間隔中有統一可能性。  
  
## <a name="syntax"></a>語法  
  
```  
template<class IntType = int>
class discrete_distribution  
   {  
public:  
   // types  
   typedef IntType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   discrete_distribution();
   template <class InputIterator>  
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>  
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions  
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```   
#### <a name="parameters"></a>參數  
*IntType*  
 整數結果類型，預設值為 `int`。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 此取樣分佈有統一寬度間隔，且每個間隔中有統一可能性。 如需其他取樣分佈的資訊，請參閱 [piecewise_linear_distribution 類別](../standard-library/piecewise-linear-distribution-class.md)和 [piecewise_constant_distribution 類別](../standard-library/piecewise-constant-distribution-class.md)。  
  
 下表提供各個成員的文章連結：  
  
|||  
|-|-|  
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|  
|`discrete_distribution::operator()`|[param_type](#param_type)|  
  
 屬性函式 `vector<double> probabilities()` 會傳回每個產生之整數的個別可能性。  
  
 如需有關分佈類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const int s) {  
  
    // uncomment to use a non-deterministic generator  
    // random_device rd;  
    // mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "probabilities (value: probability):" << endl;  
    vector<double> p = distr.probabilities();  
    int counter = 0;  
    for (const auto& n : p) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
  
    // generate the distribution as a histogram  
    map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << s << " samples:" << endl;  
    for (const auto& elem : histogram) {  
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    int samples = 100;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for the sample count: 100  
min() == 0  
max() == 4  
probabilities (value: probability):  
          0:   0.0666666667  
          1:   0.1333333333  
          2:   0.2000000000  
          3:   0.2666666667  
          4:   0.3333333333  
  
Distribution for 100 samples:  
    0 :::  
    1 ::::::::::::::  
    2 ::::::::::::::::::  
    3 :::::::::::::::::::::::::::::  
    4 ::::::::::::::::::::::::::::::::::::    
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
##  <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution  
 建構分佈。  
  
```  
// default constructor  
discrete_distribution();  
  
// construct using a range of weights, [firstW, lastW)  
template <class InputIterator>  
discrete_distribution(InputIterator firstW, InputIterator lastW);  
  
// construct using an initializer list for range of weights  
discrete_distribution(initializer_list<double> weightlist);  
  
// construct using unary operation function  
template <class UnaryOperation>  
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);  
  
// construct from an existing param_type structure  
explicit discrete_distribution(const param_type& parm);  
```  
  
### <a name="parameters"></a>參數  
*firstW*  
 要建構分佈的清單中的第一個迭代器。  
  
*lastW*  
 要建構分佈的清單中的最後一個迭代器 (非內含，因為迭代器針對結尾使用空的項目)。  
  
*weightlist*  
 要建構分佈的 [initializer_list](../cpp/initializers.md)。  
  
*count*  
 分佈範圍中的元素數目。 若 `count==0`，則相當於預設建構函式 (一律產生零)。  
  
*low*  
 分佈範圍中的最低值。  
  
*high*  
 分佈範圍中的最高值。  
  
*weightfunc*  
 表示分佈的可能性函式的物件。 參數和傳回值都必須可以轉換為 `double`。  
  
*parm*  
 用來建構分佈的 `param_type` 結構。  
  
### <a name="remarks"></a>備註  
預設建構函式會建構其中儲存的可能性值具有一個項目，且該項目具有值 1 的物件。 這會導致分佈一律產生零。  
  
如果是具有 *firstW* 和 *lastW* 參數的迭代器範圍建構函式，其會使用加權值來建構分佈物件，這些加權值是取自間隔序列 [*firstW*, *lastW*) 的迭代器。  
  
如果是具有 *weightlist* 參數的初始設定式清單建構函式，其會使用來自初始設定式清單 *weightlist* 的加權來建構分佈物件。  
  
如果是具有 *count*、*low*、*high* 和 *weightfunc* 參數的建構函式，其會根據下列規則建構初始化的分佈物件：  
-  如果*計數*< 1，  **n**  = 1，且在這種情況相當於預設建構函式，一律會產生零。  
-  如果*計數*> 0，  **n**   = *計數*。 提供**d** = (*高* - *低*) /  **n** 大於零，使用**d**統一子範圍，每個加權指派如下： `weight[k] = weightfunc(x)`，其中**x** = *低* + **k** *  **d** + **d** / 2，針對**k** = 0，...，  **n**  -1。  
  
如果是具有 `param_type` 參數 *parm* 的建構函式，其會使用 *parm* 作為預存參數結構來建構分佈物件。  
  
##  <a name="param_type"></a>  discrete_distribution::param_type  
 儲存分佈的所有參數。  
  
```  
struct param_type {  
   typedef discrete_distribution<result_type> distribution_type;  
   param_type();

   // construct using a range of weights, [firstW, lastW)  
   template <class InputIterator>  
   param_type(InputIterator firstW, InputIterator lastW);  
  
   // construct using an initializer list for range of weights  
   param_type(initializer_list<double> weightlist);  
  
   // construct using unary operation function  
   template <class UnaryOperation>  
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;
   
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```   
### <a name="parameters"></a>參數  
*firstW*  
 要建構分佈的清單中的第一個迭代器。  
  
*lastW*  
 要建構分佈的清單中的最後一個迭代器 (非內含，因為迭代器針對結尾使用空的項目)。  
  
*weightlist*  
 要建構分佈的 [initializer_list](../cpp/initializers.md)。  
  
*count*  
 分佈範圍中的元素數目。 若 *count* 為 0，此項目就相當於預設建構函式 (一律產生零)。  
  
*low*  
 分佈範圍中的最低值。  
  
*high*  
 分佈範圍中的最高值。  
  
*weightfunc*  
 表示分佈的可能性函式的物件。 參數和傳回值都必須可以轉換為 `double`。  
  
*right*  
 要與這個項目比較的 `param_type` 物件。  
  
### <a name="remarks"></a>備註  
 這個參數套件可以傳遞至 `operator()` 以產生傳回值。  
  
## <a name="see-also"></a>請參閱  
 [\<random>](../standard-library/random.md)





