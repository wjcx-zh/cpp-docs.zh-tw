---
title: 一般規則和限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19a704036ffac974bc99d93996d083733f59d0d4
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943003"
---
# <a name="general-rules-and-limitations"></a>一般規則和限制
## <a name="microsoft-specific"></a>Microsoft 特定的  
  
-   如果您宣告的函式或物件不含**dllimport**或是**dllexport**屬性、 函式或物件不會視為 DLL 介面的一部分。 因此，函式或物件的定義必須存在該模組中，或是相同程式的另一個模組中。 若要讓 DLL 介面的函式或物件的一部分，您必須宣告的函式或其他模組中的物件定義**dllexport**。 否則會產生連結器錯誤。  
  
     如果您宣告的函式或物件具有**dllexport**屬性，其定義必須出現在同一個程式的一些模組。 否則會產生連結器錯誤。  
  
-   如果您的程式中的單一模組同時包含**dllimport**並**dllexport**相同的函式或物件，宣告**dllexport**屬性會優先透過**dllimport**屬性。 不過，這樣會產生編譯器警告。 例如:   
  
    ```cpp 
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   C + + 中，您可以初始化全域宣告或靜態的本機資料指標或以宣告的資料物件位址**dllimport**屬性，在 c 中會產生錯誤此外，您可以初始化靜態區域函式指標宣告的函式的位址**dllimport**屬性。 在 C 中，此類指派會將指標設定為 DLL 匯入 Thunk (將控制權傳送至函式的程式碼 Stub) 的位址，而不是設定為函式的位址。 在 C++ 中，它會將指標設定為函式的位址。 例如:   
  
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
  
     不過，因為它包含程式**dllexport**物件的宣告中的屬性必須提供該程式中的某處的物件的定義，您可以初始化全域或區域靜態函式指標地址**dllexport**函式。 同樣地，您可以在其中初始化全域或區域靜態資料指標的位址**dllexport**資料物件。 例如，下列程式碼不會在 C 或 C++ 中產生錯誤：  
  
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
  
-   如果您套用**dllexport**未標記為基底類別的一般類別**dllexport**，編譯器會產生 C4275。  
  
     如果基底類別是類別樣板的特製化，則編譯器會產生相同的警告。 若要解決這個問題，將標記與基底類別**dllexport**。 類別樣板的特製化的問題是放置的位置 **__declspec （dllexport)**; 不允許您標記類別樣板。 相反地，明確具現化類別範本並將標示與此明確具現化**dllexport**。 例如:   
  
    ```cpp 
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     如果樣板引數為衍生類別，則這個解決方法會失敗。 例如:   
  
    ```cpp 
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     因為這是常見的模式使用範本時，編譯器變更的語意**dllexport**它套用到具有一或多個基底類別的類別，以及一或多個基底類別是類別樣板的特製化. 在此情況下，編譯器會隱含地套用**dllexport**類別樣板的特製化。 您可以執行下列作業，不會收到警告：  
  
    ```cpp 
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)