---
title: "Visual C++ 2015 的重大變更 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重大變更 [C++]"
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
caps.latest.revision: 124
caps.handback.revision: 117
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 2015 的重大變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您升級到 Visual C\+\+ 編譯器的新版本時，先前正常編譯及執行的程式碼可能會發生編譯和\/或執行階段錯誤。 新版本中會造成這類問題的變更稱為*「重大變更」*\(Breaking Change\)，在進行 C\+\+ 語言標準、函式簽章或記憶體內部物件配置的修改時通常都會有重大變更。  
  
 為了避免發生難以偵測及診斷的執行階段錯誤，我們建議您絕不要以靜態方式連結至使用不同版本編譯器所編譯的二進位檔。 此外，當您升級 EXE 或 DLL 專案時，請務必也要升級它所連結的程式庫。 如果您是使用 CRT \(C 執行階段\) 或 STL \(標準樣板程式庫\) 類型，則不要在使用不同版本編譯器所編譯的二進位檔 \(包括 DLL\) 之間傳遞它們。 如需詳細資訊，請參閱[跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。  
  
 我們還要建議您不要為不是 COM 介面或 POD 物件的物件撰寫依賴特定配置的程式碼。 如果您撰寫了這種程式碼，則必須確定它在升級之後可以正確運作。 如需詳細資訊，請參閱 [ABI 界限上的可攜性](../cpp/portability-at-abi-boundaries-modern-cpp.md)。  
  
 本文的其餘部分將描述 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中的特定重大變更，在本文中，「新行為」或「現在」等詞彙指的是該版本。 「舊行為」和「之前」等詞彙指的是 Visual Studio 2013 和較早的版本。 如需 Visual Studio 2015 Update 1 之其他變更的相關資訊，請參閱 [Update 1 的重大變更](../misc/breaking-changes-in-visual-cpp-2015-update-1.md)。  
  
1.  [編譯器的重大變更](#BK_compiler)  
  
2.  [C 執行階段 \(CRT\) 程式庫的重大變更](#BK_CRT)  
  
3.  [Standard C\+\+ 和標準樣板程式庫 \(STL\) 的重大變更](#BK_STL)  
  
4.  [MFC 和 ATL 的重大變更](#BK_MFC)  
  
5.  [並行執行階段的重大變更](#BK_ConcRT)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 編譯器  
  
-   \/Zc:forScope\- 選項  
  
     編譯器選項 **\/Zc:forScope\-** 已被取代，在未來的發行版本中將會移除  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     該選項通常是在非標準程式碼的迴圈變數應該已經超出範圍 \(根據該標準\) 之後，用來允許此非標準程式碼。 只有當您使用 \/Za 選項編譯時才需要這樣做，因為在沒有指定 \/Za 的情況下，總是允許在迴圈結束之後使用 for 迴圈變數。 如果您不在意標準一致性 \(例如，如果您並沒有打算將程式碼設計成可移植到其他編譯器\)，則可以關閉 \/Za 選項 \(或將停用語言擴充功能屬性設為 No\)。 如果您在意撰寫可攜式且符合標準的程式碼，就應該要重寫程式碼，將這類變數的宣告移至該迴圈外，使其符合此標準。  
  
    ```  
    // zc_forScope.cpp // compile with: /Zc:forScope- /Za // C2065 expected int main() { // Uncomment the following line to resolve. // int i; for (int i =0; i < 1; i++) ; i = 20;   // i has already gone out of scope under /Za }  
    ```  
  
-   **\/Zg 編譯器選項**  
  
     \/Zg 編譯器選項 \(產生函式原型\) 不再提供使用。 這個編譯器選項之前已遭取代。  
  
-   您再也無法從命令列藉由 mstest.exe 使用 C\+\+ \/CLI 來執行單元測試。 請改用 vstest.console.exe。 請參閱 [VSTest.Console.exe 命令列選項](../Topic/VSTest.Console.exe%20command-line%20options.md)。  
  
-   **可變動的關鍵字**  
  
     在之前 `mutable` 儲存類別規範可以正確無誤編譯的位置中，已再也無法允許此儲存類別規範。 現在，此編譯器會發生錯誤 C2071 \(不合法的儲存類別\)。 根據該標準，可變動的規範只可以套用至類別資料成員的名稱，而不能套用至宣告為常數或靜態的名稱，也不能套用至參考的成員。  
  
     例如，請參考下列程式碼：  
  
    ```  
    struct S { mutable int &r; };  
    ```  
  
     舊版的 Visual C\+\+ 編譯器可接受這種做法，但現在該編譯器會產生下列錯誤：  
  
    ```Output  
    錯誤 C2071: 'S::r': 不合法的儲存類別  
    ```  
  
     若要修正此錯誤，只需移除多餘的可變動關鍵字。  
  
-   **char\_16\_t 和 char32\_t**  
  
     您再也無法使用 `char16_t` 或 `char32_t` 做為 typedef 的別名，因為現在會將這些類型視為內建類型。 對於使用者和程式庫作者來說，將 char16\_t 和 char32\_t 分別定義為 uint16\_t 和 uint32\_t 的別名是很常見的做法。  
  
    ```  
    #include <cstdint> typedef uint16_t char16_t; //C2628 typedef uint32_t char32_t; //C2628 int main(int argc, char* argv[]) { uint16_t x = 1; uint32_t y = 2; char16_t a = x; char32_t b = y; return 0; }  
    ```  
  
     若要更新您的程式碼，請移除此 typedef 宣告，重新命名與這些名稱衝突的任何其他識別項。  
  
-   **非類型樣板參數**  
  
     在您提供明確的樣板引數之際，和非類型樣板參數有關的特定程式碼之類型相容性檢查即為正確。 例如，下列程式碼可在舊版的 Visual C\+\+ 中正確無誤地編譯。  
  
    ```  
    struct S1 { void f(int); void f(int, int); }; struct S2 { template <class C, void (C::*Function)(int) const> void f() {} }; void f() { S2 s2; s2.f<S1, &S1::f>(); }  
  
    ```  
  
     在目前的編譯器中，按照常理則會發生錯誤，因為該樣板參數類型與樣板引數不相符 \(該參數是指向常數成員的指標，但該函式 f 卻是非常數函式\)：  
  
    ```Output  
    錯誤 C2893: 特製化函式樣板 'void S2::f(void)' 失敗附註: 使用下列樣板引數:附註: 'C=S1'附註: 'Function=S1::f'  
    ```  
  
     若要解決程式碼中的這個錯誤，請確定您使用的樣板引數的類型與此樣板參數的宣告類型相符。  
  
-   **\_\_declspec\(align\)**  
  
     該編譯器已不再接受函式上的 `__declspec(align)`。 之前的編譯器一律將它忽略，但現在會產生編譯器錯誤。  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     若要修正這個問題，請從此函式宣告中移除 `__declspec(align)`。 因為它沒有任何作用，移除它並不會變更任何項目。  
  
-   **例外狀況處理**  
  
     有幾個例外狀況處理的變更。 首先，例外狀況物件必須可複製或可移動。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中編譯，但無法在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中編譯：  
  
    ```  
    struct S { public: S(); private: S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     問題是出在於此複製建構函式是私用的，無法如同處理例外狀況的正常過程中發生的物件一樣複製，因此並不能複製該物件。 相同情況也發生在宣告複製建構函式為 `explicit` 的時候。  
  
    ```  
    struct S { S(); explicit S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     若要更新您的程式碼，請確定例外狀況物件的複製建構函式是公用的，而且不是標示為 `explicit`。  
  
     以傳值方式攔截例外狀況也需要可複製的例外狀況物件。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中編譯，但無法在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中編譯：  
  
    ```  
    struct B { public: B(); private: B(const B &); }; struct D : public B { }; int main() { try { } catch (D d) // error { } }  
  
    ```  
  
     您可以藉由變更 `catch` 的參數類型為參考來修正此問題。  
  
    ```  
    catch(D& d) { }  
    ```  
  
-   **後面接著巨集的字串常值**  
  
     該編譯器現在支援使用者定義常值。 因此，會將後面接著巨集且不含任何中間空白字元的字串常值解譯為使用者定義常值，這可能會產生錯誤或非預期的結果。 例如，在舊版編譯器中，下列程式碼可順利編譯：  
  
    ```  
    #define _x "there" char* func() { return "hello"_x; } int main() { char * p = func(); return 0; }  
    ```  
  
     該編譯器會將其解譯為後面接著巨集的字串常值 "hello"，並且將該巨集展開成 "there"，然後再將這兩個字串常值串連成一個。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，編譯器會將它解譯為使用者定義的常值，但是因為沒有定義相符的使用者定義常值 \_x，所以會產生錯誤。  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     若要修正這個問題，請在此字串常值和巨集之間加入空格。  
  
-   **相鄰字串常值**  
  
     如同前面所述，因為字串剖析時相關變更的緣故，在舊版的 Visaul C\+\+ 版本中，會將不含任何空白字元的相鄰字串常值 \(寬字元或窄字元字串常值\) 解譯為單一的串連字串。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，您必須在兩個字串之間加入空白字元。 例如，下列程式碼必須有所變更：  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     只要在兩個字串之間加入空格即可。  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **Placement new 和 delete**  
  
     為了讓 delete 運算子 \(delete Operator\) 與 C\+\+ 14 標準一致，已對它加以變更。 如需此標準之變更的詳細資訊，請參閱 [C\+\+ 調整大小的解除配置](http://isocpp.org/files/papers/n3778.html)。 此變更加入一種全域 delete 運算子，該運算子需要大小參數。 重大變更是如果您先前使用具有相同簽章 \(藉此對應至 placement new 運算子\) 的 operator delete 函式，就會發生編譯器錯誤 \(C2956，於使用 placement new 運算子所在之處發生，因為在程式碼的該位置上，此編譯器會嘗試識別合適且相符的 delete 運算子\)。  
  
     函式 `void operator delete(void *, size_t)` 曾是 placement delete 運算子，相當於 C\+\+ 11 中的 placement new 函式 "void \* operator new\(size\_t, size\_t\)"。 搭配 C\+\+14 調整大小的解除配置，這個 delete 函式現在為*「一般解除配置函式」*\(Usual Deallocation Function\) \(全域 delete 運算子\)。 此標準的要求為如果 placement new 的使用會查詢對應的 delete 函式，並找到一般解除配置函式，則此程式語式錯誤。  
  
     例如，假設您的程式碼同時定義 placement new 和 placement delete：  
  
    ```  
    void * operator new(std::size_t, std::size_t); void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     您已定義的 placement delete 運算子和新的全域調整大小 delete 運算子之間的函式簽章比對會導致此問題發生。 針對 placement new 和 delete 運算子，請考慮是否可以使用 size\_t 以外的不同類型。  請注意 size\_t typedef 的類型是編譯器相依的；它是 Visual C\+\+ 中不帶正負號的 int 之 typedef。 較佳的解決方案是使用這類列舉類型：  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     然後，變更 placement new 和 delete 的定義，藉此使用此類型取代 size\_t 做為第二個引數。 您也需要更新對 placement new 的呼叫，藉此傳遞新的類型 \(例如，使用 `static_cast<my_type>` 從整數值加以轉換\)，並且更新 new 和 delete 的定義，用來轉換回整數類型。 您不需要為此使用列舉；具有 size\_t 成員的類別類型也可以運作。  
  
     替代方案是您或許可以完全排除 placement new。 如果您的程式碼使用 placement new 實作記憶體集區，其中 placement 引數是此物件所配置或已刪除的大小，則調整大小解除配置功能或許會很適合取代您自己自訂的記憶體集區程式碼，而且您可以不使用 placement 函式，只使用您自己的雙引數 delete 運算子，用來取代此 placement 函式。  
  
     如果您不想立即更新您的程式碼，則可以使用編譯器選項 \/Zc:sizedDealloc\- 來還原舊版的行為。 如果您使用這個選項，則此雙引數 delete 函式將不存在，也不會與您的 placement delete 運算子發生衝突。  
  
-   **等位資料成員**  
  
     等位資料成員不再具有參考類型。 下列程式碼可在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 順利編譯，但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 會產生錯誤。  
  
    ```  
    union U1 { const int i; }; union U2 { int &i; }; union U3 { struct {int &i;}; };  
    ```  
  
     前一個程式碼會產生下列錯誤：  
  
    ```Output  
    test.cpp(67): 錯誤 C2625: 'U2::i': 不合法的等位成員; 類型 'int &' 是參考類型 test.cpp(70): 錯誤 C2625: 'U3::i': 不合法的等位成員; 類型 'int &' 是參考類型  
    ```  
  
     若要解決這個問題，請將參考類型變更為指標或值。 將此類型變更為指標需要變更使用此等位欄位的程式碼。 將此程式碼變更為值也可能會變更此等位中儲存的資料，這會影響其他欄位，因為在等位類型中的欄位會共用相同的記憶體。 根據值的大小而定，它也可能會變更等位的大小。  
  
-   現在匿名等位與標準更一致。 舊版的編譯器會產生匿名等位的明確建構函式和解構函式。 這些在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中已刪除。  
  
    ```  
    struct S { S(); }; union { struct { S s; }; } u; // C2280  
    ```  
  
     前一個程式碼會在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 產生下列錯誤：  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     若要解決這個問題，請提供您自己的建構函式和 \(或\) 解構函式之定義。  
  
    ```  
    struct S { // Provide a default constructor by adding an empty function body. S() {} }; union { struct { S s; }; } u;  
    ```  
  
-   **具有匿名結構的等位**  
  
     為了符合標準，此執行階段行為為了等位中匿名結構的成員而有所變更。 建立這類等位時，不再隱含呼叫等位中匿名結構成員的建構函式。 此外，當此等位超出範圍時，將不再隱含呼叫等位中的匿名結構成員的解構函式。 請考慮下列程式碼，其中等位 U 包含匿名結構，該結構包含成員，此成員為具有解構函式的具名結構 S。  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S\n"); } ~S(){ printf("Destroying S\n"); } }; union U { struct { S s; }; U() {} ~U(){} }; void f() { U u; // Destructor implicitly called here. } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，會在建立此等位時呼叫 S 建構函式，而且當函式 f 的堆疊已清除時，會呼叫 S 的解構函式。 但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，不會呼叫此建構函式和解構函式。 該編譯器會提供有關這項行為變更的警告。  
  
    ```Output  
    警告 C4587: 'U::s': 行為變更: 不再隱含呼叫建構函式警告 C4588: 'U::s': 行為變更: 不再隱含呼叫解構函式  
    ```  
  
     若要還原原始行為，請對此匿名結構命名。 不論編譯器版本為何，非匿名結構的執行階段行為是相同的。  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S.\n"); } ~S() { printf("Destroying S\n"); } }; union U { struct { S s; } namedStruct; U() {} ~U() {} }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     或者，請嘗試將建構函式和解構函式的程式碼移到新的函式，並加入這些來自此等位之建構函式和解構函式的函式呼叫。  
  
    ```  
    #include <stdio.h> struct S { void Create() { printf("Creating S.\n"); } void Destroy() { printf("Destroying S\n"); } }; union U { struct { S s; }; U() { s.Create();  } ~U() { s.Destroy(); } }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
-   **樣板解析**  
  
     已變更樣板的名稱解析。 在 C\+\+ 中，在考慮名稱解析的候選時，也可能產生這種情況：一或多個考慮為可能符合的名稱產生無效的樣板具現化。 這些無效的具現化通常不會造成編譯器錯誤，也就是稱為 SFINAE \(替代失敗是不是錯誤\) 的原則。  
  
     現在，如果 SFINAE 需要此編譯器具現化類別樣板的特製化，則在這個程序期間發生的任何錯誤都會是編譯器錯誤。 在舊版中，此編譯器會忽略這類錯誤。 例如，請參考下列程式碼：  
  
    ```  
    #include <type_traits> template<typename T> struct S { S() = default; S(const S&); S(S&&); template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type> S(S<U>&&); }; struct D; void f1() { S<D> s1; S<D> s2(s1); } struct B { }; struct D : public B { }; void f2() { S<D> s1; S<D> s2(s1); }  
  
    ```  
  
     如果您使用目前的編譯器編譯時，會產生下列錯誤：  
  
    ```Output  
    type_traits(1110): 錯誤 C2139: 'D': 未定義的類別不允許做為編譯器內建的類型特性 '__is_base_of' 的引數..\t331.cpp(14): 附註: 請參閱 'D' 的宣告 ..\t331.cpp(10): 附註: 請參閱類別樣板具現化參考 'std::is_base_of<T,U>'，其正在進行編譯 [ T=D, U=D ]  
    ```  
  
     這是因為在進行 is\_base\_of 之第一個引動過程的時候，尚未定義類別 'D'。  
  
     在這種情況下，除非已宣告此類別，否則使用這類類型特性並不能修正問題。 如果您將 B 和 D 的定義移至此程式碼檔案開頭，則可解決此錯誤。 如果此定義位於標頭檔中，請檢查標頭檔之 include 陳述式的順序，藉此確定在使用有問題的樣板之前，會先編譯任何類別的定義。  
  
-   **複製建構函式**  
  
     在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 和 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中，如果該類別具有使用者定義的移動建構函式，但沒有使用者定義的複製建構函式，則此編譯器會產生類別的複製建構函式。 在 Dev14 中，也會將這個隱含產生的複製建構函式標示為"\= delete"。  
  
##  <a name="BK_CRT"></a> C 執行階段程式庫 \(CRT\)  
  
### 一般變更  
  
-   **重構的二進位檔**  
  
     CRT 程式庫已重構成兩個不同的二進位檔：通用 CRT \(ucrtbase\)，其中包含大部分的標準功能，以及 VC 執行階段程式庫 \(vcruntime140\)，其中包含編譯器相關的功能，例如例外狀況處理和內建。 如果您正使用預設的專案設定，則這項變更不會對您造成影響，因為此連結器會自動使用新的預設程式庫。 如果您已將此專案的**連結器**屬性**忽略所有預設程式庫**設定為**是**，或您在命令列使用 \/NODEFAULTLIB 連結器選項，則必須更新程式庫清單 \(在**其他相依性**屬性中\)，藉此包含新的、重構的程式庫。 請將舊的 CRT 程式庫 \(libcmt.lib、libcmtd.lib、msvcrt.lib、msvcrtd.lib\) 取代為對等的重構程式庫。 這兩個重構程式庫中的任何一個皆有靜態 \(.lib\) 和動態 \(.dll\) 版本，也都有發行 \(沒有後置詞\) 和偵錯版本 \(具有 "d" 後置詞\)。 此動態版本具有您可與其連結的匯入程式庫。 這兩個重構程式庫為：通用的 CRT，特別是 ucrtbase.dll 或 .lib、ucrtbased.dll 或 .lib，以及 VC 執行階段程式庫，即 libvcruntime.lib、libvcruntime.dll、libvcruntimed.lib 和 libvcruntimed.dll。 請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
### \<locale.h\>  
  
-   **localeconv**  
  
     在已啟用[個別執行緒的地區設定](../parallel/multithreading-and-locales.md)時，locale.h 中宣告的 [localeconv](../c-runtime-library/reference/localeconv.md) 函式即可正確運作。 在此程式庫的舊版中，這個函式會傳回全域地區設定的 lconv 資料，而非此執行緒的地區設定。  
  
     如果您使用個別執行緒的地區設定，您應該要檢查 localeconv 的使用情況，查看您的程式碼是否假設傳回的 lconv 資料為全域地區設定，並加以適當修改。  
  
### \<math.h\>  
  
-   **C\+\+ 數學程式庫函式的多載**  
  
     在舊版中，\<math.h\> 定義一些 \(但不是所有\) 數學程式庫函式的 C\+\+ 多載。 \<cmath\> 定義了其餘的多載，所以為了完整取得這些多載，必需將 \<cmath\> 標頭包含在內。 在只包含了 \<math.h\> 的程式碼中，函式多載解析會造成問題。 現在，所有的 C\+\+ 多載都已經從 \<math.h\> 中移除了，現在都只位於 \<cmath\>。  
  
     若要解決錯誤，請包含 \<cmath\>，藉此取得 \<math.h\> 中已移除的函式宣告。 下表列出已移動的函式。  
  
     已移動的函式：  
  
    1.  double abs\(double\) 和 float abs\(float\)  
  
    2.  double pow\(double, int\)、float pow\(float, float\)、float pow\(float, int\)、long double pow\(long double, long double\)、long double pow\(long double, int\)  
  
    3.  下列浮點函式的浮點數和 long double 版本：acos、acosh、asin、asinh、atan、atanh、atan2、cbrt、ceil、copysign、cos、cosh、erf、erfc、exp、exp2、expm1、fabs、fdim、floor、fma、fmax、fmin、fmod、frexp、hypot、ilogb、ldexp、lgamma、llrint、llround、log、log10、log1p、log2、lrint、lround、modf、nearbyint、nextafter、nexttoward、remainder、remquo、rint、round、scalbln、scalbn、sin、sinh、sqrt、tan、tanh、tgamma、trunc  
  
     如果您有使用 abs 搭配浮點類型撰寫的程式碼，且該程式碼只包含 math.h 標頭，則此浮點版本將不再可用，因此即使使用浮點引數，現在仍會將該呼叫解析成 abs\(int\)。 這會產生此錯誤：  
  
    ```Output  
    警告 C4244: 'argument'：從 'float' 轉換成 'int'，資料可能遺失  
    ```  
  
     這個警告的修正方法是將對 abs 的呼叫取代為浮點版本的 abs，例如雙精度浮點引數的 fabs 或浮點引數的 fabsf，或包含 cmath 標頭，即可繼續使用 abs。  
  
-   **浮點的一致性**  
  
     針對特殊案例的輸入，例如 NaN 和無限大，為了與 IEEE\-754 和 C11 附錄 F 規格更加一致，此數學程式庫已有許多變更。 例如，在舊版的程式庫中通常將無訊息的 NaN 輸入視為錯誤，如今已不再視為錯誤。 請參閱 [IEEE 754 標準](http://grouper.ieee.org/groups/754)和 [C11 標準](http://www.iso-9899.info/wiki/The_Standard)的附錄 F。  
  
     這些變更不會造成編譯時期錯誤，但根據此標準，可能會導致程式的行為不同且更加正確。  
  
-   **FLT\_ROUNDS**  
  
     這是在 Visual Studio 2013 中，展開為常數運算式的 FLT\_ROUNDS 巨集，因為此捨入模式為可在執行階段設定的，例如可由呼叫 fesetround 設定，所以這是不正確的。 FLT\_ROUNDS 巨集現在是動態的，而且會正確反映目前的捨入模式。  
  
### \<new\> 和 \<new.h\>  
  
-   **new 和 delete**  
  
     在此程式庫的舊版中，實作定義的 operator new 和 delete 函式會從此執行階段程式庫 DLL \(例如，msvcr120.dll\) 中匯出。 這些 operator 函式現在一律以靜態方式連結到您的二進位檔，即使是使用執行階段程式庫 DLL 亦同。  
  
     對於原生或混合程式碼 \(\/clr\) 而言，這不是重大變更，但是對於編譯成 [\/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) 的程式碼，這可能會造成您的程式碼無法編譯。 如果您將程式碼編譯成 \/clr:pure，可能會需要加入 \#include \<new\> 或 \#include \<new.h\>，以解決因為這項變更而引起的建置錯誤。 請注意在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中已取代 \/clr:pure，而且可能會在未來的版本中移除。  
  
### \<process.h\>  
  
-   **\_beginthread 和 \_beginthreadex**  
  
     [\_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 函式現在會保留模組的參考，在該模組中，執行緒程序是為了該執行緒持續期間所定義的。 這有助於確保在執行緒執行到完成之前，不會卸載模組。  
  
### \<stdarg.h\>  
  
-   **va\_start 和參考類型**  
  
     編譯 C\+\+ 程式碼時，現在 [va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 會在編譯時期驗證傳遞給它的引數不是參考類型。 此 C\+\+ 標準禁止參考類型引數。  
  
### \<stdio.h\> 和 \<conio.h\>  
  
-   **printf 和 scanf 系列的函式現在已定義為內嵌。**  
  
     所有 printf 和 scanf 函式的定義都已內嵌移動到 \<stdio.h\>、\<conio.h\> 和其他 CRT 標頭中。 對於區域宣告這些函式，但不包含適當的 CRT 標頭之任何程式而言，這是會導致連結器錯誤 \(LNK2019，無法解析的外部符號\) 的重大變更。 可能的話，您應該更新程式碼，包含此 CRT 標頭 \(亦即，加入 \#include \<stdio.h\>\) 和此內嵌函式，但如果您不要修改程式碼以包含這些標頭檔，替代方案是將額外的程式庫加入您的連結器輸入 legacy\_stdio\_definitions.lib 中。  
  
     若要將您在此 IDE 中的連結器輸入加入這個程式庫，請開啟專案節點的操作功能表，選擇 \[屬性\]，接著在 \[專案屬性\] 對話方塊中選擇 \[連結器\]，並編輯 \[連結器輸入\]，將 legacy\_stdio\_definitions.lib 加入此分號分隔的清單。  
  
     如果您的專案以靜態程式庫連結，且此程式庫使用早於 2015的 Visual C\+\+ 版本編譯，則此連結器可能會報告無法解析的外部符號。 這些錯誤可能會參考 \_iob、\_iob\_func 之內部 stdio 的定義，或 \_imp\_\* 形式之特定 stdio 函式的相關匯入。 Microsoft 建議當您升級專案時，應以最新版本的 Visual C\+\+ 編譯器和程式庫重新編譯所有的靜態程式庫。 如果該程式庫是協力廠商程式庫，其來源無法取得，您應該向協力廠商要求更新的二進位檔，或將該程式庫的使用方式封裝成不同的 DLL，其中您使用舊版的 Visual C\+\+ 編譯器和程式庫編譯該 DLL。  
  
    > [!WARNING]
    >  如果您要以 Windows SDK 8.1 或更早版本連結，您可能會遇到這些無法解析的外部符號錯誤。 在該情況下，您應該如先前所述地將 legacy\_stdio\_definitions.lib 加入連結器輸入來解決此錯誤。  
  
     若要疑難排解無法解析的符號錯誤，您可以嘗試使用 [dumpbin.exe](../build/reference/dumpbin-reference.md) 來檢查二進位檔案中定義的符號。 請嘗試下列的命令列，檢視程式庫中定義的符號。  
  
    ```  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-   **gets 和 \_getws**  
  
     [gets](../c-runtime-library/gets-getws.md) 和 [\_getws](../c-runtime-library/gets-getws.md) 函式已遭移除。 gets 函式已從 C11 中的 C 標準程式庫移除，因為無法安全地使用該函式。 \_getws 函式曾是 Microsoft 擴充功能，相當於 gets，但卻是用於寬字串。 做為這些函式的替代項目，請考慮使用 [fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[gets\_s](../c-runtime-library/reference/gets-s-getws-s.md) 和 [\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
-   **\_cgets 和 \_cgetws**  
  
     [\_cgets](../c-runtime-library/cgets-cgetws.md) 和 [\_cgetws](../c-runtime-library/cgets-cgetws.md) 函式已遭移除。 做為這些函式的替代項目，請考慮使用 [\_cgets\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) 和 [\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。  
  
-   **無限大與 NaN 格式**  
  
     在舊版本中，會使用一組 Visual C\+\+ 特定的 Sentinel 字串，將無限大和 NaN 格式化。  
  
    -   無限大：1.\#INF  
  
    -   無訊息的 NaN：1.\#QNAN  
  
    -   訊號 NaN：1.\#SNAN  
  
    -   不確定的 NaN：1.\#IND  
  
     其中任何一項都可能有正負號的前置詞，也可能根據欄位寬度和精確度而有稍微不同的格式 \(有時會有不尋常的效果，例如：printf\("%.2f\\n", INFINITY\) 可能會列印 1.\#J，因為有可能會將 \#INF「四捨五入」為 2 位數的精確度\)。 C99 導入了無限大和 NaN 格式化方式之新的需求。 現在的 Visual C\+\+ 實作符合這些需求。 新的字串如下：  
  
    -   無限大：inf  
  
    -   無訊息的 NaN：nan  
  
    -   訊號 NaN：nan\(snan\)  
  
    -   不確定的 NaN：nan\(ind\)  
  
     其中任何一項都可以有正負號的前置詞。 如果使用了大寫格式規範 \(%F，而非 %f\)，則此字串會視需要以大寫字母 \(INF，而非 inf\) 列印。  
  
     [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函式已經經過修改，藉此剖析這些新的字串，所以這些字串會藉由 printf 和 scanf 反覆存取。  
  
-   **浮點數格式化和剖析**  
  
     已引進新的浮點數格式化和剖析演算法來改善正確性。 這項變更會影響 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 和 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 系列的函式，以及像是 [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 的函式。  
  
     舊格式的演算法會產生有限位數的數字，然後以零填滿剩餘的小數位數。 若要產生會對原始浮點數值反覆存取的字串，這通常已經夠合用了，但如果您想要精確值 \(或其中最接近的十進位表示\)，就會不夠合適。 新的格式演算法會視需要產生足夠多的位數，用來代表該值 \(或用來填入指定的精確度\)。 做為改進的範例，請考慮列印 2 的大型乘冪時之結果：  
  
    ```  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        舊版：1208925819614629200000000    新版：1208925819614629200000000  
    ```  
  
     舊的剖析演算法只會考慮輸入字串中最多 17 個有效位數，並會捨棄其餘位數。 這足以產生字串所代表值的非常接近之近似值，而且通常會產生非常接近捨入正確的結果。 新的實作會考慮所有出現的位數，而且會針對所有輸入 \(長度最多 768 位數\) 產生正確捨入的結果。 此外，這些函式現在會遵循捨入模式 \(可透過 fesetround 控制\)。  這可能是行為重大變更，因為這些函式可能會輸出不同的結果。 新的結果永遠比舊的結果正確。  
  
-   **十六進位和無限大\/NaN 浮點數剖析**  
  
     如同上面所述，浮點數剖析演算法現在會剖析十六進位的浮點數字串 \(例如那些由 %a 和 %A printf 格式規範所產生的\)，和剖析所有由此 printf 函式產生的無限大和 NaN 字串。  
  
-   **%A 和 %a 零填補**  
  
     %a 和 %A 格式規範會將浮點數格式化為十六進位的尾數和二進位的指數。 在舊版，printf 函式無法正確對字串進行零填補。 例如，printf\("%07.0a\\n", 1.0\) 會列印 00x1p\+0，但這應該是 0x01p\+0 才對。 這項問題已獲得修正。  
  
-   **%A 和 %a 的精確度**  
  
     在此程式庫的舊版中，%A 和 %a 的格式規範之預設精確度是 6。 為了與 C 標準一致，現在此預設精確度為 13。  
  
     在搭配 %A 或 %a 使用格式字串的任何函式輸出中，此為執行階段行為變更。 在舊版的行為中，使用 %A 規範的輸出可能為 "1.1A2B3Cp\+111"。 現在對於相同值的輸出是 "1.1A2B3C4D5E6F7p\+111"。 若要取得舊的行為，您可以指定精確度，例如 %.6A。 請參閱[精確度規格](../c-runtime-library/precision-specification.md)。  
  
-   **%F 規範**  
  
     現在支援 %F 格式\/轉換規範。 它的功能相當於 %f 格式規範，不同之處在於無限大和 NaN 的格式使用大寫字母。  
  
     在舊版中，此實作用來剖析 F 和 N 為長度修飾詞。 這種行為可追溯至分段位址空間的年代：這些長度修飾詞曾分別用來表示遠指標和近指標，如同 %Fp 或 %Ns。 已移除這種行為。 如果遇到 %F，現在會將它視為 %F 格式規範；如果遇到 %N 時，現在會將它視為無效的參數。  
  
-   **指數格式**  
  
     %e 和 %E 格式規範會將浮點數格式化為十進位的尾數和指數。 在某些情況下，%g 和 %G 格式規範也會將數字格式化為這種形式。 在舊版中，CRT 永遠會產生具有三位數指數的字串。 例如，printf\("%e\\n", 1.0\) 會列印 1.000000e\+000。 這是不正確的：如果可使用一位數或兩位數表示該指數，則 C 要求只能列印兩位數。  
  
     在 Visual Studio 2005 中已加入全域一致性切換：[\_set\_output\_format](../c-runtime-library/set-output-format.md)。 程式可以用引數 \_TWO\_DIGIT\_EXPONENT 呼叫這個函式，以啟用符合標準的指數列印。 這項預設行為已變更為符合標準的指數列印模式。  
  
-   **格式字串驗證**  
  
     在舊版中，printf 和 scanf 函式會以無訊息模式接受許多無效的格式字串，有時會產生不尋常的作用。 例如，會將 %hlhlhld 視為 %d。 現在會將所有無效的格式字串視為無效的參數。  
  
-   **fopen 模式字串驗證**  
  
     在舊版中，fopen 系列的函式會以無訊息模式接受某些無效的模式字串 \(例如：r\+b\+\)。 現在會偵測到無效的模式字串並將其視為無效的參數。  
  
-   **\_O\_U8TEXT 模式**  
  
     現在 [\_setmode](../c-runtime-library/reference/setmode.md) 函式會正確報告在 in\_O\_U8TEXT 模式中開啟的資料流之模式。 在此程式庫的舊版中，它會報告這類資料流為在 \_O\_WTEXT 中所開啟。  
  
     如果您的程式碼解譯 \_O\_WTEXT 模式，其中資料流的編碼是 UTF\-8，這就會是一項重大變更。 如果您的應用程式不支援 UTF\_8，請考慮將這項日漸普遍之編碼方式的支援加入。  
  
-   **snprintf 和 vsnprintf**  
  
     現在已實作 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 和 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)。 舊版程式碼通常提供這些函式的巨集版本之定義，因為 CRT 程式庫並沒有將它們實作，但是在較新版本中已不再需要。 如果在包含 \<stdio.h\> 前先將 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 或 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 定義為巨集，則現在編譯會失敗並傳回錯誤，該錯誤會表示定義巨集的位置。  
  
     一般來說，修正這個問題的方式為刪除使用者程式碼中 snprintf 或 vsnprintf 的任何宣告。  
  
-   **tmpnam 產生可使用的檔案名稱**  
  
     在舊版中，tmpnam 和 tmpnam\_s 函式會在磁碟機的根目錄中 \(例如 \\sd3c.\) 產生檔案名稱。 現在這些函式會在暫存目錄中產生可用的檔案名稱路徑。  
  
-   **FILE 封裝**  
  
     在舊版中，於 \<stdio.h\> 已完全定義 FILE 類型，所以使用者程式碼有可能進入 FILE 和修改其內部項目。 已將 stdio 程式庫變更為隱藏實作詳細資料。 做為這項變更的一部分，現在 \<stdio.h\> 中所定義的 FILE 是不透明的類型，其成員無法從此 CRT 本身的外部存取。  
  
-   **\_outp 和 \_inp**  
  
     已經移除函式 [\_outp](../c-runtime-library/outp-outpw-outpd.md)、[\_outpw](../c-runtime-library/outp-outpw-outpd.md)、[\_outpd](../c-runtime-library/outp-outpw-outpd.md)、[\_inp](../c-runtime-library/inp-inpw-inpd.md)、[\_inpw](../c-runtime-library/inp-inpw-inpd.md) 和 [\_inpd](../c-runtime-library/inp-inpw-inpd.md)。  
  
### \<stdlib.h\>、\<malloc.h\> 和 \<sys\/stat.h\>  
  
-   **strtof 和 wcstof**  
  
     當 strtof 和 wcstof 函式的值無法表示為浮點數時，會無法將 errno 設為 ERANGE。 這項問題已獲得修正。 \(請注意，這個錯誤是這兩個函數特有的；而 strtod、wcstod、strtold 和 wcstold 函式不受影響。\) 這是執行階段的重大變更。  
  
-   **對齊的配置函式**  
  
     在舊版中，對齊的配置函式 \(\_aligned\_malloc、\_aligned\_offset\_malloc 等\) 會以無訊息方式接受對齊為 0 的區塊之要求。 要求的對齊必須是 2 的乘冪，而 0 卻不是。 已修正這個問題，現在會將要求的對齊為 0 視為無效的參數。 這是執行階段的重大變更。  
  
-   **堆積函式**  
  
     已移除 \_heapadd、\_heapset 和 \_heapused 函式。 這些函式已無作用，因為 CRT 已更新為使用 Windows 堆積。  
  
-   **小型堆積**  
  
     已移除 smalheap 連結選項。 請參閱[連結選項](../c-runtime-library/link-options.md)。  
  
### \<string.h\>  
  
-   **wcstok**  
  
     已變更 wcstok 函式的簽章為符合 C 標準所需的簽章。 在此程式庫的舊版中，這個函式的簽章是：  
  
    ```  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     它使用內部個別執行緒內容來追蹤呼叫之間的狀態，如同 strtok 所執行的。 此函式現在有簽章 wchar\_t\* wcstok\(wchar\_t\*, wchar\_t const\*, wchar\_t\*\*\)，並要求呼叫端將內容做為第三個引數傳遞至該函式。  
  
     已將舊的簽章加入新的 \_wcstok 函式，藉此簡化移植。 在編譯 C\+\+ 程式碼時，還有一個具有舊簽章的 wcstok 內嵌多載。 會將這個多載宣告為已被取代。 在 C 程式碼中，您可能會定義 \_CRT\_NON\_CONFORMING\_WCSTOK，讓 \_wcstok 用來取代 wcstok。  
  
### \<time.h\>  
  
-   **時鐘**  
  
     在舊版中，會使用 Windows 應用程式開發介面 [GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx) 實作 [clock](../c-runtime-library/reference/clock.md) 函式。 連同這項實作，clock 函式會受系統時間影響，因此並不一定是單調函式。 已根據 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 重新實作 clock 函式，因此該函式現在是單調函式。  
  
-   **fstat 和 \_utime**  
  
     在舊版中，[\_stat](../c-runtime-library/reference/stat-functions.md)、[fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 和 [\_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 函式未正確處理日光節約時間。 在 Visual Studio 2013 之前，這些函式全都未正確調整標準時間的時間，如同它們是在日光節約時間一樣。  
  
     在 Visual Studio 2013 中，已在 \_stat 系列的函式中修正此問題，但是在 fstat 和 \_utime 系列的函式中，類似的問題未獲修正。 這導致因為函式之間不一致所產生的問題。 現在已修正 fstat 和 \_utime 系列的函式，因此這些函式現在全都能正確且一致地處理日光節約時間。  
  
-   **asctime**  
  
     在舊版中，[asctime](../c-runtime-library/reference/asctime-wasctime.md) 函式會在一位數的天數前面填補零，例如：Fri Jun 06 08:00:00 2014。 此規格需要這類天數以空格填補，例如：Fri Jun  6 08:00:00 2014。 這項問題已獲得修正。  
  
-   **strftime 和 wcsftime**  
  
     現在 strftime 和 wcsftime 函式支援 %C、%D、%e、%F、%g、%G、%h、%n、%r、%R、%t、%T、%u 和 %V 格式規範。 此外，會剖析 E 和 O 修飾詞 \(但也會將其忽略\)。  
  
     會指定 %c 格式規範為對於目前地區設定產生「適當的日期和時間表示法」。 在 C 的地區設定中，這個表示法必須與 %a %b %e %T %Y 相同。 這和由 asctime 所產生的格式相同。 在舊版中，%c 格式規範未正確使用 MM\/DD\/YY HH:MM:SS 表示法將時間格式化。 這項問題已獲得修正。  
  
-   **timespec 和 TIME\_UTC**  
  
     現在 \<time.h\> 標頭定義 timespec 類型和 C11 標準的 timespec\_get 函式。 此外，現在定義了 TIME\_UTC 巨集，以搭配 timespec\_get 函式使用。 這對於其中任何一項有衝突定義的程式碼而言是重大變更。  
  
-   **CLOCKS\_PER\_SEC**  
  
     現在 CLOCKS\_PER\_SEC 巨集會展開成整數的類型 clock\_t，如同 C 語言所要求的。  
  
###  <a name="BK_STL"></a> 標準樣板程式庫  
 為了啟用新的最佳化和偵錯檢查，Visual Studio 所實作的 C\+\+ 標準程式庫是刻意中斷各個版本之間的二進位碼相容性 \(Binary Compatibility\)。 因此，使用 C\+\+ 標準程式庫時，使用不同版本所編譯的目的檔和靜態程式庫不可以混合在一個二進位檔 \(EXE 或 DLL\) 中，也不可以在使用不同版本所編譯的二進位檔之間傳遞 C\+\+ 標準程式庫物件。 這類混合會發出有關 \_MSC\_VER 不符的連結器錯誤  \(\_MSC\_VER 是包含此編譯器主要版本的巨集，例如對於 Visual Studio 2013 為 1800。\) 這項檢查無法偵測 DLL 混合，且無法偵測包含 Visual C\+\+ 2008 及較舊版本的混合。  
  
-   **STL include 檔**  
  
     STL 標頭中的 include 結構已有一些變更。 STL 標頭可以用未指定的方式彼此包含。 一般而言，在您所撰寫的程式碼中，應該要使其周密地包含所有根據 C\+\+ 標準所需的標頭，而不要依賴於包含其他 STL 標頭的 STL 標頭。 這使其成為可攜式跨版本和跨平台的程式碼。 在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中，至少有兩種標頭的變更會影響使用者程式碼。 首先，\<string\> 不再包含 \<iterator\>。 第二，\<tuple\> 現在會宣告 std::array，但不包含所有的 \<array\>，這可藉由下列程式碼建構的組合來中斷程式碼：您的程式碼具有名為 "array" 的變數，並且具有 using 指示詞 "using namespace std;"，而且將包含 \<tuple\> \(現在會宣告 std::array\) 的 STL 標頭 \(例如 \<functional\>\) 予以包含。  
  
-   **steady\_clock**  
  
     [steady\_clock](../standard-library/steady-clock-struct.md) 的 \<chrono\> 實作已變更為符合穩定性和單一性的 C\+\+ 標準需求。 現在 steady\_clock 以 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 為基礎，而 high\_resolution\_clock 現在是 steady\_clock 的 typedef。 如此一來，在 Visual C\+\+ 中， steady\_clock::time\_point 現在是 chrono::time\_point\<steady\_clock\> 的 typedef；不過，這不一定也會發生在其他實作中。  
  
-   **配置器和常數**  
  
     我們現在要求配置器的等號\/不等比較要在兩邊接受常數引數。  如果您的配置器定義這些運算子，如下所示：  
  
    ```  
    bool operator==(const MyAlloc& other)  
    ```  
  
     您應該將其更新，藉此將它們宣告為常數成員。  
  
    ```  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **常數項目**  
  
     C\+\+ 標準曾一律禁止常數項目 \(例如 vector\<const T\> 或 set\<const T\>\) 的容器。 Visual C\+\+ 2013 及更早版本接受這類容器。 在目前版本中，這類容器無法編譯。  
  
-   **std::allocator::deallocate**  
  
     在 Visual C\+\+ 2013 和舊版中，std::allocator::deallocate\(p, n\) 忽略針對 n 而傳遞進來的引數。  C\+\+ 標準永遠要求 n 與做為第一個引數傳遞的值相等，該值傳遞至配置的引動過程，其中此配置會傳回 p。 不過，在目前版本中，會檢查 n 的值。 對於所傳遞之 n 的引數和此標準要求不同的程式碼，這有可能會在執行階段當機。  
  
-   **hash\_map 和 hash\_set**  
  
     非標準標頭檔 hash\_map 和 hash\_set 在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中已遭取代，將在未來的版本中移除。 請改用 unordered\_map 和 unordered\_set。  
  
-   **比較子和 operator\(\)**  
  
     現在關聯容器 \(\<map\> 系列\) 要求其比較子具有可呼叫常數的函式呼叫運算子。 現在比較子類別宣告中的下列程式碼無法編譯：  
  
    ```  
    bool operator()(const X& a, const X& b)  
    ```  
  
     若要解決這個錯誤，請將此函式宣告變更為：  
  
    ```  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **類型特性**  
  
     已移除來自較早版本 C\+\+ 標準草案之類型特性的舊名稱。 這些在 C\+\+11 中已有所變更，且已在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中更新為 C\+\+11 的值。 下表顯示舊名稱和新名稱。  
  
    |舊名稱|新名稱|  
    |---------|---------|  
    |add\_reference|add\_lvalue\_reference|  
    |has\_default\_constructor|is\_default\_constructible|  
    |has\_copy\_constructor|is\_copy\_constructible|  
    |has\_move\_constructor|is\_move\_constructible|  
    |has\_nothrow\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_default\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_copy|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_copy\_constructor|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_move\_constructor|is\_nothrow\_move\_constructible|  
    |has\_nothrow\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_copy\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_move\_assign|is\_nothrow\_move\_assignable|  
    |has\_trivial\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_default\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_copy|is\_trivially\_copy\_constructible|  
    |has\_trivial\_move\_constructor|is\_trivially\_move\_constructible|  
    |has\_trivial\_assign|is\_trivially\_copy\_assignable|  
    |has\_trivial\_move\_assign|is\_trivially\_move\_assignable|  
    |has\_trivial\_destructor|is\_trivially\_destructible|  
  
-   **launch::any 和 launch::sync 原則**  
  
     已移除非標準的 launch::any 和 launch::sync 原則。 對於 launch::any，請改用 launch:async &#124; launch:deferred。 對於 launch::sync，請使用 launch::deferred。 請參閱 [launch 列舉](../Topic/launch%20Enumeration.md)。  
  
###  <a name="BK_MFC"></a> MFC 和 ATL  
  
-   **Microsoft Foundation Classes \(MFC\)** 因為其大小太大而不再隨附於 Visual Studio 的「一般」安裝。 若要安裝 MFC，請在 Visual Studio 2015 安裝程式中選擇 \[自訂\] 安裝選項。 如果您已經安裝 Visual Studio 2015，您可以重新執行 Visual Studio 安裝程式，選擇 \[自訂\] 安裝選項，以及選擇 Microsoft Foundation Classes 來安裝 MFC。 從 \[控制台\]、\[程式和功能\]，或從安裝媒體，您可以重新執行 Visual Studio 安裝程式。  
  
     Visual C\+\+ 可轉散發套件仍然包含這個程式庫。  
  
###  <a name="BK_ConcRT"></a> 並行執行階段  
  
-   **從 Windows.h 產生的巨集與 concurrency::Context::Yield 發生衝突**  
  
     並行執行階段之前使用 \#undef 取消 Yield 巨集的定義，以避免 Windows.h h 和 concurrency::Context::Yield 函式中定義的 Yield 巨集之間發生衝突。 已經移除這個 \#undef，而且已加入新的非衝突對等應用程式開發介面呼叫 [concurrency::Context::YieldExecution](../Topic/Context::YieldExecution%20Method.md)。 若要解決 Yield 的衝突，您可以更新您的程式碼，改成呼叫 YieldExecution 函式，或在呼叫位置將 Yield 函式名稱加上括弧，如下列範例所示：  
  
    ```  
    (concurrency::Context::Yield)();  
    ```  
  
## 請參閱  
 [快速入門](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)   
 [Visual C\+\+ 2013 的重大變更](https://msdn.microsoft.com/library/hh409293.aspx)