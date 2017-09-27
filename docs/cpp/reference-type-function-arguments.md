---
title: "參考類型函式引數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters, reference-type
- function arguments, reference-type
- passing parameters, reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 8
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
ms.openlocfilehash: e74cbde44cad618720983fbda4a6cf9ce8b75dc1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="reference-type-function-arguments"></a>參考類型函式引數
通常更有效率的方式是傳遞參考，而不是傳遞大型物件給函式。 這可讓編譯器傳遞物件位址，同時又可維護將用來存取物件的語法。 請考慮下列會使用 `Date` 結構的範例。  
  
```  
// reference_type_function_arguments.cpp  
struct Date  
{  
short DayOfWeek;  
short Month;  
short Day;  
short Year;  
};  
  
// Create a Julian date of the form DDDYYYY  
// from a Gregorian date.  
long JulianFromGregorian( Date& GDate )  
{  
static int cDaysInMonth[] = {  
31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31  
   };  
long JDate = 0;  
// Add in days for months already elapsed.  
for ( int i = 0; i < GDate.Month - 1; ++i )  
JDate += cDaysInMonth[i];  
// Add in days for this month.  
JDate += GDate.Day;  
  
// Check for leap year.  
if ( GDate.Year % 100 != 0 && GDate.Year % 4 == 0 )  
JDate++;  
// Add in year.  
JDate *= 10000;  
JDate += GDate.Year;  
  
return JDate;  
}  
  
int main()  
{  
}  
```  
  
 上述程式碼會顯示參考所傳遞的結構成員會使用成員選取運算子存取 (**。**) 而非指標成員選取運算子 (**->**)。  
  
 雖然傳遞做為參考型別引數會遵守非指標類型的語法，但是它們會保留指標類型的一項重要特性： 它們是宣告為可修改**const**。 由於上述程式碼的目的不是要修改物件 `GDate`，因此更適當的函式原型為：  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 此原型可確保 `JulianFromGregorian` 函式不會變更其引數。  
  
 任何函式原型採用參考類型都可以接受其所在位置相同類型的物件，因為沒有標準轉換轉換*typename*至*typename* ** &**.  
  
## <a name="see-also"></a>另請參閱  
 [參考](../cpp/references-cpp.md)
