---
title: 連結器工具錯誤 LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 278f05b8338ac4238d6862fd7b9bd7744f6c8ee5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225211"
---
# <a name="linker-tools-error-lnk2005"></a>連結器工具錯誤 LNK2005

> 物件中已定義的*符號*

符號*符號*定義了一次以上。

這個錯誤後面會接著嚴重錯誤[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能的原因和解決方案

一般來說，此錯誤表示您已中斷*一個定義規則*，這只允許指定之物件檔案中任何使用的範本、函式、類型或物件有一個定義，而對外部可見的物件或函式，在整個可執行檔上只有一個定義。

以下是此錯誤的一些常見原因。

- 標頭檔定義變數時，可能會發生此錯誤。 例如，如果您在專案的多個原始程式檔中包含此標頭檔，則會產生錯誤：

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解決方案包括：

  - **`extern`** 在標頭檔中宣告變數： `extern int global_int;` ，然後定義它，並選擇性地在一個或唯一一個原始檔中初始化 `int global_int = 17;` ：。 這個變數現在是全域的，您可以藉由宣告（ **`extern`** 例如包含標頭檔），在任何原始程式檔中使用它。 對於必須為全域的變數，我們建議此解決方案，但良好的軟體工程實務會將全域變數降至最低。

  - 將變數宣告為[static](../../cpp/storage-classes-cpp.md#static)： `static int static_int = 17;` 。 這會將定義的範圍限制為目前的物件檔案，並允許多個物件檔案擁有自己的變數複本。 我們不建議您在標頭檔中定義靜態變數，因為可能會與全域變數混淆。 偏好將靜態變數定義移至使用它們的原始程式檔中。

  - 宣告變數[selectany](../../cpp/selectany.md)： `__declspec(selectany) int global_int = 17;` 。 這會告訴連結器選擇一個定義以供所有外部參考使用，並捨棄其餘部分。 此解決方案在結合匯入程式庫時有時很有用。 否則，我們不建議將它當做避免連結器錯誤的方法。

- 當標頭檔定義的函式不是時，就會發生這個錯誤 **`inline`** 。 如果您在多個原始程式檔中包含此標頭檔，您會在可執行檔中取得函式的多個定義。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解決方案包括：

  - 將關鍵字新增至函式 **`inline`** ：

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - 移除標頭檔中的函式主體，只保留宣告，然後在一個或唯一一個原始檔中執行函數：

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- 如果您在標頭檔中的類別宣告之外定義成員函式，也可能會發生此錯誤：

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   若要修正此問題，請在類別內移動成員函式定義。 在類別宣告內定義的成員函式會隱含地內嵌。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果您連結了一個以上版本的 standard library 或 CRT，就會發生此錯誤。 例如，如果您嘗試將零售和 debug 的 CRT 程式庫，或是靜態和動態版本的媒體櫃，或是兩個不同版本的標準程式庫都連結至可執行檔，則可能會多次回報此錯誤。 若要修正此問題，請從 link 命令中移除每個程式庫的所有複本，只複製一份。 我們不建議您在相同的可執行檔中混用零售和 debug 程式庫，或不同版本的程式庫。

   若要告知連結器使用預設值，請在命令列中指定要使用的程式庫，並使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)選項來停用預設程式庫。 在 IDE 中，將參考加入至您的專案，以指定要使用的程式庫，然後開啟專案的 [**屬性頁**] 對話方塊，然後在 [**連結器**]、[**輸入**屬性] 頁面中，設定 [**忽略所有預設程式庫**] 或 [**忽略特定的預設**程式庫] 屬性，以停用預設程式庫。

- 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項時，如果混合使用靜態和動態連結程式庫，就會發生這個錯誤。 例如，如果您建立 DLL，以便在靜態 CRT 中連結的可執行檔中使用，就會發生此錯誤。 若要修正此問題，請只針對整個可執行檔和您所建立要在可執行檔中使用的任何程式庫使用靜態程式庫或動態連結程式庫。

- 如果符號是已封裝的函式（使用[/gy](../../build/reference/gy-enable-function-level-linking.md)編譯所建立的），而且它包含在一個以上的檔案中，但在編譯之間已變更，就會發生此錯誤。 若要修正此問題，請重新編譯包含封裝函式的所有檔案。

- 如果在不同程式庫中的兩個成員物件中以不同的方式定義符號，並使用這兩個成員物件，則會發生這個錯誤。 在程式庫以靜態方式連結時，若要修正這個問題，其中一種方法是只使用一個程式庫中的成員物件，然後在連結器命令列上先包含該程式庫。 若要使用這兩個符號，您必須建立區別它們的方式。 例如，如果您可以從來源建立程式庫，您可以將每個程式庫包裝在唯一的命名空間中。 或者，您可以建立新的包裝函式程式庫，它會使用唯一的名稱來將參考包裝到其中一個原始程式庫、將新程式庫連結至原始媒體櫃，然後將可執行檔連結至新的媒體櫃，而不是原始的媒體櫃。

- 如果 `extern const` 變數定義了兩次，而且每個定義都有不同的值，就會發生這個錯誤。 若要修正此問題，請只定義常數一次，或使用命名空間或 **`enum class`** 定義來區分常數。

- 如果您將 uuid 與定義 Guid （例如，oledb 和 adsiid）的其他 .lib 檔案搭配使用，就會發生這個錯誤。 例如：

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   若要修正此問題，請將[/force： MULTIPLE](../../build/reference/force-force-file-output.md)新增至連結器命令列選項，並確定 uuid 是參考的第一個程式庫。
