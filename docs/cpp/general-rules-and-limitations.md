---
title: "一般規則和限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7295cfad3d5194de6a80a15e8e186089a0f033f
ms.sourcegitcommit: ce115fcfb20b4fbc198f0f7b6d0ca3e94d7ce947
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="general-rules-and-limitations"></a>一般規則和限制
## <a name="microsoft-specific"></a>Microsoft 特定的  
  
-   如果您宣告的函式或物件，而不**dllimport**或`dllexport`屬性、 函式或物件不會視為 DLL 介面的一部分。 因此，函式或物件的定義必須存在該模組中，或是相同程式的另一個模組中。 若要讓函式或物件成為 DLL 介面的一部分，您必須在另一個模組中將函式或物件的定義宣告為 `dllexport`。 否則會產生連結器錯誤。  
  
     如果您宣告的函式或物件具有 `dllexport` 屬性，則其定義必須出現在相同程式的一些模組中。 否則會產生連結器錯誤。  
  
-   如果您的程式中的單一模組同時包含**dllimport**和`dllexport`宣告相同的函式或物件，`dllexport`屬性會優先於**dllimport**屬性。 不過，這樣會產生編譯器警告。 例如:   
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   C + + 中，您可以初始化全域宣告或靜態區域資料指標或以宣告的資料物件位址**dllimport**屬性，會產生錯誤，在 c 中。此外，您可以初始化靜態區域函式指標宣告的函式的位址**dllimport**屬性。 在 C 中，此類指派會將指標設定為 DLL 匯入 Thunk (將控制權傳送至函式的程式碼 Stub) 的位址，而不是設定為函式的位址。 在 C++ 中，它會將指標設定為函式的位址。 例如：  
  
    ```  
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
  
     不過，由於物件宣告中包含 `dllexport` 屬性的程式必須在程式的某個位置為該物件提供定義，因此您可以使用 `dllexport` 函式的位址初始化全域或區域靜態函式指標。 同樣地，您可以使用 `dllexport` 資料物件的位址初始化全域或區域靜態資料指標。 例如，下列程式碼不會在 C 或 C++ 中產生錯誤：  
  
    ```  
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
  
-   如果您套用`dllexport`未標示為基底類別的一般類別`dllexport`，編譯器會產生 C4275。  
  
     如果基底類別是類別樣板的特製化，則編譯器會產生相同的警告。 若要解決這個問題，請為基底類別加上 `dllexport` 標記。 類別樣板的特製化的問題是放置**__declspec （dllexport)**; 不允許您標記類別樣板。 相反地，您可以明確的具現化類別樣板，以及明確地使用 `dllexport` 標記具現化。 例如：  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     如果樣板引數為衍生類別，則這個解決方法會失敗。 例如：  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     因為這是使用樣板的通用樣式，而當編譯器在將 `dllexport` 套用至具有一個或多個基底類別的類別，以及有一個或多個基底類別是類別樣板的特製化時，會改變它的語意。 在這種情況下，編譯器會以隱含方式將 `dllexport` 套用至類別樣板的特製化。 您可以執行下列作業，不會收到警告：  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)