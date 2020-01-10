---
title: 一般規則和限制
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 3bd8956b08d3e5f2109c5574802a3a8a72fba537
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857524"
---
# <a name="general-rules-and-limitations"></a>一般規則和限制

**Microsoft 專屬**

- 如果您宣告不含**dllimport**或**dllexport**屬性的函式或物件，則函數或物件不會被視為 DLL 介面的一部分。 因此，函式或物件的定義必須存在該模組中，或是相同程式的另一個模組中。 若要讓函式或物件成為 DLL 介面的一部分，您必須在另一個模組中將函式或物件的定義宣告為**dllexport**。 否則會產生連結器錯誤。

   如果您宣告具有**dllexport**屬性的函式或物件，其定義必須出現在同一個程式的某些模組中。 否則會產生連結器錯誤。

- 如果程式中的單一模組同時包含相同函式或物件的**dllimport**和**dllexport**宣告，則**dllexport**屬性會優先于**dllimport**屬性。 不過，這樣會產生編譯器警告。 例如：

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- 在C++中，您可以初始化全域宣告或靜態本機資料指標，或使用以**dllimport**屬性宣告的資料物件位址，這會在 C 中產生錯誤。此外，您可以使用以**dllimport**屬性宣告之函式的位址來初始化靜態區域函式指標。 在 C 中，此類指派會將指標設定為 DLL 匯入 Thunk (將控制權傳送至函式的程式碼 Stub) 的位址，而不是設定為函式的位址。 在 C++ 中，它會將指標設定為函式的位址。 例如：

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

   不過，因為在物件的宣告中包含**dllexport**屬性的程式必須在程式中的某處提供該物件的定義，您可以使用**dllexport**函式的位址來初始化全域或區域靜態函式指標。 同樣地，您可以使用**dllexport**資料物件的位址來初始化全域或本機靜態資料指標。 例如，下列程式碼不會在 C 或 C++ 中產生錯誤：

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- 如果您將**dllexport**套用至具有未標記為**dllexport**之基類的一般類別，則編譯器會產生 C4275。

   如果基底類別是類別樣板的特製化，則編譯器會產生相同的警告。 若要解決這個情況，請使用**dllexport**標記基類。 類別樣板的特製化問題在於放置 **__declspec （dllexport）** 的位置;您不能標記類別範本。 相反地，請明確將類別樣板具現化，並以**dllexport**標記此明確具現化。 例如：

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   如果樣板引數為衍生類別，則這個解決方法會失敗。 例如：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   因為這是使用樣板的常見模式，所以編譯器會在套用至具有一或多個基類的類別，以及當一個或多個基類是類別樣板的特製化時，變更**dllexport**的語法。 在此情況下，編譯器會隱含地將**dllexport**套用至類別樣板的特製化。 您可以執行下列動作，而不會收到警告：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[dllexport、dllimport](../cpp/dllexport-dllimport.md)