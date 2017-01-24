---
title: "參考類型函式引數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引數 [C++], 函式"
  - "函式引數, 參考類型"
  - "函式參數, 參考類型"
  - "函式 [C++], 參數"
  - "傳遞參數, 參考類型引數"
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 參考類型函式引數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常更有效率的方式是傳遞參考，而不是傳遞大型物件給函式。  這可讓編譯器傳遞物件位址，同時又可維護將用來存取物件的語法。  請考慮下列會使用 `Date` 結構的範例。  
  
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
  
 上述程式碼中示範了在存取以傳址方式傳遞結構的成員時，是使用成員選取運算子 \(**.**\) 而非指標成員選取運算子 \(**–\>**\)。  
  
 雖然以參考類型傳遞的引數會遵守非指標類型的語法，但它們會保留指標類型的一項重要的特性：若未將引數宣告為 **const**，則可以進行修改。  由於上述程式碼的目的不是要修改物件 `GDate`，因此更適當的函式原型為：  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 此原型可確保 `JulianFromGregorian` 函式不會變更其引數。  
  
 任何採用參考類型的函式原型都可以在該位置接受相同類型的物件，因為其中會進行從 *typename* 到 *typename***&** 的標準轉換。  
  
## 請參閱  
 [參考](../cpp/references-cpp.md)