---
title: 原始指標（C++）
description: 如何在中使用原始指標C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 9ea498c254bc37dc8dc550232127cb2db3bc0886
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250657"
---
# <a name="raw-pointers-c"></a>原始指標（C++）

指標是一種變數類型，可將物件的位址儲存在記憶體中，並用來存取該物件。 *原始指標*是一種指標，其存留期不是由封裝物件（例如[智慧型指標](smart-pointers-modern-cpp.md)）所控制。 原始指標可以被指派另一個非指標變數的位址，或者可以指派值[nullptr](nullptr.md)。 尚未指派值的指標包含亂數據。

指標也*可以被取值*，以抓取它所指向之物件的值。 *成員存取運算子*可讓您存取物件的成員。

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

指標可以指向具類型的物件或**void**。 當程式在記憶體中的[堆積](https://wikipedia.org/wiki/Heap)上配置新的物件時，它會以指標的形式接收該物件的位址。 這類指標稱為「*擁有指標*」;當不再需要堆積配置的物件時，必須使用擁有指標（或其複本）明確地刪除該物件。 無法刪除記憶體會導致*記憶體*流失，並將該記憶體位置轉譯為電腦上的任何其他程式無法使用。 如需詳細資訊，請參閱[new 和 delete 運算子](new-and-delete-operators.md)。

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

指標（如果未宣告為**const**）可以遞增或遞減，使其指向記憶體中的新位置。 這稱為*指標算術*，用於 C 樣式的程式設計中，以反復查看陣列或其他資料結構中的元素。 **Const**指標無法指向不同的記憶體位置，而且在這個意義上與[參考](references-cpp.md)非常類似。 如需詳細資訊，請參閱[const 和 volatile 指標](const-and-volatile-pointers.md)。

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c; 
    // pconst2 = &c2; // Error! pconst2 is const.
```

在64位作業系統上，指標的大小為64位;系統的指標大小會決定它可以有多少可定址的記憶體。 指標的所有複本都會指向相同的記憶體位置。 指標（連同參考）廣泛用於，以便在C++函式之間傳遞更大的物件，因為複製物件的64位位址通常會比複製整個物件更有效率。 定義函式時，除非您想要讓函數修改物件，否則請將指標參數指定為**const** 。 一般來說，除非物件的值可能是**nullptr**，否則**常數**參考是將物件傳遞至函式的慣用方式。

函式的[指標](#pointers_to_functions)可讓函數傳遞至其他函數，並用於 C 樣式程式設計中的「回呼」。 基於C++此目的，新式使用[lambda 運算式](lambda-expressions-in-cpp.md)。

## <a name="initialization-and-member-access"></a>初始化和成員存取

下列範例示範如何宣告原始指標，並使用在堆積上配置的物件加以初始化，以及如何使用它。 它也會顯示一些與原始指標相關聯的危險。 （請記住，這是 C 樣式的程式設計， C++而不是新式！）

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
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
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

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
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>指標算術和陣列

指標與陣列密切相關。 當陣列以傳值方式傳遞至函式時，會將它當做第一個元素的指標傳遞。 下列範例示範指標和陣列的下列重要屬性：

- `sizeof` 運算子會傳回陣列的總大小（以位元組為單位）
- 若要判斷元素的數目，請將總位元組除以一個元素的大小
- 將陣列傳遞至函式時，會*decays*至指標類型
- 套用至指標時的 `sizeof` 運算子會傳回指標大小、x86 上的4個位元組或 x64 上的8位元組

```cpp
#include <iostream>

void func(int arr[], int length)
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

某些算數運算可以在非 const 指標上執行，使其指向新的記憶體位置。 您可以使用 **++** 、 **+=** 、 **-=** 和 **--** 運算子來遞增和遞減指標。 這項技術可用於陣列中，特別適用于不具類型的資料緩衝區。 **Void\*** 以**char** （1位元組）的大小遞增。 具類型的指標會依其所指向之類型的大小遞增。

下列範例會示範如何使用指標算術來存取 Windows 點陣圖中的個別圖元。 請注意**new**和**delete**和取值運算子的用法。 

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

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

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
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>void * 指標

**Void**的指標只會指向原始記憶體位置。 有時候，必須使用**void\*** 指標，例如，在程式碼和 C C++函式之間傳遞時。 

當具類型的指標轉換成 void 指標時，記憶體位置的內容不會變更，但類型資訊會遺失，因此您無法執行遞增或遞減作業。 記憶體位置可以轉型，例如，從 MyClass * 到 void *，再轉換成 MyClass *。 這類作業原本就很容易發生錯誤，而且需要非常小心地避免錯誤。 除非C++絕對必要，新式不鼓勵使用 void 指標。

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

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
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers_to_functions"></a>函式的指標

在 C 樣式程式設計中，函式指標主要是用來將函式傳遞給其他函數。 在此案例中，呼叫端可以自訂函式的行為，而不需要修改函式。 在現代C++的中， [lambda 運算式](lambda-expressions-in-cpp.md)提供的功能具有更高的型別安全和其他優點。

函式指標宣告會指定所指向函數必須具有的簽章：

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

下列範例顯示的函式 `combine` 會接受 `std::string` 的任何函式，並傳回 `std::string`。 視傳遞至 `combine` 的函式而定，它會在前面加上或附加字串。

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
[歡迎回到C++](welcome-back-to-cpp-modern-cpp.md)
