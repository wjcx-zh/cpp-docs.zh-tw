---
title: 編譯器警告 C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481313"
---
# <a name="compiler-warning-level-4-c4868"></a>編譯器警告 （層級 4） C4868

> '_檔案_(*line_number*)' 編譯器可能不會強制執行括號初始設定式清單中的左到右評估順序

括號初始設定式清單的項目是依照左到右的順序進行評估。 有兩種情況中，編譯器就無法保證此順序： 第一個是當某些項目是以傳值; 的物件第二個會進行編譯時`/clr`和某些項目欄位的物件或陣列元素。 當編譯器無法保證左到右評估它就會發出警告 C4868。

針對 Visual c + + 2015 Update 2 中所進行的編譯器一致性工作，就可以產生這個警告。 Visual c + + 2015 Update 2 之前編譯的程式碼現在可以產生 C4868。

此警告預設為關閉。 使用`/Wall`啟用這項警告。

若要解決這個警告，請先考慮是否有必要，例如當項目評估可能會產生順序有關的副作用進行初始設定式清單項目左到右評估。 在許多情況下，項目都計算的順序並沒有顯著的影響。

如果評估的順序必須是由左到右，請考慮它是否可以將項目傳遞由`const`改為參考。 這類變更會排除下列程式碼範例中的警告。

## <a name="example"></a>範例

此範例會產生 C4868，，並示範如何修正此問題：

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```