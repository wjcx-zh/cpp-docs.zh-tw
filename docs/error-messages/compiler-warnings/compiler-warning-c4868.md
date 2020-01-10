---
title: 編譯器警告 C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: c1d49eb61a5c7c47fa83dacb39ed50f42e0fb147
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810488"
---
# <a name="compiler-warning-level-4-c4868"></a>編譯器警告（層級4） C4868

> '_file_（*line_number*） ' 編譯器可能不會在括弧初始化運算式清單中強制執行由左至右的評估順序

括弧初始化運算式清單的元素是以由左至右順序評估。 在兩種情況下，編譯器無法保證此順序：第一種是當某些元素是以傳值方式傳遞的物件時。第二個是使用 `/clr` 進行編譯，而某些專案是物件的欄位，或為陣列元素。 當編譯器無法保證由左至右的評估時，它會發出警告 C4868。

針對 Visual Studio 2015 Update 2 所進行的編譯器一致性工作，可能會產生此警告。 在 Visual Studio 2015 Update 2 之前編譯的程式碼現在可以產生 C4868。

此警告預設為關閉。 請使用 `/Wall` 來啟動此警告。

若要解決這個警告，請先考慮是否需要初始化運算式清單元素的由左至右評估，例如當專案的評估可能會產生與順序相關的副作用時。 在許多情況下，評估專案的順序並不會有可觀察的效果。

如果評估的順序必須由左至右，請考慮是否能夠改為以 `const` 參考的方式傳遞元素。 這類變更會消除下列程式碼範例中的警告。

## <a name="example"></a>範例

這個範例會產生 C4868，並顯示可修正此問題的方法：

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