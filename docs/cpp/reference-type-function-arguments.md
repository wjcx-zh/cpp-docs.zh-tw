---
title: 參考類型函式引數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad8fc85a37aec80d09ed6df9280a78de0540f01
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409053"
---
# <a name="reference-type-function-arguments"></a>參考類型函式引數
通常更有效率的方式是傳遞參考，而不是傳遞大型物件給函式。 這可讓編譯器傳遞物件位址，同時又可維護將用來存取物件的語法。 請考慮下列會使用 `Date` 結構的範例。  
  
```cpp 
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
  
 上述程式碼顯示的傳址方式傳遞的結構成員會使用成員選取運算子存取 (**。**) 而不是指標成員選取運算子 (**->**)。  
  
 雖然傳遞做為參考型別引數會遵守非指標類型的語法，它們會保留指標類型的一項重要特性： 它們是除非宣告為可修改**const**。 由於上述程式碼的目的不是要修改物件 `GDate`，因此更適當的函式原型為：  
  
```cpp 
long JulianFromGregorian( const Date& GDate );  
```  
  
 此原型可確保 `JulianFromGregorian` 函式不會變更其引數。  
  
 任何函式原型都採用參考類型可以接受在其位置相同型別的物件，因為沒有標準轉換轉換*typename*至 * typename ***&**。  
  
## <a name="see-also"></a>另請參閱  
 [參考](../cpp/references-cpp.md)