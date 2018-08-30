---
title: 參考類型函式引數 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
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
ms.openlocfilehash: 042f609988a87beb8a990405e0426405bc874128
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209747"
---
# <a name="reference-type-function-arguments"></a>參考類型函式引數

通常更有效率的方式是傳遞參考，而不是傳遞大型物件給函式。 這可讓編譯器傳遞物件位址，同時又可維護將用來存取物件的語法。 請考慮下列會使用 `Date` 結構的範例。

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

上述程式碼顯示的傳址方式傳遞的結構成員會使用成員選取運算子存取 (**。**) 而不是指標成員選取運算子 (**->**)。

雖然傳遞做為參考型別引數會遵守非指標類型的語法，它們會保留指標類型的一項重要特性： 它們是除非宣告為可修改**const**。 由於上述程式碼的目的不是要修改物件 `date`，因此更適當的函式原型為：

```cpp
long DateOfYear( const Date& date );
```

此原型可確保 `DateOfYear` 函式不會變更其引數。

任何函式原型都採用參考類型可以接受在其位置相同型別的物件，因為沒有標準轉換轉換*typename*要*typename*  <strong>&</strong>.

## <a name="see-also"></a>另請參閱

[參考](../cpp/references-cpp.md)<br/>
