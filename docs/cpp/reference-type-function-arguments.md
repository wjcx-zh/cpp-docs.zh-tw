---
title: 參考類型函式引數
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], parameters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: 5a409efbe2908954d394656cb989ad6b80a9ce22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233635"
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

上述程式碼顯示使用成員選取運算子（**.**）而非指標成員選取運算子（）存取以傳址方式傳遞之結構的成員 **->** 。

雖然當做參考型別傳遞的引數會觀察到非指標類型的語法，但它們會保留指標類型的一個重要特性：除非宣告為，否則它們是可修改的 **`const`** 。 由於上述程式碼的目的不是要修改物件 `date`，因此更適當的函式原型為：

```cpp
long DateOfYear( const Date& date );
```

此原型可確保 `DateOfYear` 函式不會變更其引數。

任何採用參考型別的函式原型都可以接受其位置中相同類型的物件，因為從*typename*到*typename*的標準轉換 <strong>&</strong> 。

## <a name="see-also"></a>另請參閱

[參考](../cpp/references-cpp.md)<br/>
