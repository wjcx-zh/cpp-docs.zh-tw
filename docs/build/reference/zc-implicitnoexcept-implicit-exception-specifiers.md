---
title: "/Zc:implicitNoexcept (隱含的例外狀況規範) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:implicitNoexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc:implicitNoexcept"
  - "Zc:implicitNoexcept"
  - "-Zc:implicitNoexcept"
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:implicitNoexcept (隱含的例外狀況規範)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當指定 **\/Zc:implicitNoexcept** 選項時，編譯器會將隱含的 [noexcept](../../cpp/noexcept-cpp.md) 例外狀況規範加入至編譯器定義的特殊成員函式，以及加入至使用者定義的解構函式和解除配置器。  根據預設，會啟用 **\/Zc:implicitNoexcept** 以符合 ISO C \+ \+ 11 標準。  關閉此選項會在使用者定義的解構函式和解除配置器，以及編譯器定義的特殊成員函式上停用隱含的 `noexcept`。  
  
## 語法  
  
```vb  
/Zc:implicitNoexcept[-]  
```  
  
#### 參數  
  
## 備註  
 根據預設，如果指定 **\/Zc:implicitNoexcept**，則編譯器會遵循 ISO C \+ \+ 11 標準的第 15.4 節，並隱含地將 `noexcept` 例外狀況規範加入至每個隱含宣告或明確宣告的預設特殊成員函式—預設建構函式、複製建構函式、移動建構函式、解構函式、複製指派運算子或移動指派運算子—以及每個使用者定義的解構函式或解除配置器函式。  使用者定義的解除配置器具有隱含的 `noexcept(true)` 例外狀況規範。  若為使用者定義的解構函式，隱含的例外狀況規範為 `noexcept(true)`，除非內含的成員類別或基底類別具有不是 `noexcept(true)` 的解構函式。  若為編譯器產生的特殊成員函式，如果此函式直接叫用的任何函式實際上就是 `noexcept(false)`，則隱含的例外狀況規範為 `noexcept(false)`。  否則，隱含的例外狀況規範為 `noexcept(true)`。  
  
 編譯器不會為使用明確的 `noexcept` 或 `throw` 規範或 `__declspec(nothrow)` 屬性所宣告的函式產生隱含的例外狀況規範。  
  
 如果已藉由指定 **\/Zc:implicitNoexcept\-** 停用規範，則編譯器不會產生任何隱含的例外狀況規範。  這種行為與 Visual Studio 2013 相同，其中沒有例外狀況規範的解構函式和解除配置器可能具有 `throw` 陳述式。  根據預設，以及當指定 **\/Zc:implicitNoexcept** 時，如果在執行階段於具有隱含 `noexcept(true)` 規範的函式中遇到 `throw` 陳述式，則它會導致立即叫用 `std::terminate`,，而且不保證例外狀況處理常式的正常回溯行為。  若要協助識別這種情況，編譯器會產生 [編譯器警告 \(層級 1\) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。  如果 `throw` 是刻意的，我們建議您變更您的函式宣告，以具有明確的 `noexcept(false)` 規範，而不使用 **\/Zc:implicitNoexcept\-**。  
  
 這個範例會顯示當設定或停用 **\/Zc:implicitNoexcept** 選項時，沒有明確例外狀況規範的使用者定義的解構函式如何運作。  若要顯示設定時的行為，請使用 `cl /EHsc /W4 implicitNoexcept.cpp` 來編譯。  若要顯示停用時的行為，請使用 `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` 來編譯。  
  
```  
// implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp  
  
#include <iostream>  
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS  
#include <exception>    // for std::set_terminate  
  
void my_terminate()  
{  
    std::cout << "Unexpected throw caused std::terminate" << std::endl;  
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;  
    std::exit(EXIT_FAILURE);  
}  
  
struct A {  
    // Explicit noexcept overrides implicit exception specification  
    ~A() noexcept(false) {  
        throw 1;  
    }  
};  
  
struct B : public A {  
    // Compiler-generated ~B() definition inherits noexcept(false)  
    ~B() = default;  
};  
  
struct C {  
    // By default, the compiler generates an implicit noexcept(true)  
    // specifier for this user-defined destructor. To enable it to  
    // throw an exception, use an explicit noexcept(false) specifier,  
    // or compile by using /Zc:implicitNoexcept-  
    ~C() {    
        throw 1; // C4297, calls std::terminate() at run time  
    }  
};  
  
struct D : public C {  
    // This destructor gets the implicit specifier of its base.  
    ~D() = default;  
};  
  
int main()  
{  
    std::set_terminate(my_terminate);  
  
    try  
    {  
        {  
            B b;   
        }  
    }  
    catch (...)  
    {  
        // exception should reach here in all cases  
        std::cout << "~B Exception caught" << std::endl;  
    }  
    try  
    {  
        {  
            D d;  
        }  
    }  
    catch (...)  
    {  
        // exception should not reach here if /Zc:implicitNoexcept  
        std::cout << "~D Exception caught" << std::endl;  
    }  
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;  
    return EXIT_SUCCESS;  
}  
  
```  
  
 使用預設設定 **\/Zc:implicitNoexcept** 來編譯時，範例會產生以下輸出：  
  
  **~B 攔截到例外狀況**  
**非預期的 throw 造成 std::terminate**  
**傳回 EXIT\_FAILURE 時結束** 使用設定 **\/Zc:implicitNoexcept\-** 來編譯時，範例會產生以下輸出：  
  
  **~B 攔截到例外狀況**  
**~D 攔截到例外狀況**  
**傳回 EXIT\_SUCCESS 時結束** 如需 Visual C\+\+ 中一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[**其他選項**\] 內容，以包含 **\/Zc:implicitNoexcept** 或 **\/Zc:implicitNoexcept\-**，然後選擇 \[**確定**\]。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)   
 [noexcept](../../cpp/noexcept-cpp.md)   
 [例外狀況規格 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)   
 [terminate](../Topic/terminate%20\(%3Cexception%3E\).md)