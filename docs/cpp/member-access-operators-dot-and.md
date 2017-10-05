---
title: "成員存取運算子:。 和-&gt; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- .
- ->
dev_langs:
- C++
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7c4e69727c474cb89f931832da2dbde6e20c16b9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="member-access-operators--and--gt"></a>成員存取運算子:。 和-&gt;
## <a name="syntax"></a>語法  
  
```  
postfix-expression . name  
postfix-expression -> name  
```  
  
## <a name="remarks"></a>備註  
 成員存取運算子**。** 和** -> **用來參考結構、 等位和類別的成員。 成員存取運算式具有選定成員的值和類型。  
  
 成員存取運算式有兩種形式：  
  
1.  在第一種形式，*後置運算式*代表結構、 類別或等位型別，值和*名稱*指定的結構、 等位或類別的成員命名。 作業的值是*名稱*如果是左值和*後置運算式*是左值。  
  
2.  在第二個表單中，*後置運算式*結構、 等位或類別，代表的指標和*名稱*指定的結構、 等位或類別的成員命名。 值是*名稱*而且是左值。 ** -> **運算子會取值指標。 因此，運算式*e* ** -> ** `member`和**(\****e***)**.`member` (其中*e*代表的指標) 產生相同的結果 (除非運算子** -> **或** \* **經過多載)。  
  
## <a name="example"></a>範例  
 下列範例示範成員存取運算子的兩種形式。  
  
```  
// expre_Selection_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Date {  
   Date(int i, int j, int k) : day(i), month(j), year(k){}  
   int month;  
   int day;  
   int year;  
};  
  
int main() {  
   Date mydate(1,1,1900);  
   mydate.month = 2;     
   cout  << mydate.month << "/" << mydate.day  
         << "/" << mydate.year << endl;  
  
   Date *mydate2 = new Date(1,1,2000);  
   mydate2->month = 2;  
   cout  << mydate2->month << "/" << mydate2->day  
         << "/" << mydate2->year << endl;  
   delete mydate2;  
}  
```  
  
```Output  
2/1/1900  
2/1/2000  
```  
  
## <a name="see-also"></a>另請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [類別和結構](../cpp/classes-and-structs-cpp.md)   
 [結構和等位成員](../c-language/structure-and-union-members.md)
