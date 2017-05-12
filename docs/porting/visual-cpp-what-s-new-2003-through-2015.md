---
title: "從 2003 到 2015 的 Visual C++ 新功能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c6ac9fb7400bd0c37d1da5a0c6bd66ccbf7abd6c
ms.lasthandoff: 02/24/2017

---
# <a name="visual-c-what39s-new-2003-through-2015"></a>從 2003 到 2015 的 Visual C++ 新功能

**注意**：如需 Visual Studio 2017 的相關資訊，請參閱 [Visual Studio 2017 中的 Visual C++ 新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)和[Visual Studio 2017 中的 C++ 一致性改善](../cpp-conformance-improvements-2017.md)。

在 Visual C++ 2015 和更新版本中，隨著不斷地改善編譯器一致性，有時可能會變更編譯器解讀您現有原始程式碼的方式。 當發生這種情況時，可能會在您建置時發生不同或新的錯誤，甚至程式碼的行為與先前所建置的不同，而且看似正常運作。  
  
 所幸這些差異對於您大部分的原始程式碼影響很小，甚至完全沒有影響。即使有需要變更原始程式碼或進行其他變更才能解決這些差異，這類修正通常很少而且簡單明瞭。 我們加入了許多先前接受，但後來可能需要變更的原始程式碼範例 *(之前)*，以及用以更正的修正 *(之後)*。  
  
 雖然這些差異可脦會影響您的原始程式碼或其他組建成品，但不會影響每版 Visual C++ 更新之間的二進位相容性。 「重大變更」是較重大的變更類型，會影響二進位檔相容性，但這些類型的二進位相容性只會在 Visual C++ 的主要版本之間中斷。 例如，Visual C++ 2013 與 Visual C++ 2015 之間。 如需 Visual C++ 2013 與 Visual C++ 2015 之間的重大變更資訊，請參閱 [Visual C++ 變更歷程記錄 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)。  
  
-   [Visual C++ 2015 中的一致性改善](#VS_RTM)  
  
-   [Update 1 的合規性改進](#VS_Update1)  
  
-   [Update 2 的合規性改進](#VS_Update2)  
  
-   [Update 3 的合規性改進](#VS_Update3)  
  
##  <a name="VS_RTM"></a> Visual C++ 2015 的合規性改進  
  
-   /Zc:forScope- 選項  
  
     編譯器選項 **/Zc:forScope-** 已被取代，在未來的發行版本中將會移除  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     該選項通常是在非標準程式碼的迴圈變數應該已經超出範圍 (根據該標準) 之後，用來允許此非標準程式碼。 只有當您使用 /Za 選項編譯時才需要這樣做，因為在沒有指定 /Za 的情況下，總是允許在迴圈結束之後使用 for 迴圈變數。 如果您不在意標準一致性 (例如，如果您並沒有打算將程式碼設計成可移植到其他編譯器)，則可以關閉 /Za 選項 (或將停用語言擴充功能屬性設為 No)。 如果您在意撰寫可攜式且符合標準規範的程式碼，就應該要重寫程式碼，將這類變數的宣告移至該迴圈外，使其符合此標準。  
  
    ```  
    // zc_forScope.cpp  
    // compile with: /Zc:forScope- /Za  
    // C2065 expected  
    int main() {  
       // Uncomment the following line to resolve.  
       // int i;  
       for (int i =0; i < 1; i++)  
          ;  
       i = 20;   // i has already gone out of scope under /Za  
    }  
    ```  
  
-   **/Zg 編譯器選項**  
  
     /Zg 編譯器選項 (產生函式原型) 不再提供使用。 這個編譯器選項之前已遭取代。  
  
-   您再也無法從命令列藉由 mstest.exe 使用 C++ /CLI 來執行單元測試。 請改用 vstest.console.exe。 請參閱 [VSTest.Console.exe 命令列選項](/devops-test-docs/test/vstest-console-exe-command-line-options)。  
  
-   **可變動的關鍵字**  
  
     在之前 `mutable` 儲存類別規範可以正確無誤編譯的位置中，已再也無法允許此儲存類別規範。 現在，此編譯器會發生錯誤 C2071 (不合法的儲存類別)。 根據該標準，可變動的規範只可以套用至類別資料成員的名稱，而不能套用至宣告為常數或靜態的名稱，也不能套用至參考的成員。  
  
     例如，請參考下列程式碼：  
  
    ```  
    struct S {  
        mutable int &r;  
    };  
    ```  
  
     舊版的 Visual C++ 編譯器可接受這種做法，但現在該編譯器會產生下列錯誤：  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     若要修正此錯誤，只需移除多餘的可變動關鍵字。  
  
-   **char_16_t 與 char32_t**  
  
     您再也無法使用 `char16_t` 或 `char32_t` 做為 typedef 的別名，因為現在會將這些類型視為內建類型。 對於使用者和程式庫作者來說，將 char16_t 和 char32_t 分別定義為 uint16_t 和 uint32_t 的別名是很常見的做法。  
  
    ```  
    #include <cstdint>  
  
    typedef uint16_t char16_t; //C2628  
    typedef uint32_t char32_t; //C2628  
  
    int main(int argc, char* argv[])  
    {  
    uint16_t x = 1; uint32_t y = 2;  
    char16_t a = x;   
    char32_t b = y;   
    return 0;  
    }  
    ```  
  
     若要更新您的程式碼，請移除此 typedef 宣告，重新命名與這些名稱衝突的任何其他識別項。  
  
-   **非類型範本參數**  
  
     在您提供明確的樣板引數之際，和非類型樣板參數有關的特定程式碼之類型相容性檢查即為正確。 例如，下列程式碼可在舊版的 Visual C++ 中正確無誤地編譯。  
  
    ```  
    struct S1  
    {  
    void f(int);  
    void f(int, int);  
    };  
  
    struct S2  
    {  
    template <class C, void (C::*Function)(int) const> void f() {}  
    };  
  
    void f()  
    {  
    S2 s2;  
    s2.f<S1, &S1::f>();  
    }  
  
    ```  
  
     在目前的編譯器中，按照常理則會發生錯誤，因為該樣板參數類型與樣板引數不相符 (該參數是指向常數成員的指標，但該函式 f 卻是非常數函式)：  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     若要解決程式碼中的這個錯誤，請確定您使用的樣板引數的類型與此樣板參數的宣告類型相符。  
  
-   **__declspec(align)**  
  
     該編譯器已不再接受函式上的 `__declspec(align)` 。 之前的編譯器一律將它忽略，但現在會產生編譯器錯誤。  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     若要修正這個問題，請從此函式宣告中移除 `__declspec(align)` 。 因為它沒有任何作用，移除它並不會變更任何項目。  
  
-   **例外狀況處理**  
  
     有幾個例外狀況處理的變更。 首先，例外狀況物件必須可複製或可移動。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中編譯，但無法在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中編譯：  
  
    ```  
    struct S {  
    public:  
        S();  
    private:  
        S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     問題是出在於此複製建構函式是私用的，無法如同處理例外狀況的正常過程中發生的物件一樣複製，因此並不能複製該物件。 相同情況也發生在宣告複製建構函式為 `explicit`的時候。  
  
    ```  
    struct S {  
        S();  
        explicit S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     若要更新您的程式碼，請確定例外狀況物件的複製建構函式是公用的，而且不是標示為 `explicit`。  
  
     以傳值方式攔截例外狀況也需要可複製的例外狀況物件。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中編譯，但無法在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中編譯：  
  
    ```  
    struct B {  
    public:  
        B();  
    private:  
        B(const B &);  
    };  
  
    struct D : public B {  
    };  
  
    int main()  
    {  
        try  
        {  
        }  
        catch (D d) // error  
        {  
        }  
    }  
  
    ```  
  
     您可以藉由變更 `catch` 的參數類型為參考來修正此問題。  
  
    ```  
    catch(D& d)  
    {  
    }  
    ```  
  
-   **後接巨集的字串常值**  
  
     該編譯器現在支援使用者定義常值。 因此，會將後面接著巨集且不含任何中間空白字元的字串常值解譯為使用者定義常值，這可能會產生錯誤或非預期的結果。 例如，在舊版編譯器中，下列程式碼可順利編譯：  
  
    ```  
    #define _x "there"  
    char* func() {  
        return "hello"_x;  
    }  
    int main()  
    {  
        char * p = func();  
        return 0;  
    }  
    ```  
  
     該編譯器會將其解譯為後面接著巨集的字串常值 "hello"，並且將該巨集展開成 "there"，然後再將這兩個字串常值串連成一個。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，編譯器會將它解譯為使用者定義的常值，但是因為沒有定義相符的使用者定義常值 _x，所以會產生錯誤。  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     若要修正這個問題，請在此字串常值和巨集之間加入空格。  
  
-   **相鄰字串常值**  
  
     如同前面所述，因為字串剖析時相關變更的緣故，在舊版的 Visaul C++ 版本中，會將不含任何空白字元的相鄰字串常值 (寬字元或窄字元字串常值) 解譯為單一的串連字串。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，您必須在兩個字串之間加入空白字元。 例如，下列程式碼必須有所變更：  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     只要在兩個字串之間加入空格即可。  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **placement new 與 delete**  
  
     為了讓 delete 運算子 (delete Operator) 與 C++ 14 標準一致，已對它加以變更。 如需此標準之變更的詳細資訊，請參閱 [C++ 調整大小的解除配置](http://isocpp.org/files/papers/n3778.html)。 此變更加入一種全域 delete 運算子，該運算子需要大小參數。 重大變更是如果您先前使用具有相同簽章 (藉此對應至 placement new 運算子) 的 operator delete 函式，就會發生編譯器錯誤 (C2956，於使用 placement new 運算子所在之處發生，因為在程式碼的該位置上，此編譯器會嘗試識別合適且相符的 delete 運算子)。  
  
     函式 `void operator delete(void *, size_t)` 曾是 placement delete 運算子，相當於 C++ 11 中的 placement new 函式 "void \* operator new(size_t, size_t)"。 搭配 C++14 調整大小的解除配置，這個 delete 函式現在為 *「一般解除配置函式」* (Usual Deallocation Function) (全域 delete 運算子)。 此標準的要求為如果 placement new 的使用會查詢對應的 delete 函式，並找到一般解除配置函式，則此程式語式錯誤。  
  
     例如，假設您的程式碼同時定義 placement new 和 placement delete：  
  
    ```  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     您已定義的 placement delete 運算子和新的全域調整大小 delete 運算子之間的函式簽章比對會導致此問題發生。 針對 placement new 和 delete 運算子，請考慮是否可以使用 size_t 以外的不同類型。  請注意 size_t typedef 的類型是編譯器相依的；它是 Visual C++ 中不帶正負號的 int 之 typedef。 較佳的解決方案是使用這類列舉類型：  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     然後，變更 placement new 和 delete 的定義，藉此使用此類型取代 size_t 做為第二個引數。 您也需要更新對 placement new 的呼叫，藉此傳遞新的類型 (例如，使用 `static_cast<my_type>` 從整數值加以轉換)，並且更新 new 和 delete 的定義，用來轉換回整數類型。 您不需要為此使用列舉；具有 size_t 成員的類別類型也可以運作。  
  
     替代方案是您或許可以完全排除 placement new。 如果您的程式碼使用 placement new 實作記憶體集區，其中 placement 引數是此物件所配置或已刪除的大小，則調整大小解除配置功能或許會很適合取代您自己自訂的記憶體集區程式碼，而且您可以不使用 placement 函式，只使用您自己的雙引數 delete 運算子，用來取代此 placement 函式。  
  
     如果您不想立即更新您的程式碼，則可以使用編譯器選項 /Zc:sizedDealloc- 來還原舊版的行為。 如果您使用這個選項，則此雙引數 delete 函式將不存在，也不會與您的 placement delete 運算子發生衝突。  
  
-   **等位資料成員**  
  
     等位資料成員不再具有參考類型。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 順利編譯，但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 會產生錯誤。  
  
    ```  
    union U1 {  
        const int i;  
    };  
    union U2 {  
       int &i;  
    };  
    union U3 {  
        struct {int &i;};  
    };  
    ```  
  
     前一個程式碼會產生下列錯誤：  
  
    ```Output  
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type  
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type  
    ```  
  
     若要解決這個問題，請將參考類型變更為指標或值。 將此類型變更為指標需要變更使用此等位欄位的程式碼。 將此程式碼變更為值也可能會變更此等位中儲存的資料，這會影響其他欄位，因為在等位類型中的欄位會共用相同的記憶體。 根據值的大小而定，它也可能會變更等位的大小。  
  
-   現在匿名等位與標準更一致。 舊版的編譯器會產生匿名等位的明確建構函式和解構函式。 這些在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中已刪除。  
  
    ```  
    struct S {  
      S();  
     };  
  
     union {  
      struct {  
       S s;  
      };  
     } u; // C2280  
    ```  
  
     前一個程式碼會在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 產生下列錯誤：  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     若要解決這個問題，請提供您自己的建構函式和 (或) 解構函式之定義。  
  
    ```  
    struct S {  
    // Provide a default constructor by adding an empty function body.  
    S() {}   
    };  
  
    union {  
    struct {  
    S s;  
    };  
    } u;  
    ```  
  
-   **具匿名結構的等位**  
  
     為了符合標準，此執行階段行為為了等位中匿名結構的成員而有所變更。 建立這類等位時，不再隱含呼叫等位中匿名結構成員的建構函式。 此外，當此等位超出範圍時，將不再隱含呼叫等位中的匿名結構成員的解構函式。 請考慮下列程式碼，其中等位 U 包含匿名結構，該結構包含成員，此成員為具有解構函式的具名結構 S。  
  
    ```  
    #include <stdio.h>  
    struct S {  
        S() { printf("Creating S\n"); }  
        ~S(){ printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
        S s;  
    };  
        U() {}  
        ~U(){}  
    };  
  
    void f()  
    {  
        U u;  
        // Destructor implicitly called here.  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
    ```  
  
     在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，會在建立此等位時呼叫 S 建構函式，而且當函式 f 的堆疊已清除時，會呼叫 S 的解構函式。 但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，不會呼叫此建構函式和解構函式。 該編譯器會提供有關這項行為變更的警告。  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     若要還原原始行為，請對此匿名結構命名。 不論編譯器版本為何，非匿名結構的執行階段行為是相同的。  
  
    ```  
    #include <stdio.h>  
  
    struct S {  
        S() { printf("Creating S.\n"); }  
        ~S() { printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
            S s;  
        } namedStruct;  
        U() {}  
        ~U() {}  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
    ```  
  
     或者，請嘗試將建構函式和解構函式的程式碼移到新的函式，並加入這些來自此等位之建構函式和解構函式的函式呼叫。  
  
    ```  
    #include <stdio.h>  
  
    struct S {  
        void Create() { printf("Creating S.\n"); }  
        void Destroy() { printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
            S s;  
        };  
        U() { s.Create();  }  
        ~U() { s.Destroy(); }  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
    char s[1024];  
    printf("Press any key.\n");  
    gets_s(s);  
    return 0;  
    }  
    ```  
  
-   **範本解析**  
  
     已變更樣板的名稱解析。 在 C++ 中，在考慮名稱解析的候選時，也可能產生這種情況：一或多個考慮為可能符合的名稱產生無效的樣板具現化。 這些無效的具現化通常不會造成編譯器錯誤，也就是稱為 SFINAE (替代失敗是不是錯誤) 的原則。  
  
     現在，如果 SFINAE 需要此編譯器具現化類別樣板的特製化，則在這個程序期間發生的任何錯誤都會是編譯器錯誤。 在舊版中，此編譯器會忽略這類錯誤。 例如，請參考下列程式碼：  
  
    ```  
    #include <type_traits>  
  
    template<typename T>  
    struct S  
    {  
    S() = default;  
    S(const S&);  
    S(S&&);  
  
    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>  
    S(S<U>&&);  
    };  
  
    struct D;  
  
    void f1()  
    {  
    S<D> s1;  
        S<D> s2(s1);  
    }  
  
    struct B  
    {  
    };  
  
    struct D : public B  
    {  
    };  
  
    void f2()  
    {  
    S<D> s1;  
        S<D> s2(s1);  
    }  
  
    ```  
  
     如果您使用目前的編譯器編譯時，會產生下列錯誤：  
  
    ```Output  
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'  
    ..\t331.cpp(14): note: see declaration of 'D'  
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled  
            with  
            [  
                T=D,  
                U=D  
            ]  
    ```  
  
     這是因為在進行 is_base_of 之第一個引動過程的時候，尚未定義類別 'D'。  
  
     在這種情況下，除非已宣告此類別，否則使用這類類型特性並不能修正問題。 如果您將 B 和 D 的定義移至此程式碼檔案開頭，則可解決此錯誤。 如果此定義位於標頭檔中，請檢查標頭檔之 include 陳述式的順序，藉此確定在使用有問題的樣板之前，會先編譯任何類別的定義。  
  
-   **複製建構函式**  
  
     在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 與 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中，若類別具有使用者定義的移動建構函式，但沒有使用者定義的複製建構函式，則編譯器將會為該類別產生複製建構函式。 在 Dev14 中，也會將這個隱含產生的複製建構函式標示為"= delete"。  
  
##  <a name="VS_Update1"></a> Update 1 的合規性改進  
  
-   **私用的虛擬基底類別與間接繼承**  
  
     舊版編譯器允許衍生的類別呼叫其*間接衍生*`private virtual`的基底類別成員函式。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2280。  
  
    ```Output  
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    class base  
    {  
    protected:  
        base();  
        ~base();  
    };  
  
    class middle: private virtual base {};class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  //   
    }  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    class base;  // as above  
  
    class middle: protected virtual base {};  
    class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
     -或-  
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **多載的運算子 new 和運算子 delete**  
  
     舊版編譯器允許非成員 `operator new` 和非成員 `operator delete` 被宣告為靜態，以及在全域命名空間以外的命名空間中宣告。  這種舊行為造成的風險是，程式不會呼叫程式設計人員所預期的 `new` 或 `delete` 運算子實作，導致無訊息的錯誤執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2323。  
  
    ```Output  
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     此外，雖然編譯器不提供特定的診斷，但內嵌運算子 new 會被視為語式錯誤。  
  
-   對非類別類型 呼叫 'operator type()' (使用者定義的轉換) **  
  
     舊版編譯器允許在非類別類型上呼叫 'operator *type*()'，但以無訊息方式略過。 這種舊行為造成的風險是，會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2228。  
  
    ```Output  
    error C2228: left of '.operator type' must have class/struct/union  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column.operator index_t());  // error C2228  
    }  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'  
    }  
    ```  
  
-   **詳細類型指定名稱中有重複的類型名稱**  
  
     舊版編譯器允許複雜的類型規範中有 `typename` ，但這種方式撰寫的程式碼語意不正確。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C3406。  
  
    ```Output  
    error C3406: 'typename' cannot be used in an elaborated type specifier  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    template <typename class T>  
    class container;  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case  
    class container;  
    ```  
  
-   **從初始設定式清單推斷陣列類型**  
  
     舊版編譯器不支援初始設定式清單的陣列類型推斷。 編譯器現在支援這種形式的類型推斷，而這樣一來，使用初始設定式清單呼叫函式範本現在可能會模稜兩可，也可能和舊版編譯器選擇不同的多載。 若要解決這些問題，程式現在必須明確指定程式設計人員所要的多載。  
  
     當這種新行為讓多載解析考慮和過去的候選項目同樣適合的其他候選項目時，呼叫就會變得模稜兩可，而編譯器則會發出編譯器錯誤 C2668。  
  
    ```Output  
    error C2668: 'function' : ambiguous call to overloaded function.  
    ```  
  
     範例 1：模稜兩可地呼叫多載函式 (之前)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now considers this call ambiguous, and issues a compiler error  
        f({3});  error C2668: 'f' ambiguous call to overloaded function  
    }  
    ```  
  
     範例 1：模稜兩可地呼叫多載函式 (之後)  
  
    ```cpp  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.  
        f(3);  
    }  
    ```  
  
     當這種新行為讓多載解析考慮比過去的候選項目更適合的其他候選項目時，呼叫會明確解析為新的候選項目，讓程式行為變得和程式設計人員預期的不同。  
  
     範例 2：多載解析的變更 (之前)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)  
    struct S  
    {  
        int i;  
        int j;  
    };  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead  
        f({1, 2});  
    }  
    ```  
  
     範例 2：多載解析的變更 (之後)  
  
    ```cpp  
    struct S;  // as before  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.  
        f(S{1, 2});  
    }  
    ```  
  
-   **還原 switch 陳述式警告**  
  
     舊版編譯器移除了先前存在的和 `switch` 陳述式相關的警告，現在已還原這些警告。 編譯器現在會發出還原的警告，而與特定情況相關的警告 (包括預設的情況) 都會在包含違規情況的程式行發出，而不是在 switch 陳述式的最後一行發出。 現在，在和過去不一樣的程式行中發出警告的結果是，以前使用 `#pragma warning(disable:####)` 隱藏的警告，可能不會如預期隱藏起來。 若想要如預期隱藏這些警告，就必須將 `#pragma warning(disable:####)` 指示詞移至第一個可能違規情況的上一行。 以下是還原的警告。  
  
    ```Output  
    warning C4060: switch statement contains no 'case' or 'default' labels  
    ```  
  
    ```Output  
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label  
    ```  
  
    ```Output  
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled  
    ```  
  
    ```Output  
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'  
    ```  
  
    ```Output  
    warning C4064: switch of incomplete enum 'flags'  
    ```  
  
    ```Output  
    warning C4065: switch statement contains 'default' but no 'case' labels  
    ```  
  
    ```Output  
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'  
    ```  
  
    ```Output  
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given  
    ```  
  
     C4063 範例 (之前)  
  
    ```cpp  
    class settings  
    {  
    public:  
        enum flags  
        {  
            bit0 = 0x1,  
            bit1 = 0x2,  
            ...  
        };  
        ...  
    };  
  
    int main()  
    {  
        auto val = settings::bit1;  
  
        switch (val)  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // warning C4063  
            break;  
        }  
    };  
    ```  
  
     C4063 範例 (之後)  
  
    ```cpp  
    class settings {...};  // as above  
  
    int main()  
    {  
        // since C++11, use std::underlying_type to determine the underlying type of an enum  
        typedef std::underlying_type<settings::flags>::type flags_t;  
  
        auto val = settings::bit1;  
  
        switch (static_cast<flags_t>(val))  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // ok  
            break;  
        }  
    };  
    ```  
  
     其他還原警告的範例會於其各自文件中提供。  
  
-   **#include：路徑名稱使用上層目錄指定名稱 '..'** (只影響 /Wall /WX)  
  
     舊版編譯器未偵測到 在  `#include` 指示詞的路徑名稱中是否使用上層目錄指定名稱 '..'。 以這種方式撰寫的程式碼通常會包含因為錯誤使用專案相對路徑而存在於專案以外的標頭。 這種舊行為造成的風險是，編譯程式時所包含的原始程式檔，可能不是程式設計人員想要的檔案，或是這些相對路徑無法移植到其他建置環境。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會發出選擇性的編譯器警告 C4464。  
  
    ```Output  
    warning C4464: relative include path contains '..'  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     此外，雖然編譯器不會提供特定的診斷，但仍建議您不要使用上層目錄指定名稱 ".." 來指定專案的 include 目錄。  
  
-   **#pragma optimize() 擴充超出了標頭檔結尾** (只會影響 /Wall /WX)  
  
     舊版編譯器未偵測到最佳化旗標設定的變更，這會逸出包含在轉譯單位內的標頭檔。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在違反 `#include`的位置發出選擇性的編譯器警告 C4426。 只有當變更與編譯器命令列引數設定的最佳化旗標發生衝突時，才會發出這個警告。  
  
    ```Output  
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  // warning C4426  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  
    ```  
  
-   **不相符的 #pragma warning(push)** 和 **#pragma warning(pop)** (只影響 /Wall /WX)  
  
     舊版編譯器偵測不到要與不同原始程式碼檔案中，`#pragma warning(pop)` 狀態變更配對的 `#pragma warning(push)` 狀態變更，這種規劃極為罕見。 這種舊行為造成的風險是，編譯程式所啟用的警告集合不是程式設計人員想要的集合，可能導致無訊息的錯誤執行階段行為。 現在編譯器會偵測以此方式撰寫的程式碼，通知其程式設計人員，同時在符合 `#pragma warning(pop)` 的位置發出選擇性的編譯器警告 C5031 (如有啟用)。 此警告包含參考對應 #pragma warning(push) 位置的附註。  
  
    ```Output  
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    ...  
    #pragma warning(pop)  // pops a warning state not pushed in this source file   
    ...  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'  
    ...  
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031  
    ...  
  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  // pops the warning state pushed in this source file  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    #pragma warning(push)  // pushes the warning state pushed in this source file  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.  
    ...  
    #include "C5031_part2.h"  
    ...  
  
    ```  
  
     以此方式撰寫的程式碼雖然不常見，但有時是刻意為之。 以此方式撰寫的程式碼對於 `#include` 順序的變更十分敏感；如有可能，建議原始程式碼檔案獨立管理警告狀態。  
  
-   **不相符的 #pragma warning(push)** (只會影響 /Wall /WX)  
  
     舊版編譯器轉在轉譯單位的結尾未偵測到不相符的 `#pragma warning(push)` 狀態變更。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在不符合 #pragma warning(push) 的位置發出選擇性的編譯器警告 C5032。 只有轉譯單位沒有任何編譯錯誤時，才會發出這個警告。  
  
    ```Output  
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5032.h ends without #pragma warning(pop)  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop) // matches #pragma warning (push) on line 1  
    // C5032.h ends  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **改進之後的 #pragma 警告狀態追蹤也可能會發出其他警告**  
  
     舊版編譯器過去追蹤 #pragma 警告狀態變更的能力不佳，無法發出所有預期出現的警告。 這種行為造成的風險是，某些有效隱藏警告的情況，不是程式設計人員所預想的情況。 編譯器現在追蹤 #pragma 警告狀態的能力更強大，特別是關於範本內部的 #pragma 警告狀態變更，可以選擇性發出新的警告 C5031 和 C5032，它們的目的是協助程式設計人員找出非預期使用的 `#pragma warning(push)` 和 `#pragma warning(pop)`。  
  
     由於改良的 #pragma 警告狀態變更追蹤，以前錯誤隱藏的警告或以前與錯誤診斷問題有關的警告，現在都可能會發出。  
  
-   **不可能執行到之程式碼的識別改善**  
  
     C++ 標準程式庫的變更，以及比舊版編譯器強大的內嵌函式呼叫能力，可能會讓編譯器證明不可能執行到某些程式碼。 這種新行為可能會導致新的警告 C4720 的執行個體，且更頻繁地發出這個警告。  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     在許多情況下，只有啟用最佳化編譯時，才可能發出這個警告；因為最佳化可能內嵌更多的函式呼叫、消除多餘的程式碼，或者可能判斷某不可能執行到些程式碼。 我們觀察到，新的警告 C4720 執行個體經常發生在 try/catch 區塊，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True)時。  
  
     範例 (之前)  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(...)   
    {   
        do_something();  // ok   
    }  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(...)   
    {   
        do_something();  // warning C4702: unreachable code  
    }  
    ```  
  
##  <a name="VS_Update2"></a> Update 2 的合規性改進  
  
-   **運算式 SFINAE 的部分支援也可能會發出其他警告與錯誤**  
  
     舊版編譯器因為缺少對運算式 SFINAE 的支援，所以無法剖析 `decltype` 指定名稱內某些種類的運算式。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器現在會剖析這些運算式，並隨著一致性逐漸改進來提供運算式 SFINAE 的部分支援。 如此一來，編譯器現在就會發出在舊版編譯器未剖析的運算式中找到的警告與錯誤。  
  
     當此新行為剖析包含尚未宣告之類型的 `decltype` 運算式時，編譯器會發出編譯器錯誤 C2039。  
  
    ```Output  
    error C2039: 'type': is not a member of '`global namespace''  
    ```  
  
     範例 1：使用未宣告的型別 (之前)  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     範例 1 (之後)  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     當此新行為剖析缺少必要 `typename` 關鍵字的 `decltype` 運算式以將相依名稱指定為類型時，編譯器會發出編譯器警告 C4346 與編譯器錯誤 C2923。  
  
    ```Output  
    warning C4346: 'S2<T>::Type': dependent name is not a type  
    ```  
  
    ```Output  
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'  
    ```  
  
     範例 2：相依名稱不是型別 (之前)  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     範例 2 (之後)  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile`  **成員變數會禁止隱含定義的建構函式與指派運算子**  
  
     舊版編譯器允許具有 `volatile` 成員變數的類別自動產生預設的複製/移動建構函式及預設的複製/移動指派運算子。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器現在會考慮讓具有揮發性成員變數的類別擁有非 trivial 建構和指派運算子，這樣可防止自動產生這些運算子的預設實作。  當此類別是等位 (或類別內的匿名等位) 的成員時，就會將等位 (或包含 Unonymous 等位之類別) 的複製/移動建構函式和複製/移動指派運算子隱含定義為已刪除。 在未明確定義的情況下，嘗試建構或複製等位 (或包含匿名等位的類別) 將會發生錯誤，導致編譯器發出編譯器錯誤 C2280。  
  
    ```Output  
    error C2280: 'B::B(const B &)': attempting to reference a deleted function  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **靜態成員函式不支援 cv 限定詞**  
  
     舊版 Visual C++ 2015 允許靜態成員函式擁有 cv 限定詞。 此行為起因於 Visual C++ 2015 與 Visual C++ 2015 Update 1 的迴歸；Visual C++ 2013 與舊版 Visual C++ 拒絕以此方式撰寫的程式碼。 Visual C++ 2015 與 Visual C++ 2015 Update 1 的行為不正確，且不符合 C++ 標準。  Visual Studio 2015 Update 2 拒絕以此方式撰寫的程式碼，並會發出編譯器錯誤 C2511。  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     範例 (之前)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     範例 (之後)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **WinRT 程式碼不允許列舉的向前宣告** (只影響 /ZW)  
  
     為 Windows 執行階段 (WinRT) 編譯的程式碼不允許向前宣告 `enum` 類型，類似於使用 /clr 編譯器參數為 .Net Framework 編譯 Managed C++ 程式碼的情形。 此行為可確保一律得知列舉的大小，並能正確將其投影至 WinRT 型別系統。 編譯器拒絕以此方式撰寫的程式碼，且會發出編譯器錯誤 C2599 以及編譯器錯誤 C3197。  
  
    ```Output  
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed  
    ```  
  
    ```Output  
    error C3197: 'public': can only be used in definitions  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     範例 (之後)  
  
    ```cpp  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **不得從內部宣告多載的非成員運算子 new 與運算子 delete** (層級 1 (/ W1) 預設為開啟)  
  
     舊版編譯器不會在以內嵌方式宣告多載的非成員運算子 new 與運算子 delete 函式時發出警告。 以此方式撰寫的程式碼語式錯誤 (不需要診斷)，且可能因為 new 與 delete 運算子不相符 (尤其在搭配調整大小後的解除配置使用時)，而導致難以診斷的記憶體問題。   編譯器現在會發出編譯器警告 C4595，協助識別以此方式撰寫的程式碼。  
  
    ```Output  
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline  
    ```  
  
     範例 (之前)  
  
    ```cpp  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     範例 (之後)  
  
    ```cpp  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     可能需要先將運算子定義從標頭檔移出，再將其移入對應的原始程式檔，才能修正以此方式撰寫的程式碼。  
  
##  <a name="VS_Update3"></a> Update 3 的合規性改進  
  
-   **std::is_convertable 現在已可偵測自我指派** (標準程式庫)  
  
     當舊版 `std::is_convertable` 類型特性的複製建構函式被刪除或為私用時，其無法正確地偵測類別類型的自我指派。 現在在套用到複製建構函式被刪除或為私用的類別類型時，`std::is_convertable<>::value` 會正確設定為 `false`。  
  
     此變更沒有相關聯的編譯器診斷。  
  
     範例  
  
    ```cpp  
    #include <type_traits>  
  
    class X1  
    {  
    public:  
        X1(const X1&) = delete;  
    };  
  
    class X2  
    {  
    private:  
        X2(const X2&);  
    };  
  
    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");  
    ```  
  
     在舊版 Visual C++ 中，因為 `std::is_convertable<>::value` 不正確地設定為 `true`，致使此範例底部的靜態判斷提示能夠通過。 `std::is_convertable<>::value` 現在會正確地設定為 `false`，讓靜態判斷提示失敗。  
  
-   **預設或已刪除的 trivial 複製及移動建構函式會採用存取指定名稱**  
  
     舊版編譯器不會檢查預設或已刪除之 trivial 複製及移動建構函式的存取指定名稱，就允許其接受呼叫。 這個舊的行為不正確，而且不符合 C++ 標準。 在某些情況下，這項舊行為的風險是會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器現在會檢查預設或已刪除之 trivial 複製及移動建構函式的存取指定名稱，據此決定其是否可以接受呼叫；若無法呼叫，即發出編譯器警告 C2248。  
  
    ```Output  
    error C2248: 'S::S' cannot access private member declared in class 'S'  
    ```  
  
     範例 (之前)  
  
    ```cpp  
    class S {  
    public:  
           S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(S);  // pass S by value  
  
    int main()  
    {  
        S s;  
        f(s);  // error C2248, can't invoke private copy constructor  
    }  
    ```  
  
     範例 (之後)  
  
    ```cpp  
    class S {  
    public:  
           S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(const S&);  // pass S by reference  
  
    int main()  
    {  
        S s;  
        f(s);  
    }  
    ```  
  
-   **屬性化 ATL 程式碼支援已標示為即將淘汰** (層級 1 (/W1) 預設為開啟)  
  
     舊版編譯器支援屬性化 ATL 程式碼。 [自 Visual C++ 2008 開始下一個階段移除對屬性化 ATL 程式碼支援的下一個階段](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx)起，即已將屬性化 ATL 程式碼標示為即將淘汰。 編譯器現在會發出編譯器警告 C4467，協助識別這類已標示為即將淘汰的程式碼。  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     若要續使用屬性化 ATL 程式碼，直到編譯器停止支援為止，可將 `/Wv:18` 或 `/wd:4467` 命令列引數傳遞給編譯器，或在原始程式碼中新增 `#pragma warning(disable:4467)` 來停用此警告。  
  
     範例 1 (之前)  
  
    ```cpp  
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]  
    class A {};  
    ```  
  
     範例 1 (之後)  
  
    ```cpp  
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};  
  
    ```  
  
     您偶爾可能會需要或想要建立 IDL 檔案，以避免使用已標示為即將淘汰的 ATL 屬性，如下列範例程式碼所示  
  
     範例 2 (之前)  
  
    ```cpp  
    [emitidl];  
    [module(name="Foo")];  
  
    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]  
    __interface ICustom {  
        HRESULT Custom([in] long l, [out, retval] long *pLong);  
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);  
    };  
  
    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]  
    class CFoo : public ICustom  
    {  
        // ...  
    };  
    ```  
  
     首先，請建立 *.idl 檔案；產生的 vc140.idl 檔案可用於取得包含介面及註釋的 \*.idl 檔案。  
  
     接著請在您的組建中新增 MIDL 步驟，確保 C++ 介面定義能夠順利產生。  
  
     範例 2 IDL (之後)  
  
    ```cpp  
    import "docobj.idl";  
  
    [  
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)  
    ]  
  
    interface ICustom : IUnknown {  
        HRESULT  Custom([in] long l, [out,retval] long *pLong);  
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);  
    };  
  
    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]  
    library Foo  
    {  
        importlib("stdole2.tlb");  
        importlib("olepro32.dll");  
            [  
                version(1.0),  
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)  
            ]  
  
        coclass CFoo {  
            interface ICustom;  
        };  
    }  
    ```  
  
     然後請直接在實作檔案中使用 ATL，如下列範例程式碼所示。  
  
     範例 2 實作 (之後)  
  
    ```cpp  
    #include <idl.header.h>  
    #include <atlbase.h>  
  
    class ATL_NO_VTABLE CFooImpl :  
        public ICustom,  
        public ATL::CComObjectRootEx<CComMultiThreadModel>  
    {  
    public:  
        BEGIN_COM_MAP(CFooImpl)  
        COM_INTERFACE_ENTRY(ICustom)  
        END_COM_MAP()  
    };  
    ```  
  
-   **先行編譯的標頭檔 (PCH) 與不相符的 #include 指示詞** (僅影響 /Wall /WX)  
  
     使用先行編譯的標頭檔 (PCH) 時，舊版編譯器接受 `-Yc` 與 `-Yu` 編譯之間原始程式碼中的 `#include` 指示詞不相符。 編譯器現在已不再接受以此方式撰寫的程式碼。   現在在使用 PCH 檔案時，編譯器會發出編譯器警告 CC4598 協助識別不相符的 `#include` 指示詞。  
  
    ```Output  
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position  
    ```  
  
     範例 (之前)：  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"  
    #include "c.h"  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "b.h"  
    #include "a.h"  // mismatched order relative to X.cpp  
    #include "c.h"  
    ```  
  
     範例 (之後)  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"   
    #include "c.h"  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h" // matched order relative to X.cpp  
    #include "c.h"  
    ```  
  
-   **先行編譯的標頭檔 (PCH) 與不相符的 include 目錄** (僅影響 /Wall /WX)  
  
     使用先行編譯的標頭檔 (PCH) 時，舊版編譯器接受 `-Yc` 與 `-Yu` 編譯之間編譯器的 include 目錄 (`-I`) 命令列引數不相符。 編譯器現在已不再接受以此方式撰寫的程式碼。   現在在使用 PCH 檔案時，編譯器會發出編譯器警告 CC4599 協助識別不相符的 include 目錄 (`-I`) 命令列引數。  
  
    ```Output  
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position  
    ```  
  
     範例 (之前)  
  
    ```ms-dos  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h Z.cpp  
    ```  
  
     範例 (之後)  
  
    ```ms-dos  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h -I.. Z.cpp  
    ```
