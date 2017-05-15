---
title: "連結器工具錯誤 LNK2005 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 40097ea2b5c5519a5b883aad09788cf2f802ea36
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk2005"></a>連結器工具錯誤 LNK2005
*符號*已定義於物件  
  
符號*符號*定義了一次以上。   
  
此錯誤後面是嚴重錯誤[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### <a name="possible-causes-and-solutions"></a>可能原因和解決方案  
  
一般而言，此錯誤表示您中斷*一個定義規則*，可讓任何使用的範本、 函數、 類型或物件在指定的物件檔案中，只有一個定義並只有一個定義在外部可見的物件或函式的整個可執行檔。  
  
以下是一些常見原因造成此錯誤。  
  
-   標頭檔中定義的變數時，會發生此錯誤。 例如，如果您專案中，多個原始程式檔中包含此標頭檔，會產生錯誤︰  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    可能的解決方案包括：  
  
    -   宣告變數`extern`標頭檔︰ `extern int global_int;`，然後定義它，並選擇性地將它初始化只能有一個原始程式檔中︰ `int global_int = 17;`。 此變數現在是全域您可以使用任何原始程式檔中藉由宣告它`extern`，例如，透過包含標頭檔。 我們建議此解決方案必須是全域的變數，但軟體工程設計做法降到最低的全域變數。  
    
    -   宣告變數[靜態](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`。 這會限制到目前的物件檔，定義的範圍，並可讓多個目的檔，以便擁有其自己的變數複本。 我們不建議您在標頭檔中定義靜態變數因為可能會與全域變數產生混淆。 想要將靜態變數的定義移到原始程式檔使用它們。  
  
    -   宣告變數[selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`。 這會告訴連結器的所有外部參考，挑選一個定義以供使用，並捨棄其餘部分。 合併匯入程式庫時，此解決方案有時候是很有用。 否則，我們不建議您這麼做用來避免發生連結器錯誤。  
  
-   標頭檔定義不是函式時，會發生此錯誤`inline`。 如果您在一個以上的原始程式檔中包含此標頭檔，您會取得多個定義的函式可執行檔中。  
    
    ```h  
    // LNK2005_func.h  
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    可能的解決方案包括：  
  
    -   新增`inline`函式的關鍵字︰ 

        ```h  
        // LNK2005_func_inline.h  
        inline int sample_function(int k) { return 42 * (k % 167); }  
        ```  
  
    -   標頭檔中移除函式主體，保留的宣告，然後實作函式只能有一個原始程式檔中︰  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   如果您定義在類別宣告之外的成員函式標頭檔中，也會發生這個錯誤︰  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    若要修正此問題，請移動類別內的成員函式定義。 在類別宣告內定義的成員函式是以隱含方式內嵌的。  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   如果您將連結的標準程式庫或 CRT 的多個版本，就會發生此錯誤。 例如，如果您嘗試同時零售版和偵錯 CRT 程式庫，或連結的程式庫，靜態和動態版本，或者兩個不同的標準程式庫版本可執行檔，此錯誤可能會報告多次。 若要修正此問題，請從連結命令移除所有某一個複本的每個程式庫。 我們不建議您混用零售和偵錯程式庫或文件庫，在相同的可執行檔中的不同版本。  
  
    若要告知連結器命令列使用程式庫以外的預設值，指定 使用，並使用程式庫[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)選項以停用的預設程式庫。 在 IDE 中，將參考加入至專案，以指定的程式庫來使用，然後開啟**屬性頁**對話方塊，您的專案，然後在**連結器**，**輸入**屬性頁上，設定**忽略所有預設程式庫**，或**忽略特定的預設程式庫**屬性停用的預設程式庫。   
  
-   如果您混用使用的靜態和動態程式庫，當您使用時，會發生此錯誤[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。 比方說，如果您使用的 DLL 中建置可執行檔中靜態 CRT 連結，會發生此錯誤。 若要修正此問題，只有靜態程式庫或文件庫動態只可執行檔整個和使用您建置使用可執行檔中的任何程式庫。  
  
-   如果符號為封裝函式，會發生此錯誤 (編譯以建立[/Gy](../../build/reference/gy-enable-function-level-linking.md)) 和它包含在多個檔案，但編譯之間不同。 若要修正此問題，請重新編譯包含封裝的函式的所有檔案。  
  
-   如果在不同的程式庫的兩個成員物件中定義的符號不同，而且兩個成員物件可用，就會發生此錯誤。 以靜態方式連結程式庫時，修正此問題的一個方法是從只有一個程式庫，使用成員物件，並將該程式庫包含連結器命令列上的第一次。 若要使用這兩個符號，您必須建立方式，以加以區別。 比方說，如果您可以建立從來源文件庫，您可以包裝每個媒體櫃中唯一的命名空間。 或者，您可以建立新的包裝函式程式庫使用換行的其中一個原始程式庫的參考，請將新的程式庫連結至原始程式庫，然後將可執行檔連結至您新的程式庫，而不是原始程式庫的唯一名稱。  
  
-   如果，可能會發生這個錯誤`extern const`變數會定義兩次，並在每個定義中有不同的值。 若要修正此問題，請在定義常數只能出現一次，或使用命名空間或`enum class`區別常數定義。  
  
-   如果您 uuid.lib 與其他定義 Guid （例如 oledb.lib 和 adsiid.lib） 的.lib 檔，會發生此錯誤。 例如:   
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要修正此問題，請加入[/force: multiple 都會](../../build/reference/force-force-file-output.md)連結器命令列選項，並確定 uuid.lib 是第一個參考的程式庫。
  
## <a name="additional-information"></a>其他資訊  
  
如果您使用較舊版本的工具組，請參閱下列知識庫文章，如需有關此錯誤的特定原因︰  
  
-   [以錯誤的順序，在 Visual c + + 連結的 CRT 程式庫和 MFC 程式庫時，就會發生 LNK2005 錯誤](https://support.microsoft.com/kb/148652)  
  
-   [修正︰ 全域多載的刪除運算子原因發生 LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [當您編譯 Visual c + + ATL 可執行檔 (.exe) 專案，您會收到發生 LNK2005 錯誤](https://support.microsoft.com/kb/184235)。  
  

