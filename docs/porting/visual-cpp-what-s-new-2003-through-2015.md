---
title: 從 2003 到 2015 的 Visual C++ 新功能
ms.date: 11/04/2016
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 6d79406e07b8839e196f15d9bc3aed96cbc3dca8
ms.sourcegitcommit: 31a2a9845f5e1d35ab054906d8cdc6582a5220bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51520172"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>從 2003 到 2015 的 Visual C++ 新功能

此頁面會收集從 Visual Studio 2015 往回到 2003 之所有 Visual C++ 版本的所有「新功能」頁面。 這項資訊的提供是為了方便起見，這在從舊版 Visual C++ 升級時可能十分有用。

> [!NOTE]
> 如需 Visual Studio 2017 的資訊，請參閱 [Visual Studio 2017 中 Visual C++ 的新功能](../what-s-new-for-visual-cpp-in-visual-studio.md)及[Visual Studio 2017 中 Visual C++ 的合規性改進](../cpp-conformance-improvements-2017.md)。

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Visual Studio 2015 中 C++ 的新功能

在 Visual Studio 2015 和更新版本中，隨著不斷地改善編譯器一致性，有時可能會變更編譯器解讀您現有原始程式碼的方式。 當發生這種情況時，可能會在您建置時發生不同或新的錯誤，甚至程式碼的行為與上版組建不同，而且看似正常運作。

所幸這些差異對於您大部分的原始程式碼影響很小，甚至完全沒有影響。即使有需要變更原始程式碼或進行其他變更才能解決這些差異，這類修正通常很少而且簡單明瞭。 我們加入了許多先前接受，但後來可能需要變更的原始程式碼範例 *(之前)*，以及用以更正的修正 *(之後)*。

雖然這些差異可脦會影響您的原始程式碼或其他組建成品，但不會影響每版 Visual C++ 更新之間的二進位相容性。 「重大變更」是較重大的變更類型，會影響二進位檔相容性，但這些類型的二進位相容性只會在 Visual C++ 的主要版本之間中斷。 例如，Visual C++ 2013 與 Visual C++ 2015 之間。 如需 Visual C++ 2013 與 Visual C++ 2015 之間的重大變更資訊，請參閱 [Visual C++ 變更歷程記錄 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)。

- [Visual Studio 2015 的一致性改善](#VS_RTM)

- [Visual Studio 2015 Update 1 的一致性改善](#VS_Update1)

- [Visual Studio 2015 Update 2 的一致性改善](#VS_Update2)

- [Visual Studio 2015 Update 3 的一致性改善](#VS_Update3)

### <a name="VS_RTM"></a> Visual Studio 2015 的一致性改善

- **/Zc:forScope- 選項**

   `/Zc:forScope-` 編譯器選項已淘汱，並將在未來版本中移除。

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   該選項通常是在非標準程式碼的迴圈變數應該已經超出範圍 (根據該標準) 之後，用來允許此非標準程式碼。 只有當您使用 `/Za` 選項編譯時才需要這樣做，因為在沒有指定 `/Za` 的情況下，會一律允許在迴圈結束之後使用 for 迴圈變數。 如果您不在意標準一致性 (例如，如果您並不打算將程式碼設計成可移植到其他編譯器)，則可以關閉 `/Za` 選項 (或將**停用語言延伸模組**屬性設為**否**)。 如果您在意撰寫可攜式且符合標準規範的程式碼，就應該要重寫程式碼，將這類變數的宣告移至該迴圈外，使其符合此標準。

   ```cpp
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

- **Zg 編譯器選項。**

   `/Zg` 編譯器選項 (產生函式原型) 已無法使用。 這個編譯器選項之前已遭取代。

- 您再也無法從命令列藉由 mstest.exe 使用 C++ /CLI 來執行單元測試。 請改用 vstest.console.exe

- **可變動的關鍵字。**

   在 **mutable** 儲存類別指定名稱原先可編譯而不會發生錯誤的位置，已無法再加以使用。 現在，此編譯器會發生錯誤 C2071 (不合法的儲存類別)。 根據該標準，可變動的規範只可以套用至類別資料成員的名稱，而不能套用至宣告為常數或靜態的名稱，也不能套用至參考的成員。

   例如，請參考下列程式碼：

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   舊版的 Visual C++ 編譯器可接受這種做法，但現在該編譯器會產生下列錯誤：

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   若要修正此錯誤，只要移除冗餘的 **mutable** 關鍵字即可。

- **char_16_t 與 char32_t**

   您再也無法使用 `char16_t` 或 `char32_t` 做為 typedef 的別名，因為現在會將這些類型視為內建類型。 使用者和程式庫作者通常會分別定義 `char16_t` 和 `char32_t` 作為 `uint16_t` 和 `uint32_t` 的別名。

   ```cpp
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

   若要更新您的程式碼，請移除此 **typedef** 宣告，並重新命名任何其他與這些名稱衝突的識別項。

- **非類型範本參數**

   在您提供明確的樣板引數之際，和非類型樣板參數有關的特定程式碼之類型相容性檢查即為正確。 例如，下列程式碼可在舊版的 Visual C++ 中正確無誤地編譯。

   ```cpp
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

- **__declspec(align)**

   該編譯器已不再接受函式上的 `__declspec(align)` 。 之前的編譯器一律將它忽略，但現在會產生編譯器錯誤。

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   若要修正這個問題，請從此函式宣告中移除 `__declspec(align)` 。 因為它沒有任何作用，移除它並不會變更任何項目。

- **例外狀況處理**

   有幾個例外狀況處理的變更。 首先，例外狀況物件必須可複製或可移動。 下列程式碼在 Visual Studio 2013 中可成功編譯，但無法在 Visual Studio 2015 中編譯：

   ```cpp
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

   問題是出在於此複製建構函式是私用的，無法如同處理例外狀況的正常過程中發生的物件一樣複製，因此並不能複製該物件。 相同情況也適用於將複製建構函式宣告為 **explicit** 的時候。

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   若要更新您的程式碼，請確定例外狀況物件的複製建構函式是公用的，而未標示為 **explicit**。

   以傳值方式攔截例外狀況也需要可複製的例外狀況物件。 下列程式碼在 Visual Studio 2013 中可成功編譯，但無法在 Visual Studio 2015 中編譯：

   ```cpp
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

   您可以將 **catch** 的參數類型變更為參考，以修正這個問題。

   ```cpp
    catch(D& d)
    {
    }
   ```

- **後接巨集的字串常值**

   該編譯器現在支援使用者定義常值。 因此，會將後面接著巨集且不含任何中間空白字元的字串常值解譯為使用者定義常值，這可能會產生錯誤或非預期的結果。 例如，在舊版編譯器中，下列程式碼可順利編譯：

   ```cpp
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

   該編譯器會將其解譯為後面接著巨集的字串常值 "hello"，並且將該巨集展開成 "there"，然後再將這兩個字串常值串連成一個。 在 Visual Studio 2015 中，編譯器會將其解譯為使用者定義的常值，但是沒有相符的使用者定義常值 _x，所以會產生錯誤。

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   若要修正這個問題，請在此字串常值和巨集之間加入空格。

- **相鄰字串常值**

   如同前面所述，因為字串剖析時相關變更的緣故，在舊版的 Visaul C++ 版本中，會將不含任何空白字元的相鄰字串常值 (寬字元或窄字元字串常值) 解譯為單一的串連字串。 在 Visual Studio 2015 中，您必須在兩個字串之間新增空白字元。 例如，下列程式碼必須有所變更：

   ```cpp
    char * str = "abc""def";
   ```

   只要在兩個字串之間加入空格即可。

   ```cpp
    char * str = "abc" "def";
   ```

- **placement new 與 delete**

   為了讓 **delete** 運算子與 C++ 14 標準一致，已對它進行變更。 如需此標準之變更的詳細資訊，請參閱 [C++ 調整大小的解除配置](http://isocpp.org/files/papers/n3778.html)。 變更當中新增了一種全域 **delete** 運算子，該運算子會採用大小參數。 中斷性變更是如果您先前使用具有相同簽章 (藉此對應至 **placement new** 運算子) 的運算子 **delete**，就會發生編譯器錯誤 (C2956，於使用 **placement new** 處發生，因為在程式碼的該位置上，編譯器會嘗試識別合適且相符的 **delete** 運算子)。

   函式 `void operator delete(void *, size_t)` 曾是 **placement delete** 運算子，相當於 C++ 11 中的 **placement new** 函式 `void * operator new(size_t, size_t)`。 搭配 C++14 調整大小的解除配置，這個 **delete** 函式現在為「一般解除配置函式」 (全域 **delete** 運算子)。 標準的要求是，如果 **placement new** 的使用會查詢對應的 **delete** 函式，並找到一般解除配置函式，則此程式語式錯誤。

   例如，假設您的程式碼同時定義 **placement new** 和 **placement delete**：

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   您已定義的 **placement delete** 運算子與調整大小的全域新 **delete** 運算子之間，因為函式簽章相符，而導致此問題發生。 對於任何 **placement new** 和 **delete** 運算子，請考慮是否可以使用 `size_t` 以外的其他類型。  請注意，`size_t` **typedef** 的類型與編譯器有關；若為 Visual C++ 中的 **unsigned int**，則會是 **typedef**。 較佳的解決方案是使用這類列舉類型：

   ```cpp
    enum class my_type : size_t {};
   ```

   然後，變更 placement **new** 和 **delete** 的定義，以使用此類型取代 `size_t` 成為第二個引數。 您也需要更新對 **placement new** 的呼叫，以傳遞新的類型 (例如，使用 `static_cast<my_type>` 從整數值加以轉換)，並且更新 **new** 和 **delete** 的定義，用來轉換回整數類型。 您不需要為此使用 **enum**；具有 `size_t` 成員的類別類型也適用。

   另一個解決方案是，您或許可以完全排除 **placement new**。 如果您的程式碼使用 **placement new** 實作記憶體集區，其中 placement 引數是配置或刪除的物件大小，則調整大小解除配置功能或許會很適合取代您自己的自訂記憶體集區程式碼，而且您可以不使用 placement 函式，只使用您自己的雙引數 **delete** 運算子，用來取代此 placement 函式。

   如果您不想立即更新您的程式碼，則可以使用編譯器選項 `/Zc:sizedDealloc-` 來還原舊版的行為。 如果您使用這個選項，則雙引數 **delete** 函式將不存在，也不會與您的 **placement delete** 運算子發生衝突。

- **等位資料成員**

   等位資料成員不再具有參考類型。 下列程式碼會在 Visual Studio 2013 中成功編譯，但在 Visual Studio 2015 中會產生錯誤。

   ```cpp
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

- **匿名等位**

   現在與標準更一致。 舊版的編譯器會產生匿名等位的明確建構函式和解構函式。 這些已在 Visual Studio 2015 中刪除。

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   前述程式碼會在 Visual Studio 2015 產生下列錯誤：

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   若要解決這個問題，請提供您自己的建構函式和 (或) 解構函式之定義。

   ```cpp
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

- **具匿名結構的等位**

   為了符合標準，此執行階段行為為了等位中匿名結構的成員而有所變更。 建立這類等位時，不再隱含呼叫等位中匿名結構成員的建構函式。 此外，當此等位超出範圍時，將不再隱含呼叫等位中的匿名結構成員的解構函式。 請考慮下列程式碼，其中等位 U 包含匿名結構，該結構包含成員，此成員為具有解構函式的具名結構 S。

   ```cpp
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

   在 Visual Studio 2013 中，會在建立 union 時呼叫 S 的建構函式，而在清除函式 f 的堆疊時，會呼叫 S 的解構函式。 但在 Visual Studio 2015 中，不會呼叫此建構函式和解構函式。 該編譯器會提供有關這項行為變更的警告。

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   若要還原原始行為，請對此匿名結構命名。 不論編譯器版本為何，非匿名結構的執行階段行為是相同的。

   ```cpp
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

   ```cpp
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

- **範本解析**

   已變更樣板的名稱解析。 在 C++ 中，在考慮名稱解析的候選時，也可能產生這種情況：一或多個考慮為可能符合的名稱產生無效的樣板具現化。 這些無效的具現化通常不會造成編譯器錯誤，也就是稱為 SFINAE (替代失敗是不是錯誤) 的原則。

   現在，如果 SFINAE 需要此編譯器具現化類別樣板的特製化，則在這個程序期間發生的任何錯誤都會是編譯器錯誤。 在舊版中，此編譯器會忽略這類錯誤。 例如，請參考下列程式碼：

   ```cpp
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

- **複製建構函式**

   在 Visual Studio 2013 和 Visual Studio 2015 中，如果類別具有使用者定義的移動建構函式，但沒有使用者定義的複製建構函式，則編譯器會為該類別產生複製建構函式。 在 Dev14 中，也會將這個隱含產生的複製建構函式標示為"= delete"。

### <a name="VS_Update1"></a> Visual Studio 2015 Update 1 的一致性改善

- **私用的虛擬基底類別與間接繼承**

   舊版編譯器允許衍生類別呼叫其「間接衍生」`private virtual`基底類別的成員函式。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2280。

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

  \-或-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **多載的運算子 new 與運算子 delete**

   編譯器先前版本允許非成員 **operator new** 和非成員 **operator delete** 宣告為 static，以及在全域命名空間以外的命名空間中宣告。  這種舊行為造成的風險是，程式不會呼叫程式設計人員所預期的 **new** 或 **delete** 運算子實作，導致無訊息的錯誤執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2323。

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

- **對非類別類型呼叫 'operator *type*()' (使用者定義的轉換)**：舊版編譯器允許對非類別類型呼叫 'operator *type*()'，但以無訊息方式略過。 這種舊行為造成的風險是，會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2228。

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

- **複雜的類型指定名稱中有重複的類型名稱**：舊版編譯器允許複雜的類型規範中有 **typename**，但這種方式撰寫的程式碼語意不正確。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C3406。

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

- **初始設定式清單的陣列類型推斷**：舊版編譯器不支援初始設定式清單的陣列類型推斷。 編譯器現在支援這種形式的類型推斷，而這樣一來，使用初始設定式清單呼叫函式範本現在可能會模稜兩可，也可能和舊版編譯器選擇不同的多載。 若要解決這些問題，程式現在必須明確指定程式設計人員所要的多載。

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

- **還原 switch 陳述式警告**

   編譯器先前版本已移除先前存在與 **switch** 陳述式相關的警告，現在已還原這些警告。 編譯器現在會發出還原的警告，而與特定情況相關的警告 (包括預設的情況) 都會在包含違規情況的程式行發出，而不是在 switch 陳述式的最後一行發出。 現在，在和過去不一樣的程式行中發出警告的結果是，以前使用 `#pragma warning(disable:####)` 隱藏的警告，可能不會如預期隱藏起來。 若想要如預期隱藏這些警告，就必須將 `#pragma warning(disable:####)` 指示詞移至第一個可能違規情況的上一行。 以下是還原的警告。

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

- **#include：路徑名稱使用上層目錄指定名稱 '..'** (只會影響 `/Wall` `/WX`)

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

- **#pragma optimize() 延伸超出了標頭檔結尾** (只會影響 `/Wall` `/WX`)

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

- **不相符的 #pragma warning(push)** 和 **#pragma warning(pop)** (只會影響 `/Wall` `/WX`)

   舊版編譯器偵測不到要與不同原始程式碼檔案中，`#pragma warning(pop)` 狀態變更配對的 `#pragma warning(push)` 狀態變更，這種規劃極為罕見。 這種舊行為造成的風險是，編譯程式所啟用的警告集合不是程式設計人員想要的集合，可能導致無訊息的錯誤執行階段行為。 現在編譯器會偵測以此方式撰寫的程式碼，通知其程式設計人員，同時在符合 `#pragma warning(pop)` 的位置發出選擇性的編譯器警告 C5031 (如有啟用)。 此警告包含參考對應 `#pragma warning(push)` 位置的附註。

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

- **不相符的 #pragma warning(push)** (只會影響 `/Wall` `/WX`)

   舊版編譯器轉在轉譯單位的結尾未偵測到不相符的 `#pragma warning(push)` 狀態變更。 編譯器現在會偵測以此方式撰寫的程式碼並通知其程式設計人員，同時在不相符的 `#pragma warning(push)` 位置發出選擇性的編譯器警告 C5032 (如有啟用)。 只有轉譯單位沒有任何編譯錯誤時，才會發出這個警告。

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

- **改進之後的 #pragma 警告狀態追蹤也可能會發出其他警告**

   舊版編譯器過去追蹤 `#pragma warning` 狀態變更的能力不佳，無法發出所有預期出現的警告。 這種行為造成的風險是，某些有效隱藏警告的情況，不是程式設計人員所預想的情況。 編譯器現在追蹤 `#pragma warning` 狀態的能力更強大，特別是關於範本內部的 `#pragma warning` 狀態變更，可以選擇性發出新的警告 C5031 和 C5032，其目的是協助程式設計人員找出非預期使用的 `#pragma warning(push)` 和 `#pragma warning(pop)`。

   在 `#pragma warning` 狀態變更追蹤經過改良之後，以往不當隱藏的警告或先前與誤判問題有關的警告，現在都能夠發出。

- **不可能執行到之程式碼的識別改善**

   C++ 標準程式庫的變更，以及比舊版編譯器強大的內嵌函式呼叫能力，可能會讓編譯器證明不可能執行到某些程式碼。 這種新行為可能會導致新的警告 C4720 的執行個體，且更頻繁地發出這個警告。

   ```Output
    warning C4720: unreachable code
   ```

   在許多情況下，只有啟用最佳化編譯時，才可能發出這個警告；因為最佳化可能內嵌更多的函式呼叫、消除多餘的程式碼，或者可能判斷某不可能執行到些程式碼。 我們觀察到，警告 C4720 的新執行個體經常發生在 **try/catch** 區塊，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) 時。

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

### <a name="VS_Update2"></a> Visual Studio 2015 Update 2 的一致性改善

- **運算式 SFINAE 的部分支援也可能會發出其他警告與錯誤**

   編譯器先前版本因為不支援 SFINAE 運算式，所以無法剖析 **decltype** 指定名稱內某些種類的運算式。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器現在會剖析這些運算式，並隨著一致性逐漸改進來提供運算式 SFINAE 的部分支援。 如此一來，編譯器現在就會發出在舊版編譯器未剖析的運算式中找到的警告與錯誤。

   當這個新行為剖析 **decltype** 運算式，而其中包含尚未宣告的類型時，編譯器會發出編譯器錯誤 C2039。

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

   當這個新行為剖析缺少必要 **typename** 關鍵字的 **decltype** 運算式以將相依名稱指定為類型時，編譯器會發出編譯器警告 C4346 與編譯器錯誤 C2923。

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

- `volatile` **成員變數會禁止隱含定義的建構函式與指派運算子**：舊版編譯器允許具有 **volatile** 成員變數的類別自動產生預設複製/移動建構函式和預設複製/移動指派運算子。 這個舊的行為不正確，而且不符合 C++ 標準。 編譯器現在會考慮讓具有揮發性成員變數的類別擁有非 trivial 建構和指派運算子，這樣可防止自動產生這些運算子的預設實作。 當此類別是等位 (或類別內的匿名等位) 的成員時，就會將等位 (或包含 Unonymous 等位之類別) 的複製/移動建構函式和複製/移動指派運算子隱含定義為已刪除。 在未明確定義的情況下，嘗試建構或複製等位 (或包含匿名等位的類別) 將會發生錯誤，導致編譯器發出編譯器錯誤 C2280。

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

- **靜態成員函式不支援 cv 限定詞**

   舊版 Visual C++ 2015 允許靜態成員函式擁有 cv 限定詞。 此行為起因於 Visual C++ 2015 與 Visual C++ 2015 Update 1 的迴歸；Visual C++ 2013 與舊版 Visual C++ 拒絕以此方式撰寫的程式碼。 Visual C++ 2015 與 Visual C++ 2015 Update 1 的行為不正確，且不符合 C++ 標準。  Visual Studio 2015 Update 2 拒絕以此方式撰寫的程式碼，並會發出編譯器錯誤 C2511。

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   範例 (之前)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   範例 (之後)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **WinRT 程式碼不允許列舉的向前宣告** (僅會影響 `/ZW`)

   為 Windows 執行階段 (WinRT) 編譯的程式碼不允許向前宣告 **enum** 類型，類似於使用 `/clr` 編譯器參數為 .Net Framework 編譯受控 C++ 程式碼的情形。 此行為可確保一律得知列舉的大小，並能正確將其投影至 WinRT 型別系統。 編譯器拒絕以此方式撰寫的程式碼，且會發出編譯器錯誤 C2599 以及編譯器錯誤 C3197。

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

- **不得以內嵌方式宣告多載的非成員運算子 new 與運算子 delete** (層級 1 (`/W1`) 預設為開啟)

   舊版編譯器不會在以內嵌方式宣告非成員 **operator new** 與 **operator delete** 函式時發出警告。 以此方式撰寫的程式碼語式錯誤 (不需要診斷)，且可能因為 new 與 delete 運算子不相符 (尤其在搭配調整大小後的解除配置使用時)，而導致難以診斷的記憶體問題。 編譯器現在會發出編譯器警告 C4595，協助識別以此方式撰寫的程式碼。

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

### <a name="VS_Update3"></a> Visual Studio 2015 Update 3 的一致性改善

- **std::is_convertable 現在已可偵測自我指派** (標準程式庫)：當舊版 `std::is_convertable` 類型特性的複製建構函式遭刪除或為私用時，其無法正確地偵測類別類型的自我指派。 現在在套用到複製建構函式已刪除或為 private 的類別類型時，`std::is_convertable<>::value` 會正確設定為 **false**。

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

   在舊版 Visual C++ 中，因為 `std::is_convertable<>::value` 不當設為 **true**，導致此範例底部的靜態判斷提示能夠通過。 `std::is_convertable<>::value` 現在會正確地設定為 **false**，讓靜態判斷提示失敗。

- **預設或已刪除的 trivial 複製及移動建構函式會採用存取指定名稱**

   舊版編譯器不會檢查預設或已刪除之 trivial 複製及移動建構函式的存取指定名稱，就允許其接受呼叫。 這個舊的行為不正確，而且不符合 C++ 標準。 在某些情況下，這項舊行為的風險是會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器現在會對預設或刪除的 trivial 複製及移動建構函式進行存取指定名稱檢查，據此決定其是否可以接受呼叫；若無法呼叫，即發出編譯器警告 C2248。

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

- **屬性化 ATL 程式碼支援已標示為即將淘汰** (層級 1 (`/W1`) 預設為開啟)

   舊版編譯器支援屬性化 ATL 程式碼。 [自 Visual C++ 2008 開始下一個階段移除對屬性化 ATL 程式碼支援的下一個階段](https://msdn.microsoft.com/library/bb384632)起，即已將屬性化 ATL 程式碼標示為即將淘汰。 編譯器現在會發出編譯器警告 C4467，協助識別這類已標示為即將淘汰的程式碼。

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   若要續使用屬性化 ATL 程式碼，直到編譯器停止支援為止，可將 `/Wv:18` 或 `/wd4467` 命令列引數傳遞給編譯器，或在原始程式碼中新增 `#pragma warning(disable:4467)` 來停用此警告。

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

- **先行編譯的標頭檔 (PCH) 與不相符的 #include 指示詞** (僅會影響 `/Wall` `/WX`)

   使用先行編譯的標頭檔 (PCH) 時，舊版編譯器接受 `-Yc` 與 `-Yu` 編譯之間原始程式碼中的 `#include` 指示詞不相符。 編譯器現在已不再接受以此方式撰寫的程式碼。 現在在使用 PCH 檔案時，編譯器會發出編譯器警告 CC4598 協助識別不相符的 `#include` 指示詞。

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

- **先行編譯的標頭檔 (PCH) 與不相符的 #include 目錄** (僅會影響 `/Wall` `/WX`)

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Visual Studio 2013 中 C++ 的新功能

### <a name="improved-iso-cc-standards-support"></a>改良的 ISO C/C++ 標準支援

#### <a name="compiler"></a>編譯器

Microsoft Visual C++ 編譯器支援下列 ISO C++11 語言功能：

- 函式樣板的預設樣板引數。
- 委派建構函式
- 明確轉換運算子。
- 初始設定式清單和一致的初始化。
- 原始字串常值。
- Variadic 範本。
- 別名範本。
- 刪除的函式。
- 非靜態資料成員初始設定式 (NSDMI)。
- 預設的函式。 \*
- 支援下列 ISO C99 語言功能：
- _Bool
- 複合常值。
- 指定的初始設定式。
- 程式碼的混合宣告。
- 可以使用新的編譯器選項 `/Zc:strictStrings`，來禁止字串常值轉換為可修改的值。 在 C++98 中，從字串常值到 `char*` (以及寬字串常值到 `wchar_t*`) 的轉換已被取代。 在 C++11 中，轉換已完全移除。 雖然編譯器可以嚴格遵守這個標準，但可提供 `/Zc:strictStrings` 選項，讓您可以控制轉換。 選項預設為關閉。 請注意，當您在偵錯模式中使用這個選項時，無法編譯 STL。
- 左/右值參考轉換。 使用右值參考，C++11 可以清楚區別左值和右值。 在過去，編譯器在特定轉換情節中不提供此功能。 已新增編譯器選項 `/Zc:rvalueCast`，使編譯器符合 C++ 語言工作文件 (請參閱第 5.4 節 [expr.cast]/1)。 當這個選項未指定時的預設行為，與 Visual Studio 2012 中的預設行為相同。

> [!NOTE]
> 在預設的函式中，不支援使用 =default 要求成員移動建構函式和移動指派運算子。

### <a name="c99-libraries"></a>C99 程式庫

會針對下列標頭中遺漏的函式新增宣告和實作：math.h、ctype.h、wctype.h、stdio.h、stdlib.h 和 wchar.h。 同時新增的有新標頭 complex.h、stdbool.h、fenv.h 和 inttypes.h，以及在其中宣告之所有函式的實作。 會有新的 C++ 包裝函式標頭 (ccomplex、cfenv、cinttypes、ctgmath)，並更新許多其他 C++ 包裝函式標頭 (ccomplex、cctype、clocale、cmath、cstdint、cstdio、cstring、cwchar 和 cwctype)。

### <a name="standard-template-library"></a>標準樣板程式庫

支援 C++11 明確轉換運算子、初始設定式清單、限定範圍列舉和 variadic 範本。
所有容器現在支援 C++11 精細項目要求。
支援下列 C++14 功能：

- "透明運算子函式" less<>、greater<>、plus<>、multiplies<> 等等。
- make_unique<T>(args...) 和 make_unique<T[]>(n)
- cbegin()/cend()、rbegin()/rend() 和 crbegin()/crend() 非成員函式。
- \<atomic> 已收到許多效能加強功能。
- \<type_traits> 已收到主要穩定和程式碼修正。

### <a name="breaking-changes"></a>重大變更

這個改善的 ISO C/C++ 標準支援可能需要對現有程式碼進行變更，使其符合 C++11 並在 Visual Studio 2013 的 Visual C++ 中正確編譯。

### <a name="visual-c-library-enhancements"></a>Visual C++ 程式庫增強功能

- 已新增 C++ REST SDK。 它有 REST 服務的現代 C++ 實作。
- 已加強 C++ AMP 紋理支援。 現在包含對 Mipmap 和新的取樣模式的支援。
- PPL 工作支援多個排程技術和非同步偵錯。 新的應用程式開發介面可讓您建立一般結果和例外狀況的 PPL 工作。

### <a name="c-application-performance"></a>C++ 應用程式效能

- 自動向量化工具現在可以辨識並最佳化更多 C++ 模式，讓程式碼更快速地執行。
- ARM 平台和 Atom 微架構程式碼品質改善。
- 已新增 __vectorcall 呼叫慣例。 使用 __vectorcall 呼叫慣例傳遞向量類型引數，以使用向量暫存器。
- 新的連結器選項。 `/Gw` (編譯器) 和 `/Gy` (組譯工具) 參數會啟用連結器最佳化以產生更精簡的二進位檔。
- C++ AMP 共用記憶體支援，可降低或排除 CPU 與 GPU 之間的資料複製。

### <a name="profile-guided-optimization-pgo-enhancements"></a>特性指引最佳化 (PGO) 加強功能

- 由縮減使用 PGO 所最佳化之應用程式工作集而產生的效能提升。
- Windows 執行階段應用程式開發的新 PGO。

### <a name="windows-runtime-app-development-support"></a>Windows 執行階段應用程式開發支援

- **支援值結構中的 Boxed 類型。**

   您現在可以使用可為 null 的欄位來定義實值類型，例如 `IBox<int>^` 而非 **int**。這表示欄位可以有值或等於 **nullptr**。

- **更豐富的例外狀況資訊。**

   C++/CX 支援新 Windows 錯誤模型，能夠跨應用程式二進位介面 (ABI) 擷取及散佈豐富的例外狀況資訊，包括呼叫堆疊和自訂訊息字串。

- **Object::ToString() 現在是虛擬的。**

   您現在可以覆寫使用者定義的 Windows 執行階段 ref 類型中的 ToString。

- **支援被取代的 API。**

   公用 Windows 執行階段應用程式開發介面現在已標示為已被取代，並且有指定的、顯示為建置警告的自訂訊息，可以提供移轉指引。

- **偵錯工具改善。**

   支援原生/JavaScript Interop 偵錯、Windows 執行階段例外狀況診斷和非同步程式碼偵錯 (Windows 執行階段和 PPL)。

> [!NOTE]
> 除了本章節說明的 C++ 特定功能及功能加強外，Visual Studio 中其他功能加強也能協助您撰寫出更完善的 Windows 執行階段應用程式。

### <a name="diagnostics-enhancements"></a>診斷加強功能

- 偵錯工具改善。 支援非同步偵錯和 Just My Code 偵錯。
- 程式碼分析分類。 您現在可以檢視 [程式碼分析器] 的分類輸出，協助您尋找並修正程式碼缺失。
- XAML 診斷。 您現在可以在 XAML 中診斷 UI 回應性和電池用量問題。
- 圖形和 GPU 偵錯改進。
- 在實際的裝置上進行遠端擷取和播放。
- 同時 C++ AMP 和 CPU 偵錯。
- 改進的 C++ AMP 執行階段診斷。
- HLSL 計算著色器追蹤偵錯。

### <a name="3-d-graphics-enhancements"></a>3D 圖形加強功能

- 影像內容管線支援預乘的 Alpha DDS 格式。
- 影像編輯器使用內部預乘的 Alpha 進行轉譯，藉以避免轉譯變形 (例如深色光暈)。
- 影像和模型編輯器。 影像編輯器和模型編輯器中的著色器設計工具現在支援建立使用者定義的篩選條件。

### <a name="ide-and-productivity"></a>IDE 和產能

**改善的程式碼格式設定**。 您可以將多個格式設定套用至您的 C++ 程式碼。 您可以使用這些設定，來控制括號、關鍵字、縮排、間距和換行的新行位置。 當您完成陳述式和區塊時和當您將程式碼貼入檔案時，程式碼會自動格式化。

**以大括弧完成。** C++ 程式碼現在會自動完成對應至這些開頭字元的結尾字元：

- { (大括弧)
- [ (方括弧)
- ( (括弧)
- ' (單引號)
- " (雙引號)

**其他 C++ 自動完成功能。**

- 加入類別類型的分號。
- 完成原始字串常值的括號。
- 完成多行註解 (/\* \*/)

在顯示文字比對清單後，[尋找所有參考] 現在會自動解析並在背景中篩選參考。

**以內容為主的成員清單篩選。** 無法存取的成員會從 IntelliSense 成員清單中篩選掉。 例如，私用成員在成員清單中不會顯示，除非您修改實作類型的程式碼。 當成員清單開啟時，您可以按 **Ctrl**+**J** 移除一個篩選層級 (只適用於目前成員清單視窗)。 您可以再按一次 **Ctrl**+**J**，移除文字篩選並顯示每個成員。

**參數說明捲動。** 在參數說明工具提示中顯示的函式簽章現在會根據您實際輸入參數的數目變更，而不是根據目前內容顯示任意簽章並且不加以更新。 當它顯示在巢狀函式上時，參數說明也會正常運作。

**切換標頭/程式碼檔。** 您現在可以使用捷徑功能表上的命令或鍵盤快速鍵，在標頭和其對應的程式碼檔之間切換。

**可調整大小的 C++ 專案屬性視窗**

**C++/CX 和 C++/CLI 中的事件處理常式程式碼自動產生。**  當您輸入程式碼，在 C++/CX 或 C++/CLI 程式碼檔中加入事件處理常式時，編輯器可以自動產生委派執行個體和事件處理常式定義。 當事件處理常式程式碼可自動產生時，工具提示視窗會出現。

**DPI 感知加強功能。** 應用程式資訊清單檔案的 DPI 感知設定現在支援「以螢幕為基礎的高 DPI 感知」設定。

**更快速組態切換。** 對於大型應用程式，切換組態 (特別是後續切換作業) 執行更快速。

**建置階段效率。** 許多最佳化和多核心利用會讓建置更快速，尤其是對大型專案來說。 具有 C++ WinMD 參考的 C++ 應用程式，其累加建置同樣更加快速。

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Visual Studio 2012 中 C++ 的新功能

### <a name="improved-c11-standards-support"></a>改善的 C++11 標準支援

#### <a name="standard-template-library"></a>標準樣板程式庫

- 支援新的 STL 標頭：\<atomic>、\<chrono>、\<condition_variable>、\<filesystem>、\<future>、\<mutex>、\<ratio> 和 \<thread>。
- 為了最佳化記憶體資源使用量，現在的容器會較小。 例如，在具有預設設定的 x86 發行模式中、`std::vector` 已從 Visual Studio 2010 中的 16 個位元組壓縮為 Visual Studio 2012 中的 12 個位元組，而 `std::map` 已從 Visual Studio 2010 中的 16 個位元組壓縮為 Visual Studio 2012 中的 8 個位元組。
- 已實作 SCARY 迭代器，這對 C++11 標準而言允許但不需要。

#### <a name="other-c11-enhancements"></a>其他 C++11 加強功能

- 範圍架構的 for 迴圈。 您可以撰寫更穩固的迴圈，以處理 (for-range-declaration : expression) 形式的陣列、STL 容器和 Windows 執行階段集合。 這是核心語言支援的一部分。
- 無狀態 Lambda 是開頭為空 Lambda Introducer [] 而且未擷取區域變數，現在可隱含地轉換為 C++11 標準所需的函式指標。
- 限定範圍的列舉支援。 現在支援 C++ 列舉類別列舉索引鍵。 下列程式碼示範此列舉索引鍵與前一個列舉行為的差異。

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Windows 執行階段應用程式開發支援

- **原生 XAML UI 模型**。 對於 Windows 執行階段應用程式，您可以使用新的原生 XAML UI 模型。
- **Visual C++ 元件延伸模組**。 這些延伸模組可精簡 Windows 執行階段物件的使用，而這些物件是 Windows 執行階段應用程式的必要部分。 如需詳細資訊，請參閱[使用 C++ 的 Windows 執行階段應用程式藍圖](../windows/universal-windows-apps-cpp.md)和 [Visual C++ 語言參考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **DirectX 遊戲**。 您可以使用 Windows 執行階段應用程式的全新 DirectX 支援來開發引人入勝的遊戲。
- **XAML/DirectX Interop**。 同時使用 XAML 和 DirectX 的 Windows 執行階段應用程式現在可以有效率地共同運作。
- **Windows 執行階段元件 DLL 開發**。 元件 DLL 開發可讓您延伸 Windows 執行階段環境。

### <a name="compiler-and-linker"></a>編譯器和連結器

- **自動向量化工具**。 編譯器會分析您程式碼中的迴圈，可能的話，還會發出向量暫存器使用指示，以及所有新式處理器中的指示。 這樣可以更快速地執行迴圈。 (針對 Streaming SIMD Extensions，處理器指令稱為 SSE)。 您不需要啟用或要求此最佳化，因為會自動予以套用。
- **自動平行化工具**. 編譯器可以分析您程式碼中的迴圈，並發出將計算分散到多個核心或處理器的指示。 這樣可以更快速地執行迴圈。 您必須要求此最佳化，因為預設不予啟用。 在許多情況下，這有助於在程式碼中將 `#pragma loop(hint_parallel(N))` 包含在您想要平行化的迴圈正前方。
- 自動向量化工具和自動平行化工具可以一起運作，讓計算分散到多個核心，而每個核心上的程式碼都會使用其向量暫存器。

### <a name="new-in-visual-studio-2012-update-1"></a>Visual Studio 2012 Update 1 的新功能

當您建置 C++ 程式碼時，會以 Windows XP 為目標。
您可以使用 Visual C++ 編譯器和程式庫，以將目標設為 Windows XP 和 Windows Server 2003。

#### <a name="parallel-programming-support"></a>平行程式設計支援

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP 善用在獨立圖形顯示卡上通常呈現為 GPU 的資料平行硬體，來加速 C++ 程式碼的執行。 C++ AMP 程式設計模型包含多維陣列、索引、記憶體傳輸、並排顯示和數學函式庫。 使用 C++ AMP 語言延伸模組和編譯器限制，即可控制如何將資料從 CPU 移至 GPU 並移回。

**偵錯。** 使用 C++ AMP 以 GPU 為目標之應用程式的偵錯體驗，就像其他 C++ 應用程式的偵錯一樣。 這包含先前提到的新平行偵錯新增項目。

**分析。** 現在有根據 C++ AMP 和其他 Direct3D 程式設計模型之 GPU 活動的分析支援。

#### <a name="general-parallel-programming-enhancements"></a>一般平行程式設計加強功能

使用移至多核心和許多核心架構的硬體，開發人員可以不再依賴來自單一核心不斷增加的時脈速度。 並行執行階段中的平行程式設計支援可讓開發人員善用這些新的架構。
在 Visual Studio 2010 中，已引進功能強大的 C++ 平行化程式庫 (例如平行模式程式庫)，以及透過表現複雜資料流程管線來善用並行的功能。 在 Visual Studio 2012 中，已延伸這些程式庫，以提供開發人員最需要之平行模式的較佳效能、更多控制和更豐富支援。 供應項目的廣度現在包含：

- 可支援非同步和持續的豐富工作程式設計模型。
- 平行演算法，支援派生-聯結平行處理原則 (parallel_for、含親和性的 parallel_for、parallel_for_each、parallel_sort、parallel_reduce、parallel_transform)。
- 並行安全容器，提供標準資料結構的安全執行緒版本，例如 priority_queue、queue、vector 和 map。
- 非同步代理程式庫，開發人員可用來表示自然分解成並行單位的資料流程管線。
- 可自訂的排程器和資源管理員，以促進平滑組合此清單中的模式。

##### <a name="general-parallel-debugging-enhancements"></a>一般平行偵錯加強功能

除了 [平行工作] 視窗和 [平行堆疊] 視窗之外，Visual Studio 2012 還會提供新的 [平行監看式] 視窗讓您可以檢查跨所有執行緒和處理序的運算式值，以及對結果執行排序和篩選。 您也可以使用自己的視覺化檢視來延伸時間範圍，以及善用跨所有工具視窗的新多處理序支援。

### <a name="ide"></a>IDE

**Visual Studio 範本支援。** 您現在可以使用 Visual Studio 範本技術來編寫 C++ 專案和項目範本。

**非同步方案載入。** 現在會非同步載入專案 (先載入方案的主要部分)，讓您可以更快速地開始工作。

**遠端偵錯的自動化部署。** 已簡化 Visual C++ 中遠端偵錯的檔案部署。 專案操作功能表上的 [部署] 選項會將偵錯組態屬性中指定的檔案自動複製到遠端電腦。 不再需要手動將檔案複製至遠端電腦。

**C++/CLI IntelliSense。** C++/CLI 現在提供完整 IntelliSense 支援。 快速諮詢、參數說明、清單成員和自動完成這類 IntelliSense 功能現在適用於 C++/CLI。 此外，本文件中所列的其他 IntelliSense 和 IDE 加強功能也適用於 C++/CLI。

**更豐富的 IntelliSense 工具提示。** C++ IntelliSense 快速諮詢工具提示現在會顯示更豐富的 XML 文件註解樣式資訊。 如果您使用程式庫中具有 XML 文件註解的 API (例如，C++ AMP)，則 IntelliSense 工具提示不只會顯示宣告，還會顯示其他資訊。 此外，如果您的程式碼具有 XML 文件註解，則 IntelliSense 工具提示還會顯示更豐富的資訊。

**C++ 程式碼建構。** 基本結構程式碼適用於參數 if-else, for 迴圈，以及 [清單成員] 下拉式清單中的其他基本程式碼建構。 從清單中選取一段程式碼，以將它插入至程式碼，然後填入必要邏輯。 您也可以建立自己自訂的一段程式碼，以在編輯器中使用。

**清單成員加強功能。** 在程式碼編輯器中鍵入程式碼時，會自動顯示 [清單成員] 下拉式清單。 結果已經過篩選，因此在您鍵入時只會顯示相關成員。 您可以控制 [成員清單] 所使用的篩選邏輯類型：在 [選項] 對話方塊的 [文字編輯器] > [C/C++] > [進階] 下方。

**語意顏色標示。** 類型、列舉、巨集和其他 C++ 權杖現在預設有顏色標示。

**反白顯示參考。** 選取符號現在會反白顯示目前檔案中符號的所有執行個體。 按 **Ctrl**+**Shift**+**向上鍵**或 **Ctrl**+**Shift**+**向下鍵**，在反白顯示的參考之間移動。 您可以在 [選項] 對話方塊的 [文字編輯器] > [C/C++] > [進階] 下關閉此功能。

### <a name="application-lifecycle-management-tools"></a>應用程式生命週期管理工具

#### <a name="static-code-analysis"></a>靜態程式碼分析

已更新 C++ 靜態分析，可提供更豐富的錯誤內容資訊、其他分析規則以及更佳的分析結果。 在新的 [程式碼分析] 視窗中，您可以依關鍵字、專案和嚴重性來篩選訊息。 當您在視窗中選取訊息時，會在程式碼編輯器中反白顯示程式碼中已觸發訊息的行。 針對特定 C++ 警告，訊息會列出可顯示導致警告之執行路徑的原始程式行；會反白顯示接受該特定路徑的決策點和原因。
程式碼分析包含在大部分 Visual Studio 2012 版本中。 在 Professional、Premium 和 Ultimate Edition 中，包含所有規則。 在 Windows 8 和 Windows Phone 的 Express Edition 中，只會包含最重要的警告。 Express Edition for Web 未包含程式碼分析。
以下是一些其他程式碼分析加強功能：

- 新的並行警告可協助您避免發生並行 Bug，方法是確定您在多執行緒 C/C++ 程式中使用正確的鎖定專業領域。 分析器偵測到可能的競爭條件、鎖定順序反轉、呼叫端/被呼叫端鎖定合約違規、不相符的同步處理作業，以及其他並行 Bug。
- 您可以指定要使用規則集套用至程式碼分析回合的 C++ 規則。
- 在 [程式碼分析] 視窗中，您可以在原始程式碼中插入會隱藏所選警告的 pragma。
- 您可以加強靜態程式碼分析的正確性和完整性，方法是使用新版的 Microsoft 原始程式碼註釋語言 (SAL) 來描述函式如何使用其參數、它對它們的假設，以及完成時所進行的保證。
- 64 位元 C++ 專案支援。

#### <a name="updated-unit-test-framework"></a>已更新單元測試架構

在 Visual Studio 中使用新的 C++ 單元測試架構來撰寫 C++ 單元測試。 在 [新增專案] 對話方塊的 Visual C++ 分類下方找到 C++ 單元測試專案範本，以將新的單元測試專案新增至現有 C++ 方案。 在 Unittest1.cpp 檔案的已產生 TEST_METHOD 程式碼虛設常式中，開始撰寫單元測試。 撰寫測試程式碼時，請建置方案。 當您想要執行測試時，請依序選擇 [檢視] > [其他視窗] > [單元測試總管] 來開啟 [單元測試總管] 視窗，然後針對您想要的測試案例，在捷徑功能表上選擇 [執行選取的測試]。 測試回合完成之後，即可在相同的視窗中檢視測試結果和其他堆疊追蹤資訊。

#### <a name="architecture-dependency-graphs"></a>架構相依性圖形

若要深入了解程式碼，現在可以在方案中產生二進位、類別、命名空間和 Include 檔案的相依性圖形。 在功能表列上，選擇 [架構] > [產生相依性關係圖]，然後**針對解決方案**或**針對 Include 檔案**產生相依性關係圖。 關係圖產生完成後，即可展開每個節點進行探索、在節點之間移動來了解相依性關係，以及選擇節點捷徑功能表上的 [檢視內容] 來瀏覽原始程式碼。 若要產生 Include 檔案的相依性關係圖，請在 \*.cpp 原始程式碼檔或 \*.h 標頭檔的捷徑功能表上，選擇 [產生 Include 檔案關係圖]。

#### <a name="architecture-explorer"></a>架構總管

使用**架構總管**，即可瀏覽 C++ 解決方案、專案或檔案中的資產。 在功能表列上，依序選擇 [架構] > [視窗] > [架構總管]。 您可以選取感興趣的節點 (例如 [類別檢視])。 在此情況下，會展開含有命名空間清單的工具視窗右側。 如果您選取命名空間，則新的資料行會顯示此命名空間中的類別、結構和列舉清單。 您可以繼續瀏覽這些資產，或返回最左側的資料行來啟動另一個查詢。 請參閱**使用架構總管尋找程式碼**。

#### <a name="code-coverage"></a>程式碼涵蓋範圍

已更新程式碼涵蓋範圍，以在執行階段動態檢測二進位檔。 這會降低組態額外負荷，並提供更佳的效能。 您也可以從 C++ 應用程式的單元測試來收集程式碼涵蓋範圍資料。 建立 C++ 單元測試之後，即可使用**單元測試總管**來找出解決方案中的測試。 若要執行單元測試並收集其程式碼涵蓋範圍資料，請在 [單元測試總管] 中選擇 [分析程式碼涵蓋範圍]。 您可以在 [程式碼涵蓋範圍結果] 視窗中檢查程式碼涵蓋範圍結果；在功能表列上，依序選擇 [測試] > [視窗] > [程式碼涵蓋範圍結果]。

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Visual Studio 2010 中 C++ 的新功能

### <a name="c-compiler-and-linker"></a>C++ 編譯器和連結器

**auto 關鍵字。** **auto** 關鍵字具有新用途。 使用 **auto** 關鍵字的預設意義來宣告變數，該變數的類型是推算自變數宣告中的初始設定運算式。 `/Zc:auto` 編譯器選項會叫用 **auto** 關鍵字新或舊的意義。

**decltype 類型規範。** **decltype** 類型指定名稱會傳回指定的運算式類型。 搭配使用 **decltype** 類型指定名稱與 **auto** 關鍵字，以宣告複雜或只有編譯器才知道的類型。 例如，使用這項組合來宣告其傳回類型視範本引數類型而定的範本函式。 或是，宣告可呼叫其他函式後傳回所呼叫函式之傳回類型的範本函式。

**Lambda 運算式。** Lambda 函式只有函式主體，但沒有名稱。 Lambda 函式結合函式指標與函式物件的最佳特性。 使用 Lambda 函式本身作為範本函式參數，而不是函式物件，或是搭配使用 **auto** 關鍵字來宣告其類型為 Lambda 的變數。

**右值參考。** 右值參考宣告子 (&&) 可宣告右值的參考。 右值參考可讓您使用移動語意和完整轉寄，以撰寫更有效的建構函式、函式和範本。

**static_assert 宣告。** **static_assert** 宣告會在編譯時間測試軟體判斷提示，不像其他判斷提示機制在執行階段進行測試。 如果判斷提示失敗，則編譯會失敗，並且發出指定的錯誤訊息。

**nullptr 和 __nullptr 關鍵字。** Visual C++ 編譯器可讓您搭配使用 **nullptr** 關鍵字與機器碼或受控碼。 **nullptr** 關鍵字會指出物件控制代碼、內部指標或原生指標類型未指向物件。 當您使用 `/clr` 編譯器選項時，編譯器會將 **nullptr** 解譯為受控碼，不使用 `/clr` 選項時，則解譯為機器碼。
Microsoft 特定 **__nullptr** 關鍵字的意義與 **nullptr** 相同，但只適用於機器碼。 如果您使用 `/clr` 編譯器選項編譯原生 C/C++ 程式碼，則編譯器無法判斷 **nullptr** 關鍵字是機器或受控字詞。 為了讓編譯器清楚您的意圖，請使用 nullptr 關鍵字來指定受控字詞，並使用 **__nullptr** 指定機器字詞。

**/Zc:trigraphs 編譯器選項。** 預設會停用三併詞支援。 若要啟用三併詞的支援，可使用 `/Zc:trigraphs` 編譯器選項。
三併詞包含兩個連續的問號 (??)，後接唯一的第三個字元。 編譯器會以對應的標點符號字元取代三併詞。 例如，編譯器會將 ??= 三併詞取代為 # (數字記號) 字元。 若在 C 原始程式檔中使用的字元集不含特定標點符號字元，您可改用三併詞。

**新的特性指引最佳化選項。** PogoSafeMode 是新的特性指引最佳化選項，可讓您指定在最佳化應用程式時是要使用安全模式還是快速模式。 安全模式是安全執行緒，但速度比快速模式慢。 快速模式是預設行為。

**新的通用語言執行平台 (CLR) 選項 /clr:nostdlib。** 已新增 `/clr` (通用語言執行平台編譯) 的新選項。 如果包含相同程式庫的不同版本，則會發出編譯錯誤。 新的選項可讓您排除預設 CLR 程式庫，以讓您的程式可以使用指定的版本。

**新的 pragma 指示詞 detect_mistmatch。** pragma 指示詞 detect_mismatch 可讓您將標記放在與其他同名的標記進行比較的檔案。 如果相同的名稱有多個值，則連結器會發出錯誤。

**XOP 內建函式、FMA4 內建函式和 LWP 內建函式。** 已新增新的內建函式，以支援針對 Visual Studio 2010 SP1 所新增的 XOP 內建函式、針對 Visual Studio 2010 SP1 所新增的 FMA4 內建函式，以及針對 Visual Studio 2010 SP1 處理器技術所新增的 LWP 內建函式。 使用 __cpuid、__cpuidex 來判斷特定電腦上支援的處理器技術。

### <a name="visual-c-projects-and-the-build-system"></a>Visual C++ 專案和組建系統

**MSBuild。** Visual C++ 方案和專案現在使用 MSBuild.exe 所建置，而此檔案會取代 VCBuild.exe。 MSBuild 是相同彈性且可延伸的 XML 建置工具，供其他 Visual Studio 語言和專案類型使用。 因為這項變更，所以 Visual C++ 專案檔現在使用 XML 檔案格式，而且副檔名為 .vcxproj。 舊版 Visual Studio 中的 Visual C++ 專案檔會自動轉換成新的檔案格式。

**VC++ 目錄。** VC++ 目錄設定現在位於兩個地方。 使用專案屬性頁面來設定 VC++ 目錄的每一專案值。 使用**屬性管理員**和屬性工作表來設定 VC++ 目錄的全域每一組態值。

**專案對專案相依性。** 在舊版本中，專案之間的已定義相依性已儲存在方案檔中。 這些方案轉換成新的專案檔格式時，相依性會轉換成專案對專案參考。 因為方案相依性和專案對專案參考的概念不同，所以這項變更可能會影響應用程式。

**巨集和環境變數。** 新的 _ITERATOR_DEBUG_LEVEL 巨集會叫用迭代器的偵錯支援。 使用這個巨集，而不是較舊的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 巨集。

### <a name="visual-c-libraries"></a>Visual C++ 程式庫

**並行執行階段程式庫。** 並行執行階段架構支援同時執行的應用程式和元件，而且是在 Visual C++ 中透過程式設計並行應用程式的架構。 為了支援並行應用程式設計，平行模式程式庫 (PPL) 提供一般用途的容器和演算法來執行細部平行處理原則。 非同步代理程式程式庫提供以執行者項目為基礎的程式設計模型和訊息傳遞介面，以進行粗略的資料流程和管線工作。

**標準 C++ 程式庫。** 下列清單描述許多已對標準 C++ 程式庫進行的變更。

- 新的右值參考 C++ 語言功能已用來實作標準範本程式庫中許多函式的移動語意和完整轉寄。 移動語意和完整轉寄可大幅改善用以配置或指派變數或參數之作業的效能。
- 右值參考也用來實作新的 `unique_ptr` 類別，而此類別是比 `auto_ptr` 類別更安全的智慧型指標類型。 `unique_ptr` 類別是可移動但無法複製、實作不影響安全性的嚴格擁有權語意，而且適用於了解右值參考的容器。 `auto_ptr` 類別即將淘汰。
- 舉例來說，第十五個新函式 `find_if_not`、`copy_if` 和 `is_sorted` 已新增到 \<algorithm> 標頭。
- 在 \<memory> 標頭中，新的 make_shared 函式是一種方便、穩固且有效率的方式，可在建構物件的同時設定物件的共用指標。
- \<forward_list> 標頭支援單一連結清單。
- 新的 `cbegin`、`cend`、`crbegin` 和 `crend` 成員函式會提供透過容器向前或向後移動的 `const_iterator`。
- \<system_error> 標頭和相關範本支援處理低階系統錯誤。 `exception_ptr` 類別的成員可以用來傳輸執行緒之間的例外狀況。
- \<codecvt> 標頭支援將 Unicode 字元的各種編碼轉換成其他編碼。
- \<allocators> 標頭定義數個範本，協助配置和釋放節點容器的記憶體區塊。
- \<random> 標頭有許多更新。

### <a name="microsoft-foundation-class-mfc-library"></a>Microsoft Foundation Class (MFC) 程式庫

**Windows 7 功能。** MFC 支援許多 Windows 7 功能，例如功能區使用者介面 (UI)、工作列、跳躍清單、索引標籤式縮圖、縮圖預覽、進度列、圖示重疊和搜尋索引。 因為 MFC 會自動支援許多 Windows 7 功能，所以您可能不需要修改現有應用程式。 若要在新的應用程式中支援其他功能，請使用 [MFC 應用程式精靈] 來指定您想要使用的功能。

**多點觸控感知。** MFC 支援的應用程式具有多點觸控使用者介面；例如，針對 Microsoft Surface 作業系統所撰寫的應用程式。 多點觸控應用程式可以處理 Windows 觸控訊息和手勢訊息，其為觸控式訊息的組合。 只需要註冊應用程式的觸控和手勢事件，而且作業系統會將多點觸控事件傳送至事件處理常式。

**高 DPI 感知。** 根據預設，MFC 應用程式現在是高 DPI 感知。 如果應用程式是高 DPI (高像素/點) 感知，則作業系統可以將視窗、文字和其他 UI 項目調整為目前螢幕解析度。 這表示縮放的影像更容易正確進行配置，但未裁剪或不美觀。

**重新啟動管理員。** 重新啟動管理員會自動儲存文件，並在文件未預期關閉或重新啟動時重新啟動應用程式。 例如，您可以使用重新啟動管理員，以啟動由自動更新所關閉的應用程式。 如需如何設定應用程式使用重新啟動管理員的詳細資訊，請參閱**如何：新增重新啟動管理員支援**。

**CTaskDialog。** `CTaskDialog` 類別可以用來取代標準的 `AfxMessageBox` 訊息方塊。 `CTaskDialog` 類別所顯示和收集的資訊，比標準訊息方塊更多。

#### <a name="safeint-library"></a>SafeInt 程式庫

新的 SafeInt 程式庫會執行可處理整數溢位的安全算術作業。 此程式庫也會比較不同類型的整數。

#### <a name="new-active-template-library-atl-macros"></a>新的 Active Template Library (ATL) 巨集

已將新巨集新增至 ATL，以展開 PROP_ENTRY_TYPE 和 PROP_ENTRY_TYPE_EX 的功能。 PROP_ENTRY_INTERFACE 和 PROP_ENTRY_INTERFACE_EX 可讓您新增有效的 CLSID 清單。 PROP_ENTRY_INTERFACE_CALLBACK 和 PROP_ENTRY_INTERFACE_CALLBACK_EX 可讓您指定回呼函式來判斷 CLSID 是否有效。

#### <a name="analyze-warnings"></a>/analyze 警告

已從 C 執行階段 (CRT)、MFC 和 ATL 程式庫移除大部分 `/analyze` (企業程式碼分析) 警告。

#### <a name="animation-and-d2d-support"></a>動畫和 D2D 支援

MFC 現在支援動畫和 Direct2D 圖形。 MFC 程式庫有數個新的 MFC 類別和函式來支援這項功能。 還有兩個新的逐步解說，示範如何將 D2D 物件和動畫物件新增至專案。 這些逐步解說是**逐步解說：將 D2D 物件新增至 MFC 專案**和**逐步解說：將動畫新增至 MFC 專案**。

### <a name="ide"></a>IDE

**改善的 IntelliSense。** IntelliSense for Visual C++ 已完全重新設計，目前更為快速、更精確，並且能夠處理較大型的專案。 為了達成這項改善，IDE 會區分開發人員如何檢視和修改原始程式碼，以及 IDE 如何使用原始程式碼和專案設定來建置方案。
基於這項責任區隔，如果系統依據取代舊無編譯瀏覽 (.ncb) 檔案的新 SQL Server 桌面資料庫 (.sdf) 檔案，則可以處理 [類別檢視] 和新的 [巡覽至] 對話方塊這類瀏覽功能。 只有在必要時，快速資訊、自動完成和參數說明這類 IntelliSense 功能才會剖析轉譯單位。 新的 [呼叫階層] 視窗這類混合式功能使用瀏覽與 IntelliSense 功能的組合。
因為 IntelliSense 只會處理您當時所需的資訊，所以 IDE 回應更為迅速。 此外，因為資訊是最新的，所以 IDE 檢視和視窗更為精確。 最後，因為 IDE 基礎結構更有組織、更有能力，更具擴充性，所以它可以處理較大型的專案。

**改善的 IntelliSense 錯誤。** IDE 可以更適當地偵測到可能導致 IntelliSense 遺失的錯誤，並在其下顯示紅色波浪底線。 此外，IDE 會向 **[錯誤清單] 視窗**報告 IntelliSense 錯誤。 若要顯示造成問題的程式碼，請按兩下 **[錯誤清單] 視窗**中的錯誤。

**#include 自動完成功能。** IDE 支援 `#include` 關鍵字的自動完成。 鍵入 `#include` 時，IDE 會建立有效標頭檔的下拉式清單方塊。 如果您繼續鍵入檔案名稱，則 IDE 會根據您的輸入來篩選清單。 您隨時都可以從清單中選取您想要包含的檔案。 這可讓您快速包含檔案，而不需要知道確切的檔案名稱。

**巡覽至。** [巡覽至] 對話方塊可讓您搜尋專案中符合指定字串的所有符號和檔案。 當您在搜尋字串中鍵入其他字元時，會立即修訂搜尋結果。 [結果] 回饋欄位會告知找到的項目數，並協助決定是否限制搜尋。 [種類/範圍]、[位置] 和 [預覽] 回饋欄位可協助您釐清具有類似名稱的項目。 此外，您可以延伸這項功能，來支援其他程式設計語言。

**平行偵錯和分析。** Visual Studio 偵錯工具具有並行執行階段感知，而且可協助您針對平行處理應用程式進行疑難排解。 您可以使用新的並行分析工具來視覺化您應用程式的整體行為。 此外，您可以使用新的工具視窗來視覺化工作的狀態和其呼叫堆疊。

**功能區設計工具。** **功能區設計工具**是圖形化編輯器，可讓您建立和修改 MFC 功能區 UI。 最終功能區 UI 是以 XML 為基礎的資源檔 (.mfcribbon-ms) 呈現。 若是現有的應用程式，您可以暫時新增幾行程式碼，然後叫用**功能區設計工具**，來擷取目前功能區 UI。 建立功能區資源檔之後，即可將手寫的功能區 UI 程式碼取代為幾個可載入功能區資源的陳述式。

**呼叫階層。** [呼叫階層] 視窗可讓您巡覽至特定函式所呼叫的所有函式，或呼叫特定函式的所有函式。

### <a name="tools"></a>工具

**MFC 類別精靈。** Visual C++ 2010 會帶回良好相關的 [MFC 類別精靈] 工具。 [MFC 類別精靈] 是將類別、訊息和變數新增至專案的便利方式，而不需要手動修改原始程式檔集合。

**ATL 控制項精靈。** ATL 控制項精靈不會自動填入 `ProgID` 欄位。 如果 ATL 控制項沒有 `ProgID`，其他工具可能無法加以使用。 [插入使用中控制項] 對話方塊，即為工具需要控控制項擁有 `ProgID` 的其中一例。 如需對話方塊的詳細資訊，請參閱**插入 ActiveX 控制項對話方塊**。

### <a name="microsoft-macro-assembler-reference"></a>Microsoft 巨集組合程式參考

YMMWORD 資料類型的新增可支援 Intel Advanced Vector Extensions (AVX) 指示中所含的 256 位元多媒體運算元。

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Visual Studio 2008 中 C++ 的新功能

### <a name="visual-c-integrated-development-environment-ide"></a>Visual C++ 整合式開發環境 (IDE)

- 在 ATL、MFC 和 Win32 應用程式中建立的對話方塊現在會遵守 Windows Vista 樣式指導方針。 當您使用 Visual Studio 2008 建立新的專案時，所有您插入至應用程式的對話方塊都會遵守 Windows Vista 樣式指導方針。 如果您重新編譯您使用舊版 Visual Studio 所建立的專案，則任何現有對話方塊的外觀都會與先前的外觀相同。 如需如何將對話方塊插入應用程式中的詳細資訊，請參閱**對話方塊編輯器**。

- **ATL 專案**精靈現在有選項可以註冊所有使用者的元件。 從 Visual Studio 2008 開始，除非您選取 [註冊所有使用者的元件]，否則 **ATL 專案**精靈所建立的 COM 元件和類型庫會註冊於登錄的 HKEY_CURRENT_USER 節點中。
- **ATL 專案**精靈不再提供選項來建立屬性化 ATL 專案。 自 Visual Studio 2008 起，**ATL 專案**精靈不再提供變更新專案屬性化狀態的選項。 現在未歸屬精靈所建立的所有新 ATL 專案。
- 可以重新導向寫入登錄。 引進 Windows Vista 之後，寫入登錄的特定區域則需要以提升權限模式執行程式。 不適合一律以提升權限模式執行 Visual Studio。 個別使用者重新導向會將登錄寫入從 HKEY_CLASSES_ROOT 自動重新導向到 HKEY_CURRENT_USER，而不需要進行任何程式設計變更。
- 現在，**類別設計工具**的原生 C++ 程式碼支援有限。 在舊版 Visual Studio 中，**類別設計工具**只能與 Visual C# 和 Visual Basic 搭配使用。 C++ 使用者現在可以使用**類別設計工具**，但只能是唯讀模式。 如需如何搭配使用**類別設計工具**與 C++ 的詳細資訊，請參閱**在類別設計工具中使用 Visual C++ Code**。
- 此專案精靈不再有選項可以建立 C++ SQL Server 專案。 自 Visual Studio 2008 起，[新增專案精靈] 不再提供建立 C++ SQL Server 專案的選項。 使用舊版 Visual Studio 建立的 SQL Server 專案仍可正常地編譯及運作。

### <a name="visual-c-libraries"></a>Visual C++ 程式庫

#### <a name="general"></a>一般

- 應用程式可以繫結至特定版本的 Visual C++ 程式庫。 應用程式有時取決於發行後對 Visual C++ 程式庫進行的更新。 在此情況下，在具有舊版程式庫的電腦上執行應用程式可能會導致非預期的行為。 您現在可以將應用程式繫結至特定版本的程式庫，讓它不要在具有舊版程式庫的電腦上執行。

#### <a name="stlclr-library"></a>STL/CLR 程式庫

- Visual C++ 現在包含 STL/CLR 程式庫。 STL/CLR 程式庫是本身為標準 C++ 程式庫子集之標準範本庫 (STL) 的包裝，以與 C++ 和 .NET Framework 通用語言執行平台 (CLR) 搭配使用。 使用 STL/CLR，您現在可以在受控環境中使用所有容器、迭代器和 STL 演算法。

#### <a name="mfc-library"></a>MFC 程式庫

- Windows Vista 支援通用控制項。 已在 18 個新或現有類別中新增超過 150 種方法，支援 Windows Vista 中的功能，或改善目前 MFC 類別中的功能。
- 新的 `CNetAddressCtrl` 類別可讓您輸入與驗證 IPv4 和 IPv6 位址或 DNS 名稱。
- 新的 `CPagerCtrl` 類別可簡化 Windows 頁面巡覽區控制項的使用。
- 新的 `CSplitButton` 類別可簡化 Windows splitbutton 控制項的使用，來選取預設或選擇性動作。

#### <a name="c-support-library"></a>C++ 支援程式庫

- C++ 引進封送處理程式庫。 封送處理程式庫提供簡單且最佳化的方式，來封送處理原生與受控環境之間的資料。 此程式庫是使用 PInvoke 這類更複雜且較不具效率之方法的替代方式。 如需詳細資訊，請參閱 **C++ 中的封送處理概觀**。

#### <a name="atl-server"></a>ATL Server

- ATL Server 是發行為共用原始碼專案。
- 大部分 ATL Server 程式碼基底都已發行到 CodePlex 成為共用原始碼專案，而且未安裝為 Visual Studio 2008 的一部分。 有幾個與 ATL Server 相關聯的檔案已不再屬於 Visual Studio 的一部分。 如需移除的檔案清單，請參閱**移除的 ATL Server 檔案**。
- atlenc.h 中的資料編碼和解碼類別，以及 atlutil.h 與 atlpath.h 中的公用程式函式和類別現在都是 ATL 程式庫的一部分。
- 只要支援舊版 Visual Studio 所含的 ATL Server 版本，Microsoft 就會繼續支援這些 Visual Studio 版本。 CodePlex 會繼續將 ATL Server 程式碼開發為社群專案。 Microsoft 不支援 ATL Server 的 CodePlex 版本。

### <a name="visual-c-compiler-and-linker"></a>Visual C++ 編譯器和連結器

#### <a name="compiler-changes"></a>編譯器變更

- 編譯器支援受控累加建置。 如果您指定這個選項，則編譯器不會在參考的組件變更時重新編譯程式碼。 相反地，它會執行累加建置。 只有在變更影響相依的程式碼時，才會重新編譯檔案。
- 不再支援與 ATL Server 相關的屬性。 編譯器不再支援數個直接與 ATL Server 相關的屬性。 如需已移除屬性的完整清單，請參閱＜重大變更＞。
- 編譯器支援 Intel Core 微架構。 編譯器包含在程式碼產生期間微調 Intel Core 微架構。 預設會啟用這項調整，而且無法予以停用，因為它也可協助 Pentium 4 和其他處理器。
- 內建函式支援較新的 AMD 和 Intel 處理器。 數個新的內建指令支援較新 AMD 和 Intel 處理器中的更強大功能。 如需新內建函式的詳細資訊，請參閱**補充 Streaming SIMD Extensions 3 指令**、**Streaming SIMD Extensions 4 指令**、**SSE4A 和 Advanced Bit Manipulation 內建函式**、**AES 內建函式**、**_mm_clmulepi64_si128** 和 **__rdtscp**。
- `__cpuid` 函式已更新。 `__cpuid`、`__cpuidex` 函式現在支援 AMD 和 Intel 處理器最新修訂中的數個新功能。 `__cpuidex` 內建函式是新的，並且收集最新處理器的詳細資訊。
- `/MP` 編譯器選項可減少總建置時間。 `/MP` 選項可以大幅降低編譯數個原始程式檔的總時間，方法是建立數個同時編譯檔案的處理序。 這個選項特別適用於支援超執行緒、多個處理器或多個核心的電腦。
- `/Wp64` 編譯器選項和 **__w64** 關鍵字即將淘汰。 能夠偵測 64 位元可攜性問題的 `/Wp64` 編譯器選項和 **__w64** 關鍵字即將淘汰，會在編譯器的未來版本中移除。 請使用以 64 位元平台為目標的 Visual C++ 編譯器，而不是這個編譯器選項和關鍵字。
- `/Qfast_transcendentals` 會為超越函式產生內嵌程式碼。
- 當您使用 `/fp:except` 編譯器選項時，`/Qimprecise_fwaits` 會移除 try 區塊內部的 fwait 命令。

### <a name="linker-changes"></a>連結器變更

- Visual C++ 連結器 (link.exe) 現在會將使用者帳戶控制資訊內嵌到可執行檔的資訊清單檔。 預設會啟用此功能。 如需如何停用此功能或修改預設行為的詳細資訊，請參閱 `/MANIFESTUAC` (將 UAC 資訊內嵌在資訊清單中)。
- 連結器現在有 `/DYNAMICBASE` 選項，可啟用 Windows Vista 的位址空間配置隨機功能。 這個選項修改可執行檔的標頭，指出是否應該在載入時間為應用程式隨機重定基底。

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Visual Studio 2005 中 C++ 的新功能

下列是 Visual C++ 2005 Service Pack 1 的新功能：

### <a name="intrinsics-for-x86-and-x64"></a>x86 和 x64 的內建函式

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>僅限 x64 的內建函式

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>新的語言關鍵字

__sptr、__uptr

### <a name="new-compiler-features"></a>新的編譯器功能

編譯器在此版本中有重大變更。

- `64 位元原生和跨編譯器。
- 已新增 `/analyze` (企業程式碼分析) 編譯器選項。
- 已新增 `/bigobj` 編譯器選項。
- 已新增 `/clr:pure`、`/clr:safe` 和 `/clr:oldSyntax`。 (之後在 Visual Studio 2015 中被取代，並在 Visual Studio 2017 被移除。)
- 淘汰的編譯器選項：在此版本中，淘汰了許多編譯器選項；如需詳細資訊，請參閱**淘汰的編譯器選項**。
- 已減少 `/clr` 程式碼中的 Double Thunking；如需詳細資訊，請參閱 **Double Thunking (C++)**。
- `/EH` (例外狀況處理模型) 或 `/EHs` 不再用來攔截因擲回以外的事件而引發的例外狀況；請使用 `/EHa`。
- 已新增 `/errorReport` (回報內部編譯器錯誤) 編譯器選項。
- 已新增 `/favor` (最適用於 64) 編譯器選項。
- 已新增 `/FA`、`/Fa` (清單檔) 編譯器選項。
- 已新增 `/FC` (診斷中原始程式碼檔的完整路徑) 編譯器選項。
- 已新增 `/fp` (指定浮點數行為) 編譯器選項。
- 已新增 `/G` (最適用於處理器) 選項編譯器選項。
- 已新增 `/G` (最適用於處理器) 選項編譯器選項。
- 已移除 `/G3`、`/G4`、`/G5`、`/G6`、`/G7`及 `/GB` 編譯器選項。 編譯器現在會使用「混合模型」，以嘗試建立所有架構的最佳輸出檔。
- 已移除 `/Gf`。 請改用 `/GF` (消除重複字串)。
- `/GL` (整個程式最佳化) 現在與 `/CLRHEADER` 相容。
- 根據預設，`/GR` 現在會開啟。
- `/GS` (緩衝區安全性檢查) 現在提供易受攻擊指標參數的安全性保護。 根據預設，`/GS` 現在會開啟。 `/GS` 現在也適用於使用 `/clr` (通用語言執行平台編譯) 編譯為 MSIL 的函式。
- 已新增 `/homeparams` (將暫存器參數複製到堆疊) 編譯器選項。
- 已新增 `/hotpatch` (建立可線上修補的映像) 編譯器選項。
- 已更新內嵌函式啟發學習法；如需詳細資訊，請查看 **inline**、**__inline**、**__forceinline** 和 **inline_depth**
- 已新增許多新的內建函式，而且現在記載許多先前未記載的內建函式。
- 任何失敗的 new 呼叫預設會擲回例外狀況。
- 已移除 `/ML`和 `/MLd` 編譯器選項。 Visual C++ 不再支援單一執行緒、靜態連結的 CRT 程式庫支援。
- 編譯器已實作具名傳回值最佳化，而其啟用時機是使用 `/O1`、`/O2` (大小最小、速度最快)、`/Og` (全域最佳化) 和 `/Ox` (完全最佳化) 進行編譯時。
- 已移除 `/Oa` 編譯器選項，但會自動忽略；請使用 `noalias` 或 `restrict__declspec` 修飾詞指定編譯器如何進行混淆。
- 已移除 `/Op` 編譯器選項。 請改用 `/fp` (指定浮點數行為)。
- Visual C++ 現在支援 OpenMP。
- 已新增 `/openmp` (啟用 OpenMP 2.0 支援) 編譯器選項。
- 已移除 `/Ow` 編譯器選項，但會自動忽略。 請使用 `noalias` 或 `restrict__declspec` 修飾詞指定編譯器如何進行混淆。

### <a name="profile-guided-optimizations"></a>特性指引最佳化

- 已移除 `/QI0f`。
- 已移除 `/QIfdiv`。
- 已新增 `/QIPF_B` (B CPU 逐步偵錯的 Errata) 編譯器選項。
- 已新增 `/QIPF_C` (C CPU 逐步偵錯的 Errata) 編譯器選項。
- 已新增 `/QIPF_fr32` (請勿使用上層的 96 浮點數暫存器) 編譯器選項。
- 已新增 `/QIPF_noPIC` (產生與位置有關的程式碼) 編譯器選項。
- 已新增 `/QIPF_restrict_plabels` (假設在執行階段並未建立函式) 編譯器選項。

### <a name="unicode-support-in-the-compiler-and-linker"></a>編譯器和連結器中的 Unicode 支援

- `/vd` (停用建構置換) 現在可讓您在所建構的物件上使用 dynamic_cast 運算子 (/vd2)
- 已移除 `/YX` 編譯器選項。 請改用 `/Yc` (建立先行編譯標頭檔) 或 `/Yu` (使用先行編譯標頭檔)。 如果您從組建組態中移除 `/YX`，而且未予以取代，則可能會導致更快速的建置。
- 根據預設，`/Zc:forScope` 現在會開啟。
- 根據預設，`/Zc:wchar_t` 現在會開啟。
- 已移除 `/Zd` 編譯器選項。 不再支援僅行號偵錯資訊。 請改用 `/Zi` (如需詳細資訊，請參閱 **/Z7、/Zi、/ZI (偵錯資訊格式)**)。
- `/Zg` 現在僅適用於 C 原始程式碼檔，而不適用於 C++ 原始程式碼檔。
- 已新增 `/Zx` (偵錯最佳化 Itanium 程式碼) 編譯器選項。

### <a name="new-language-features"></a>新的語言功能

- Attributeattribute 現在已被取代。
- 已新增 `appdomain__declspec` 修飾詞。
- 已新增 `__clrcall` 呼叫慣例。
- 當使用者嘗試存取即將淘汰的類別或函式時，即將淘汰的 (C++) **declspec** 修飾詞現在可讓您指定要在編譯時間顯示的字串。
- **dynamic_cast** 運算子有中斷性變更。
- 原生列舉現在可讓您指定基礎類型。
- 已新增 `jitintrinsicdeclspec` 修飾詞。
- 已新增 `noaliasdeclspec` 修飾詞。
- 已新增 `process__declspec` 修飾詞。
- **抽象**、**覆寫**和**密封**適用於原生編譯。
- 已新增 **__restrict** 關鍵字。
- 已新增 `restrictdeclspec` 修飾詞。
- **__thiscall** 現在是關鍵字。
- 現在已記載 **__unaligned** 關鍵字。
- **volatile** (C++) 具有與最佳化相關的已更新行為。

### <a name="new-preprocessor-features"></a>新的前置處理器功能

- 已新增 __CLR_VER 預先定義巨集。
- 註解 (C/C++) pragma 現在接受 `/MANIFESTDEPENDENCY` 當作連結器註解。 要註解的 exestr 選項現在已被取代。
- `embedded_idl` 屬性 (`#import` 指示詞) 現在接受選擇性參數。
- `fenv_access` pragma
- `float_control` pragma
- `fp_contract` pragma
- 如果您在 pragma 受控、非受控和非受控區段中有全域變數，則不會以宣告順序來初始化全域變數。 例如，如果使用受控全域變數初始化非受控全域變數，而且需要完全建構的受控物件，則這可能是重大變更。
- 使用 init_seg 所指定的區段現在是唯讀的，而不是與舊版本一樣是讀寫。
- inline_depth 預設值現在是 16。 預設值 16 也作用於 Visual C++ .NET 2003。
- 已新增 _INTEGRAL_MAX_BITS 預先定義巨集，請參閱＜預先定義巨集＞。
- 已新增 _M_CEE、_M_CEE_PURE 和 _M_CEE_SAFE 預先定義巨集，請參閱＜預先定義巨集＞。
- 已新增 _M_IX86_FP 預先定義巨集。
- 已新增 _M_X64 預先定義巨集。
- `make_public` pragma
- 已更新 `managed`、`unmanaged` pragma 語法 (現在有 `push` 和 `pop`)
- 在所有 `/clr` 編譯中，`#using` 指示詞現在都會隱含參考 mscorlib.dll。
- 已新增 _OPENMP 預先定義巨集。
- 已更新最佳化 pragma，a 和 w 不再是有效的參數。
- 已新增 no_registry#import 屬性。
- 已新增 `region`、`endregion` pragma
- 已新增 _VC_NODEFAULTLIB 預先定義巨集。
- 現在已實作 Variadic 巨集。
- `vtordisp` 即將淘汰，將在未來的 Visual C++ 版本中移除。
- `warning` pragma 現在具有隱藏指定名稱。

### <a name="new-linker-features"></a>新的連結器功能

- 不允許模組 (非組件 MSIL 輸出檔) 作為連結器的輸入。
- 已新增 `/ALLOWISOLATION` (資訊清單查閱) 連結器選項。
- `/ASSEMBLYRESOURCE` (內嵌受控資源) 已經過更新，現在可讓您指定組件中資源的名稱，以及指定資源在組件中是私用的。
- 已新增 `/CLRIMAGETYPE` (指定 CLR 映像類型) 連結器選項。
- 已新增 `/CLRSUPPORTLASTERROR` (保留最後的 PInvoke 呼叫錯誤碼) 連結器選項。
- 已新增 `/CLRTHREADATTRIBUTE` (設定 CLR 執行緒屬性) 連結器選項。
- 已新增 `/CLRUNMANAGEDCODECHECK` (新增 SuppressUnmanagedCodeSecurityAttribute) 連結器選項。
- 已新增 `/ERRORREPORT` (回報內部連結器錯誤) 連結器選項。
- 已移除 `/EXETYPE` 連結器選項。 連結器不再支援建立 Windows 95 和 Windows 98 裝置驅動程式。 使用適當的 DDK 來建立這些裝置驅動程式。 EXETYPE 關鍵字不再適用於模組定義檔。
- 已新增 `/FUNCTIONPADMIN` (建立可線上修補的映像) 連結器選項。
- 在使用 `/clr` 所編譯的模組上，現在支援 `/LTCG` 連結器選項。 `/LTCG`也已更新，以支援特性指引最佳化。
- 已新增 `/MANIFEST` (建立並存資訊清單) 連結器選項。
- 已新增 `/MANIFESTDEPENDENCY` (指定資訊清單相依性) 連結器選項。
- 已新增 `/MANIFESTFILE` (為資訊清單檔案命名) 連結器選項。
- 已移除 `/MAPINFO:LINES` 連結器選項。
- 已新增 `/NXCOMPAT` (與資料執行防止相容) 連結器選項。
- 已新增 `/PGD` (指定特性指引最佳化的資訊庫) 連結器選項。
- 已新增 `/PROFILE` (效能工具分析工具) 連結器選項。
- `/SECTION` (指定區段屬性) 連結器選項現在支援屬性否定，且不再支援 L 或 D (VxD 相關) 屬性。
- 編譯器和連結器中的 Unicode 支援
- `/VERBOSE` (列印進度訊息) 連結器選項現在也接受 ICF 和 REF。
- 已移除 `/VXD` 連結器選項。 連結器不再支援建立 Windows 95 和 Windows 98 裝置驅動程式。 使用適當的 DDK 來建立這些裝置驅動程式。 VXD 關鍵字不再適用於模組定義檔。
- 已移除 `/WS` 連結器選項。 使用了 `/WS` 來修改以 Windows NT 4.0 為目標的映像。 可以使用 IMAGECFG.exe -R 檔案名稱來取代 `/WS`。 在 Windows NT 4.0 CD-ROM 的 SUPPORT\DEBUG\I386\IMAGECFG.EXE 中，可以找到 IMAGECFG.exe。
- 現在會記載 `/WX` (將連結器警告視為錯誤) 連結器選項。

### <a name="new-linker-utility-features"></a>新的連結器公用程式功能

- 以新增 `/ALLOWISOLATION` editbin 選項
- 已移除 DESCRIPTION 模組定義檔陳述式。 連結器不再支援建置虛擬裝置驅動程式。
- `/ERRORREPORT` 選項已新增至 bscmake.exe、dumpbin.exe、editbin.exe 和 lib.exe。
- 已新增 `/LTCG` lib 選項。
- 以新增 `/NXCOMPAT` editbin 選項。
- 已新增 `/RANGE` dumpbin 選項。
- 已新增 `/TLS` dumpbin 選項。
- 已移除 `/WS` editbin 選項。 使用了 `/WS` 來修改以 Windows NT 4.0 為目標的映像。 可以使用 IMAGECFG.exe -R 檔案名稱來取代 `/WS`。 在 Windows NT 4.0 CD-ROM 的 SUPPORT\DEBUG\I386\IMAGECFG.EXE 中，可以找到 IMAGECFG.exe。
- 已新增 /WX[:NO] lib 選項。

### <a name="new-nmake-features"></a>新的 NMAKE 功能

- 已新增 `/ERRORREPORT`。
- 已新增 `/G`。
- 已更新預先定義的規則。
- ＜遞迴巨集＞中所記載的 $(MAKE) 巨集現在提供 nmake.exe 的完整路徑。

### <a name="new-masm-features"></a>新的 MASM 功能

- MASM 運算式現在是 64 位元值。 在舊版本中，MASM 運算式是 32 位元值。
- __asm int 3 指令現在會導致函式編譯為原生。
- 現在已記載 ALIAS (MASM)。
- 已新增 `/ERRORREPORT` ml.exe 和 ml64.exe 選項。
- 現在已記載 .FPO。
- Visual C++ 2005 不會隨附 H2INC.exe。 如果您需要繼續使用 H2INC，請使用舊版 Visual C++ 中的 H2INC.exe。
- 已新增 IMAGEREL 運算子。
- 已新增 HIGH32 運算子。
- 已新增 LOW32 運算子。
- ml64.exe 是 x64 架構的 MASM 版本。 它會將 x64 .asm 檔案組譯為 x64 物件檔案。 x64 編譯器不支援內嵌組件語言。 已新增 ml64.exe (x64) 的下列 MASM 指示詞：
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- .SETFRAME；此外，已使用僅限 x64 語法來更新 PROC 指示詞。
- 已新增 MMWORD 指示詞
- `/omf` (ML.exe 命令列選項) 現在表示 `/c`。 ML.exe 不支援連結 OMF 格式物件。
- SEGMENT 指示詞現在支援額外屬性。
- 已新增 SECTIONREL 運算子。
- 已新增 XMMWORD 指示詞

### <a name="new-crt-features"></a>新的 CRT 功能

- 已新增數個函式的安全版本。 這些函式會以更好的方式處理錯誤，並在緩衝區上強制執行更嚴格的控制項，協助避免常見的安全性問題。 新的安全版本是依 **_s** 尾碼進行識別。
- 許多函式的現有較不安全版本已被取代。 若要停用取代警告，請定義 _CRT_SECURE_NO_WARNINGS。
- 傳遞無效的參數時，許多現有函式現在都會驗證其參數，並叫用無效的參數處理常式。
- 許多現有函式現在會設定先前沒有的 `errno`。
- 已新增 integer 類型的 typedef `errno_t`。 只要函式傳回類型或參數處理了來自 `errno` 的錯誤碼，就會使用 `errno_t`。 `errno_t` 會取代 `errcode`。
- 地區設定相關函式現在有版本可以接受地區設定作為參數，而不是使用目前地區設定。 這些新的函式具有 **_l** 尾碼。 已新增許多新函式，以使用地區設定物件。 新的函式包括 `_get_current_locale`、`_create_locale` 和 `_free_locale`。
- 已新增新的函式，以支援檔案控制代碼的鎖定和解除鎖定。
- `_spawn` 函式系列不會在成功時將 errno 重設為零，但在舊版本中會這麼做。
- 有可讓您指定引數使用順序的 `printf` 函式系列版本可供使用。
- Unicode 現在是支援的文字格式。 `_open` 函式支援 _O_TEXTW、_O_UTF8 和 _O_UTF16 屬性。 `fopen` 函式支援 "ccs=ENCODING" 方法來指定 Unicode 格式。
- 以受控碼 (MSIL) 來建置的新版 CRT 程式庫現在可供使用，並會在透過 `/clr` (通用語言執行平台編譯) 選項進行編譯時使用。
- 已移除 _fileinfo。
- `time_t` 的預設大小現在是 64 位元，以將 `time_t` 範圍和數個時間函式擴展為 3000 年。
- CRT 現在支援設定每個執行緒的地區設定。 已新增 `_configthreadlocale` 函式以支援此功能。
- 已新增 `_statusfp2` 和 `__control87_2` 函式，允許存取和控制 x87 和 SSE2 浮點處理器上的浮點數控制字組。
- 已新增 `_mkgmtime` 和 `_mkgmtime64` 函式，支援將時間 (struct tm) 轉換成格林威治標準時間 (GMT)。
- 已對 `swprintf` 和 `vswprintf` 進行變更，使其更貼近標準。
- 新的標頭檔 INTRIN.H 提供一些內建函式的原型。
- `fopen` 函式現在有 N 屬性。
- `_open` 函式現在有 _O_NOINHERIT 屬性。
- `atoi` 函式現在會傳回 INT_MAX，並在溢位時將 `errno` 設為 ERANGE。 在舊版本中，未定義溢位行為。
- `printf` 函式系列使用格式類型指定名稱 %a 和 %A，以支援根據 ANSI C99 標準所實作的十六進位浮點數輸出。
- `printf` 系列現在支援 "ll" (long long) 大小前置詞。
- 已將 `_controlfp` 函式最佳化，以提高效能。
- 已新增一些函式的偵錯版本。
- 已新增 `_chgsignl` 和 `_cpysignl` (long double 版本)。
- 已將 `_locale_t` 類型新增到類型資料表。
- 已新增巨集 `_countof` 來計算陣列中的元素數。
- 在每個函式主題中，已新增 .NET Framework 對等項目上的區段。
- 數個字串函式現在都有選項可以截斷字串，而不是在輸出緩衝區太小時失敗。請參閱 **_TRUNCATE**。
- `_set_se_translator` 現在需要使用 `/EHa` 編譯器選項。
- `fpos_t` 現在於 `/Za` 下方 (C 程式碼) 以及手動設定 __STDC__ (C++ 程式碼) 時，都是 **__int64**。 過去則是 **struct**。
- _CRT_DISABLE_PERFCRIT_LOCKS 可以改善單一執行緒程式的 I/O 效能。
- POSIX 名稱以淘汰，取代為符合 ISO C++ 的名稱 (例如，使用 `_getch` 而非 `getch`)。
- 新的連結選項 .obj 檔案可用於 pure 模式
- `_recalloc` 結合了 `realloc` 與 `calloc` 的功能。

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Visual Studio 2003 中 C++ 的新功能

### <a name="compiler"></a>編譯器

- 如何在舊版執行階段上執行使用目前編譯器版本所建置之 Managed Extensions for C++ 應用程式的資訊。
- Managed Extensions for C++ 常見問題集。
- 已新增逐步解說，顯示如何移植現有原生應用程式以使用 Managed Extensions for C++：逐步解說：移植現有原生 C++ 應用程式以與 .NET Framework 元件相互操作。
- 您現在可以在實值型別的方法上建立委派。
- 針對 Visual C++ .NET 2003，編譯器與 C++ 標準的相符性已大幅加強。
- 已新增 `/arch` 編譯器選項。
- `/Gf` 即將淘汰，將在下一版的 Visual C++ 移除。
- 已新增 `/G7` 編譯器選項。
- 已加強 `/GS` 編譯器選項，以協助保護區域變數不發生直接緩衝區溢位。
- 已移除 `/noBool` 編譯器選項。 編譯器現在允許 **bool** 在 C++ 原始程式碼檔中只顯示為關鍵字 (而非識別碼)。
- **long long** 類型現在以 **__int64** 的 **typedef** 提供使用。請注意，CRT 尚未支援 **long long**。
- `/Zm` 編譯器選項現在會指定先行編譯標頭記憶體配置上限。
- 現在已記載 _InterlockedCompareExchange 內建函式。
- 現在已記載 _InterlockedDecrement 內建函式。
- 現在已記載 _InterlockedExchange 內建函式。
- 現在已記載 _InterlockedExchangeAdd 內建函式。
- 現在已記載 _InterlockedIncrement 內建函式。
- 已新增 _ReadWriteBarrier 內建函式。

### <a name="attributes"></a>屬性

- 現在已記載 `implements` 屬性。

### <a name="linker-features"></a>連結器功能

已新增下列連結器參數：

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

已新增 .SAFESEH 指示詞和 `/safeseh` ml.exe 選項。

## <a name="see-also"></a>請參閱

[Visual C++ 移植和升級指南](visual-cpp-porting-and-upgrading-guide.md)
