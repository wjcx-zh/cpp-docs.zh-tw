---
title: C++ type system
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 1f12f7505438dc995aaf8a045fd903488e9ff092
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246608"
---
# <a name="c-type-system"></a>C++ type system

The concept of *type* is very important in C++. 每個變數、函式引數和函式傳回值都必須有類型才能編譯。 此外，在評估之前，編譯器會以隱含的方式指定每一個運算式 (包括常值) 的類型。 Some examples of types include **int** to store integral values, **double** to store floating-point values (also known as *scalar* data types), or the Standard Library class [std::basic_string](../standard-library/basic-string-class.md) to store text. You can create your own type by defining a **class** or **struct**. 此類型會指定配置給變數 (或運算式結果) 的記憶體數量、可在該變數中存放的值種類、這些值 (位元模式) 的解譯方式，以及可對其執行的作業。 本文包含 C++ 類型系統主要功能的簡略概觀。

## <a name="terminology"></a>用語

**Variable**: The symbolic name of a quantity of data so that the name can be used to access the data it refers to throughout the scope of the code where it is defined. In C++, *variable* is generally used to refer to instances of scalar data types, whereas instances of other types are usually called *objects*.

**Object**: For simplicity and consistency, this article uses the term *object* to refer to any instance of a class or structure, and when it is used in the general sense includes all types, even scalar variables.

**POD type** (plain old data): This informal category of data types in C++ refers to types that are scalar (see the Fundamental types section) or are *POD classes*. POD 類別的靜態資料成員同時也是 POD，沒有使用者定義的建構函式、使用者定義解構函式或使用者定義的指派運算子。 此外，POD 類別沒有虛擬函式、沒有基底類別，也沒有私用或受保護的非靜態資料成員。 POD 類型通常用於外部資料交換，例如以 C 語言撰寫的模組 (其中只有 POD 類型)。

## <a name="specifying-variable-and-function-types"></a>指定變數和函式類型

C++ is a *strongly typed* language and it is also *statically-typed*; every object has a type and that type never changes (not to be confused with static data objects).
**When you declare a variable** in your code, you must either specify its type explicitly, or use the **auto** keyword to instruct the compiler to deduce the type from the initializer.
**When you declare a function** in your code, you must specify the type of each argument and its return value, or **void** if no value is returned by the function. 例外情況是在您使用函式樣板，可允許任意類型的引數。

在您初次宣告變數之後，就不能再變更其類型。 不過，您可以將變數值或函式的傳回值複製到另一個不同類型的變數。 Such operations are called *type conversions*, which are sometimes necessary but are also potential sources of data loss or incorrectness.

當您宣告 POD 類型的變數時，強烈建議您將其初始化，也就是指定其初始值。 在您初始化變數以前，變數都會包含由先前遺留在該記憶體位置之任何位元所構成的「垃圾」值。 這是一個要記住的 C++ 重要層面，如果您是從另一個用來處理初始化的語言轉換而來時則更是如此。 宣告非 POD 類別類型的變數時，建構函式會處理初始化。

下列範例示範一些簡單的變數宣告，這些宣告各有一些描述。 這個範例也會示範編譯器如何使用類型資訊允許或不允許對變數進行某些後續作業。

```cpp
int result = 0;              // Declare and initialize an integer.
double coefficient = 10.8;   // Declare and initialize a floating
                             // point value.
auto name = "Lady G.";       // Declare a variable and let compiler
                             // deduce the type.
auto address;                // error. Compiler cannot deduce a type
                             // without an intializing value.
age = 12;                    // error. Variable declaration must
                             // specify a type or use auto!
result = "Kenny G.";         // error. Can’t assign text to an int.
string result = "zero";      // error. Can’t redefine a variable with
                             // new type.
int maxValue;                // Not recommended! maxValue contains
                             // garbage bits until it is initialized.
```

## <a name="fundamental-built-in-types"></a>基本 (內建) 類型

有別於某些程式語言，C++ 並沒有可衍生出所有其他類型的通用基底類型。 The language includes many *fundamental types*, also known as *built-in types*. This includes numeric types such as **int**, **double**, **long**, **bool**, plus the **char** and **wchar_t** types for ASCII and UNICODE characters, respectively. Most fundamental types (except **bool**, **double**, **wchar_t** and related types) all have unsigned versions, which modify the range of values that the variable can store. For example, an **int**, which stores a 32-bit signed integer, can represent a value from -2,147,483,648 to 2,147,483,647. An **unsigned int**, which is also stored as 32-bits, can store a value from 0 to 4,294,967,295. 每個案例中的可能值總數都相同；只有範圍不同。

基本類型是由編譯器辨識，其內建規則會控制可對這些類型執行哪些作業，以及如何轉換成其他基本類型。 For a complete list of built-in types and their size and numeric limits, see [Fundamental Types](../cpp/fundamental-types-cpp.md).

下圖顯示內建類型的相對大小：

![Size in bytes of built&#45;in types](../cpp/media/built-intypesizes.png "Size in bytes of built&#45;in types")

下表列出最常用的基本類型：

|輸入|大小|註解|
|----------|----------|-------------|
|int|4 個位元組|整數值的預設選項。|
|雙線|8 個位元組|浮點值的預設選項。|
|bool|1 個位元組|表示可以是 true 或 false 的值。|
|char|1 個位元組|使用較舊 C-Style 字串或 std::string 物件中永遠不需要轉換成 UNICODE 之的 ASCII 字元。|
|wchar_t|2 個位元組|表示可能以 UNICODE 格式 (在 Windows 上為 UTF-16，而其他作業系統可能不同) 編碼的「寬」字元值。 這是用於 `std::wstring` 類型字串的字元類型。|
|unsigned&nbsp;char|1 個位元組|C++ 沒有內建 `byte` 類型。  使用 unsigned char 表示位元組值。|
|unsigned int|4 個位元組|位元旗標的預設選項。|
|long long|8 個位元組|表示極大的整數值。|

## <a name="the-void-type"></a>void 類型

The **void** type is a special type; you cannot declare a variable of type **void**, but you can declare a variable of type __void \*__ (pointer to **void**), which is sometimes necessary when allocating raw (un-typed) memory. However, pointers to **void** are not type-safe and generally their use is strongly discouraged in modern C++. In a function declaration, a **void** return value means that the function does not return a value; this is a common and acceptable use of **void**. While the C language required functions that have zero parameters to declare **void** in the parameter list, for example, `fou(void)`, this practice is discouraged in modern C++ and should be declared `fou()`. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>常數類型限定詞

任何內建或使用者定義的類型都可以由 const 關鍵字限定。 Additionally, member functions may be **const**-qualified and even **const**-overloaded. The value of a **const** type cannot be modified after it is initialized.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

The **const** qualifier is used extensively in function and variable declarations and "const correctness" is an important concept in C++; essentially it means to use **const** to guarantee, at compile time, that values are not modified unintentionally. For more information, see [const](../cpp/const-cpp.md).

A **const** type is distinct from its non-const version; for example, **const int** is a distinct type from **int**. You can use the C++ **const_cast** operator on those rare occasions when you must remove *const-ness* from a variable. For more information, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>字串類型

Strictly speaking, the C++ language has no built-in string type; **char** and **wchar_t** store single characters - you must declare an array of these types to approximate a string, adding a terminating null value (for example, ASCII `'\0'`) to the array element one past the last valid character (also called a *C-style string*). C-Style 字串需要撰寫更多程式碼或使用外部字串公用程式庫函式。 But in modern C++, we have the Standard Library types `std::string` (for 8-bit **char**-type character strings) or `std::wstring` (for 16-bit **wchar_t**-type character strings). These C++ Standard Library containers can be thought of as native string types because they are part of the standard libraries that are included in any compliant C++ build environment. 只要使用 `#include <string>` 指示詞，即可在您的程式中使用這些類型。 (If you are using MFC or ATL, the CString class is also available, but is not part of the C++ standard.) The use of null-terminated character arrays (the C-style strings previously mentioned) is strongly discouraged in modern C++.

## <a name="user-defined-types"></a>使用者定義類型

When you define a **class**, **struct**, **union**, or **enum**, that construct is used in the rest of your code as if it were a fundamental type. 它在記憶體中的大小已知，而且套用了有關其在編譯時間檢查、執行階段和程式存留期之使用方式的特定規則。 基本內建類型和使用者定義類型之間的主要差異如下：

- 編譯器沒有使用者定義類型的內建知識。 It learns of the type when it first encounters the definition during the compilation process.

- 您會藉由定義 (透過多載) 適當的運算子做為類別成員或非成員函式，指定對類型執行哪些作業，以及如何轉換為其他類型。 For more information, see [Function Overloading](function-overloading.md)

## <a name="pointer-types"></a>指標類型

在 C 語言的最早期版本中，C++ 繼續讓您使用特殊宣告子 `*` (星號) 宣告指標類型的變數。 指標類型會將在儲存實際資料值之位置的位址儲存在記憶體中。 In modern C++, these are referred to as *raw pointers*, and are accessed in your code through special operators `*` (asterisk) or `->` (dash with greater-than). This is called *dereferencing*, and which one that you use depends on whether you are dereferencing a pointer to a scalar or a pointer to a member in an object. 處理指標類型一直以來都是 C 及 C++ 程式開發最具挑戰性和令人困惑的一面。 This section outlines some facts and practices to help use raw pointers if you want to, but in modern C++ it’s no longer required (or recommended) to use raw pointers for object ownership at all, due to the evolution of the [smart pointer](../cpp/smart-pointers-modern-cpp.md) (discussed more at the end of this section). 使用原始指標觀察物件仍然有用且安全，但若要將其用於物件擁有權，就必須小心使用，並非常仔細地考量如何建立和終結所擁有的物件。

您首先應該知道的事就是，宣告原始指標變數時只會配置，在儲存該指標在被取值時所參考之記憶體位置位址時所需的記憶體。 Allocation of the memory for the data value itself (also called *backing store*) is not yet allocated. 換句話說，宣告原始指標變數，即是在建立記憶體位址變數，而不是實際資料變數。 在確定變數包含可用於備份存放區的有效位址之前就先取值指標變數，會導致程式中產生未定義的行為 (通常是嚴重錯誤)。 下列範例示範這種錯誤：

```cpp
int* pNumber;       // Declare a pointer-to-int variable.
*pNumber = 10;      // error. Although this may compile, it is
                    // a serious error. We are dereferencing an
                    // uninitialized pointer variable with no
                    // allocated memory to point to.
```

這個範例會對指標類型取值，但不配置任何記憶體的來儲存指派給它的實際整數資料或有效記憶體位址。 下列程式碼示範這些錯誤：

```cpp
    int number = 10;          // Declare and initialize a local integer
                              // variable for data backing store.
    int* pNumber = &number;   // Declare and initialize a local integer
                              // pointer variable to a valid memory
                              // address to that backing store.
...
    *pNumber = 41;            // Dereference and store a new value in
                              // the memory pointed to by
                              // pNumber, the integer variable called
                              // "number". Note "number" was changed, not
                              // "pNumber".
```

更正的程式碼範例會使用本機堆疊記憶體，建立 `pNumber` 所指向的備份存放區。 我們為了簡單起見使用基本類型。 In practice, the backing store for pointers are most often user-defined types that are dynamically-allocated in an area of memory called the *heap* (or *free store*) by using a **new** keyword expression (in C-style programming, the older `malloc()` C runtime library function was used). Once allocated, these variables are usually referred to as objects, especially if they are based on a class definition. Memory that is allocated with **new** must be deleted by a corresponding **delete** statement (or, if you used the `malloc()` function to allocate it, the C runtime function `free()`).

However, it is easy to forget to delete a dynamically-allocated object- especially in complex code, which causes a resource bug called a *memory leak*. 因此，強烈建議您不要在現代 C++ 使用原始指標。 It is almost always better to wrap a raw pointer in a [smart pointer](../cpp/smart-pointers-modern-cpp.md), which will automatically release the memory when its destructor is invoked (when the code goes out of scope for the smart pointer); by using smart pointers you virtually eliminate a whole class of bugs in your C++ programs. 下列範例中，假設 `MyClass` 是具有公用方法 `DoSomeWork();` 的使用者定義類型

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

For more information about smart pointers, see [Smart Pointers](../cpp/smart-pointers-modern-cpp.md).

For more information about pointer conversions, see [Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md).

For more information about pointers in general, see [Pointers](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Windows 資料類型

在 C 和 C++ 的傳統 Win32 程式設計中，大部分函式會使用 Windows 專有的 typedef 和 #define 巨集 (定義於 `windef.h`) 來指定參數和傳回值的類型。 These Windows data types are mostly just special names (aliases) given to C/C++ built-in types. For a complete list of these typedefs and preprocessor definitions, see [Windows Data Types](/windows/win32/WinProg/windows-data-types). 這些 Typedef (例如 HRESULT 和 LCID) 很有用而且是描述性的。 其他如 INT，並無特殊意義，只是基本 C++ 類型的別名而已。 其他 Windows 資料類型有從 C 程式設計和 16 位元處理器時代保留下來的名稱，在現代硬體或作業系統上並無用處或意義。 There are also special data types associated with the Windows Runtime Library, listed as [Windows Runtime base data types](/windows/win32/WinRT/base-data-types). 在現代 C++ 中，一般的方針就是，除非 Windows 類型傳達有關如何解譯值的額外涵義，否則優先使用 C++ 基本類型。

## <a name="more-information"></a>更多資訊

如需 C++ 類型系統的詳細資訊，請參閱下列主題：

|||
|-|-|
|[實值型別](../cpp/value-types-modern-cpp.md)|Describes *value types* along with issues relating to their use.|
|[Type Conversions and Type Safety](../cpp/type-conversions-and-type-safety-modern-cpp.md)|描述一般類型轉換問題並顯示如何避免這些問題。|

## <a name="see-also"></a>請參閱

[Welcome back to C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
