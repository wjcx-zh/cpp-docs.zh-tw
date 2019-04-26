---
title: 在沒有建構函式的情況下初始化類別和結構 (C++)
ms.date: 10/17/2018
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4f696f4fc8862b953e40a03c96b88d1a0b7f720b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183410"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>在沒有建構函式的情況下初始化類別和結構 (C++)

您不一定需要定義類別的建構函式，尤其是相當簡單的類別。 使用者可以使用統一初始化來初始化類別或結構的物件 (如下列範例所示)：

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

請注意，當類別或結構有沒有建構函式，但您提供清單中的項目類別中宣告的成員的順序。 如果類別具有建構函式，提供依參數順序的項目。

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
[建構函式](../cpp/constructors-cpp.md)
