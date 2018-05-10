---
title: dllimport-dllexport 的規則和限制 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e39c3eb9a45c80ff5e855bd5aacbbef5a9533ef6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>dllimport/dllexport 的規則和限制
**Microsoft 特定的**  
  
-   如果您宣告未具有 **dllimport** 或 `dllexport` 屬性的函式，則不會將此函式視為 DLL 介面的一部分。 因此，函式的定義必須存在該模組中，或是相同程式的另一個模組中。 若要讓函式成為 DLL 介面的一部分，您必須在另一個模組中將函式的定義宣告為 `dllexport`。 否則，在建置用戶端時會產生連結器錯誤。  
  
-   如果您程式中的單一模組包含相同函式的 **dllimport** 和 `dllexport` 宣告，則 `dllexport` 屬性會優先於 **dllimport** 屬性。 不過，這樣會產生編譯器警告。 例如:   
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllExport void func1( void );   /* Warning; dllexport */  
                                       /* takes precedence. */  
  
    ```  
  
-   您無法使用以 **dllimport** 屬性宣告的資料物件位址來初始化靜態資料指標。 例如，下列程式碼會產生錯誤：  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport int i;  
       .  
       .  
       .  
       int *pi = &i;                           /* Error */  
  
       void func2()  
       {  
          static int *pi = &i;                   /* Error */  
       }  
  
    ```  
  
-   若使用以 **dllimport** 宣告的函式位址初始化靜態函式指標，會將指標設定為 DLL 匯入 Thunk (將控制權轉至函式的程式碼 Stub) 的位址，而不是設定為函式的位址。 這項指派不會產生錯誤訊息：  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void   
       .  
       .  
       .  
       static void ( *pf )( void ) = &func1;   /* No Error */  
  
       void func2()  
       {  
          static void ( *pf )( void ) = &func1;  /* No Error */  
       }  
  
    ```  
  
-   由於物件宣告中包含 `dllexport` 屬性的程式必須為該物件提供定義，因此您可以使用 `dllexport` 函式的位址初始化全域或區域靜態函式指標。 同樣地，您可以使用 `dllexport` 資料物件的位址初始化全域或區域靜態資料指標。 例如:   
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllImport int i;  
  
       DllExport void func1( void );  
       DllExport int i;  
       .  
       .  
       .  
       int *pi = &i;                            /* Okay */  
       static void ( *pf )( void ) = &func1;    /* Okay */  
  
       void func2()  
       {  
          static int *pi = i;                     /* Okay */  
          static void ( *pf )( void ) = &func1;   /* Okay */  
       }  
  
    ```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [DLL 匯入及匯出函式](../c-language/dll-import-and-export-functions.md)