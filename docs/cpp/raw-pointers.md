---
title: 原始指標（c + +）
description: 如何在 c + + 中使用原始指標
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- ':::no-loc(void):::'
- ':::no-loc(nullptr):::'
- ':::no-loc(const):::'
- ':::no-loc(char):::'
- ':::no-loc(new):::'
- ':::no-loc(delete):::'
ms.openlocfilehash: 53679559888191fe7f2aad7cb5a70d607974ae96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233648"
---
# <a name="raw-pointers-c"></a>原始指標（c + +）

*指標*是一種變數類型。 它會將物件的位址儲存在記憶體中，並用來存取該物件。 *原始指標*是一種指標，其存留期不是由封裝物件所控制，例如[智慧型指標](smart-pointers-modern-cpp.md)。 原始指標可以被指派另一個非指標變數的位址，或者可以指派的值 [:::no-loc(nullptr):::](:::no-loc(nullptr):::.md) 。 尚未指派值的指標包含亂數據。

指標也*可以被取值*，以抓取它所指向之物件的值。 *成員存取運算子*可讓您存取物件的成員。

```cpp
    int* p = :::no-loc(nullptr):::; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

指標可以指向具類型的物件或 **`:::no-loc(void):::`** 。 當程式在記憶體中的[堆積](https://wikipedia.org/wiki/Heap)上設定物件時，它會以指標的形式接收該物件的位址。 這類指標稱為「*擁有指標*」。 當不再需要所需的堆積設定物件時，必須使用擁有指標（或其複本）來明確釋放該物件。 無法釋放記憶體會導致*記憶體*流失，並將該記憶體位置轉譯為電腦上的任何其他程式無法使用。 使用配置 **`:::no-loc(new):::`** 的記憶體必須使用 **`:::no-loc(delete):::`** （或** :::no-loc(delete)::: \[ ]**）釋放。 如需詳細資訊，請參閱[ :::no-loc(new)::: 和 :::no-loc(delete)::: 運算子](:::no-loc(new):::-and-:::no-loc(delete):::-operators.md)。

```cpp
    MyClass* mc = :::no-loc(new)::: MyClass(); // allocate object on the heap
    mc->print(); // access class member
    :::no-loc(delete)::: mc; // :::no-loc(delete)::: object (please don't forget!)
```

指標（如果未宣告為 **`:::no-loc(const):::`** ）可以遞增或遞減，以指向記憶體中的另一個位置。 這種運算稱為*指標算術*。 它用於 C 樣式的程式設計中，以反復查看陣列或其他資料結構中的元素。 **`:::no-loc(const):::`** 指標無法指向不同的記憶體位置，而且在這個意義上類似于[參考](references-cpp.md)。 如需詳細資訊，請參閱[ :::no-loc(const)::: 和 volatile 指標](:::no-loc(const):::-and-volatile-pointers.md)。

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    :::no-loc(const)::: :::no-loc(char):::* str = "Hello world";

    :::no-loc(const)::: int c = 1;
    :::no-loc(const)::: int* p:::no-loc(const)::: = &c; // declare a non-:::no-loc(const)::: pointer to :::no-loc(const)::: int
    :::no-loc(const)::: int c2 = 2;
    p:::no-loc(const)::: = &c2;  // OK p:::no-loc(const)::: itself isn't :::no-loc(const):::
    :::no-loc(const)::: int* :::no-loc(const)::: p:::no-loc(const):::2 = &c;
    // p:::no-loc(const):::2 = &c2; // Error! p:::no-loc(const):::2 is :::no-loc(const):::.
```

在64位的作業系統上，指標的大小為64位。 系統的指標大小會決定它可以有多少可定址的記憶體。 指標的所有複本都會指向相同的記憶體位置。 指標（連同參考）廣泛用於 c + +，以便在函式之間傳遞更大的物件。 這是因為複製物件的位址通常比複製整個物件更有效率。 定義函式時，請將指標參數指定為， **`:::no-loc(const):::`** 除非您想要函式來修改物件。 一般而言， **`:::no-loc(const):::`** 參考是將物件傳遞給函式的慣用方式，除非物件的值可能是 **`:::no-loc(nullptr):::`** 。

函式的[指標](#pointers_to_functions)可讓函數傳遞至其他函數，並用於 C 樣式程式設計中的「回呼」。 基於此目的，新式 c + + 會使用[lambda 運算式](lambda-expressions-in-cpp.md)。

## <a name="initialization-and-member-access"></a>初始化和成員存取

下列範例顯示如何宣告、初始化和使用原始指標。 它會使用 **`:::no-loc(new):::`** 進行初始化，以指向在堆積上配置的物件，您必須明確地進行此操作 **`:::no-loc(delete):::`** 。 此範例也會顯示與原始指標相關聯的幾個危險。 （請記住，此範例是 C 樣式程式設計，而非現代 c + +！）

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
:::no-loc(void)::: func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
:::no-loc(void)::: func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use :::no-loc(new)::: to allocate and initialize memory
    MyClass* pmc = :::no-loc(new)::: MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    :::no-loc(delete):::(pmc); // don't forget to give memory back to operating system!
   // :::no-loc(delete):::(pmc2); //crash! memory location was already :::no-loc(delete):::d
}
```

## <a name="pointer-arithmetic-and-arrays"></a>指標算術和陣列

指標與陣列密切相關。 當陣列以傳值方式傳遞至函式時，會將它當做第一個元素的指標傳遞。 下列範例示範指標和陣列的下列重要屬性：

- 運算子會傳回 **`sizeof`** 陣列的總大小（以位元組為單位）
- 若要判斷元素的數目，請將總位元組除以一個元素的大小
- 將陣列傳遞至函式時，會*decays*至指標類型
- 套用 **`sizeof`** 至指標時的運算子會傳回指標大小、x86 上的4個位元組或 x64 上的8個位元組

```cpp
#include <iostream>

:::no-loc(void)::: func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

某些算數運算可以用於非 :::no-loc(const)::: 指標，使其指向另一個記憶體位置。 指標會使用 **++** 、 **+=** **-=** 和運算子來遞增和遞減 **--** 。 這項技術可用於陣列中，特別適用于不具類型的資料緩衝區。 會以 **:::no-loc(void):::\*** **`:::no-loc(char):::`** （1個位元組）的大小遞增。 具類型的指標會以其指向的類型大小遞增。

下列範例會示範如何使用指標算術來存取 Windows 點陣圖中的個別圖元。 請注意 and 和取值運算子的用法 **`:::no-loc(new):::`** **`:::no-loc(delete):::`** 。

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    :::no-loc(const):::expr int bufferSize = 30000;
    unsigned :::no-loc(char):::* buffer = :::no-loc(new)::: unsigned :::no-loc(char):::[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned :::no-loc(char):::* begin = &buffer[0];
    unsigned :::no-loc(char):::* end = &buffer[0] + bufferSize;
    unsigned :::no-loc(char):::* p = begin;
    :::no-loc(const):::expr int pixelWidth = 3;
    :::no-loc(const):::expr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned :::no-loc(char):::).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<:::no-loc(char):::*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(&header), sizeof(header));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(begin), bufferSize);

    :::no-loc(delete):::[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="no-locvoid-pointers"></a>:::no-loc(void):::* 指標

**`:::no-loc(void):::`** 僅指向原始記憶體位置的指標。 有時必須使用 **:::no-loc(void):::\*** 指標，例如，在 c + + 程式碼和 c 函式之間傳遞時。

當具類型的指標轉換成 :::no-loc(void)::: 指標時，記憶體位置的內容不會變更。 不過，類型資訊會遺失，因此您無法執行遞增或遞減作業。 記憶體位置可以轉型，例如從轉換成， `MyClass*` **`:::no-loc(void):::*`** 再轉換回 `MyClass*` 。 這類作業原本就很容易出錯，而且需要特別注意 :::no-loc(void)::: 錯誤。 新式 c + + :::no-loc(void)::: 在幾乎所有情況下都不鼓勵使用指標。

```cpp

//func.c
:::no-loc(void)::: func(:::no-loc(void):::* data, int length)
{
    :::no-loc(char):::* c = (:::no-loc(char):::*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    :::no-loc(void)::: func(:::no-loc(void):::* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = :::no-loc(new)::: MyClass{10, "Marian"};
    :::no-loc(void):::* p = static_cast<:::no-loc(void):::*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator :::no-loc(new)::: to allocate untyped memory block
    :::no-loc(void):::* p:::no-loc(void)::: = operator :::no-loc(new):::(1000);
    :::no-loc(char):::* p:::no-loc(char)::: = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::);
    for(:::no-loc(char):::* c = p:::no-loc(char):::; c < p:::no-loc(char)::: + 1000; ++c)
    {
        *c = 0x00;
    }
    func(p:::no-loc(void):::, 1000);
    :::no-loc(char)::: ch = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::)[0];
    std::cout << ch << std::endl; // 'A'
    operator :::no-loc(delete):::(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>函式的指標

在 C 樣式程式設計中，函式指標主要是用來將函式傳遞給其他函數。 這項技術可讓呼叫者自訂函式的行為，而不需要修改函式。 在現代 c + + 中， [lambda 運算式](lambda-expressions-in-cpp.md)提供的功能具有更高的型別安全和其他優點。

函式指標宣告會指定所指向函數必須具有的簽章：

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
:::no-loc(void)::: (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

下列範例會顯示一個函式 `combine` ，該函式會採用接受的任何函式做為參數 `std::string` ，並傳回 `std::string` 。 根據傳遞至的函式 `combine` ，它會在字串前面加上或附加。

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>另請參閱

[智慧型指標](smart-pointers-modern-cpp.md) 
[間接取值運算子： *](indirection-operator-star.md)<br/>
[傳址運算子：&](address-of-operator-amp.md)</br>
[歡迎回到 c + +](welcome-back-to-cpp-modern-cpp.md)
