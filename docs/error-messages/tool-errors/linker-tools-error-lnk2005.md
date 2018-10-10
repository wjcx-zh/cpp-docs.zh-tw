---
title: 連結器工具錯誤 LNK2005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3dbb1d63e7d7c6f5e036fc0cde967277c91a40
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890121"
---
# <a name="linker-tools-error-lnk2005"></a>連結器工具錯誤 LNK2005

> *符號*已定義於物件

符號*符號*已定義一次以上。

此錯誤後面是嚴重錯誤[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能原因和解決方案

一般而言，此錯誤表示您中斷*一個定義規則*，可讓任何使用的範本、 函數、 類型或物件在指定的物件檔案中，只有一個定義，只有一個定義跨越整個可執行檔外部可見的物件或函式。

以下是一些常見原因造成此錯誤。

- 標頭檔中定義的變數時，會發生此錯誤。 例如，如果您在專案中，多個原始程式檔中包含此標頭檔，會發生錯誤：

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解決方案包括：

   - 將變數宣告`extern`標頭檔中： `extern int global_int;`，然後定義它，並選擇性地將它初始化只能有一個原始程式檔中： `int global_int = 17;`。 此變數現在是全域您可以使用任何原始程式檔中宣告它`extern`，例如，包含標頭檔。 我們建議的變數必須是全域的此解決方案，但良好的軟體工程實務降到最低的全域變數。

   - 將變數宣告[靜態](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`。 這會限制目前的物件檔中，以定義的範圍，並可讓多個目的檔，以便有自己的變數複本。 我們不建議您在標頭檔中定義靜態變數因為可能會發生與全域變數產生混淆。 想要將靜態變數的定義移到原始程式檔使用它們。

   - 將變數宣告[selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`。 這會告訴連結器的所有外部參考，挑選一個定義以供使用，並捨棄其餘部分。 有時候合併匯入程式庫時，此解決方案是很有用。 否則，我們不建議您這麼做來避免連結器錯誤。

- 標頭檔定義不是函式時，會發生此錯誤`inline`。 如果您在多個原始程式檔中包含此標頭檔，您會取得多個定義的函式可執行檔。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解決方案包括：

   - 新增`inline`函式的關鍵字：

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - 移除標頭檔中的函式主體，並保留的宣告，然後實作函式中只能有一個原始程式檔：

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- 如果您的標頭檔中定義成員函式，在類別宣告之外，也會發生此錯誤：

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   若要修正此問題，請移動類別內的成員函式定義。 在類別宣告內定義的成員函式會以隱含方式內嵌。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果您連結的 CRT 的標準程式庫的多個版本，就會發生此錯誤。 比方說，如果您嘗試同時零售和偵錯 CRT 程式庫，或連結程式庫中，靜態和動態版本或標準程式庫的兩個不同版本到可執行檔時，可能會報告此錯誤的次數。 若要修正此問題，請將所有保留一個複本的每個程式庫移除連結 命令。 我們不建議您混用零售和偵錯程式庫或不同版本，請在程式庫，在相同的可執行檔。

   若要告訴連結器命令列使用程式庫以外的預設值，指定 使用，並使用程式庫[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)選項以停用的預設程式庫。 在 IDE 中，將參考加入至您的專案，以指定的程式庫，以使用此項目，然後再開啟**屬性頁**對話方塊，您的專案，然後在**連結器**，**輸入**屬性頁面上，設定**忽略所有預設程式庫**，或**忽略特定的預設程式庫**屬性，以停用的預設程式庫。

- 如果您混用靜態和動態程式庫的使用，當您使用時，會發生此錯誤[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。 比方說，如果您使用的 DLL 在建置可執行檔靜態 CRT 中的連結，會發生此錯誤。 若要修正此問題，只有靜態程式庫或僅動態程式庫的可執行檔的整個和使用您建置使用可執行檔中的任何程式庫。

- 如果符號為封裝函式，會發生此錯誤 (由編譯[/Gy](../../build/reference/gy-enable-function-level-linking.md)) 和它包含一個以上的檔案中，但編譯之間不同。 若要修正此問題，請重新編譯包含封裝的函式的所有檔案。

- 如果在不同的程式庫的兩個成員物件中以不同的方式定義符號，並用這兩個成員物件，會發生此錯誤。 若要修正此問題，以靜態方式連結程式庫時的一個方法是從只有一個程式庫，使用成員物件，並將該程式庫包含連結器命令列上的第一次。 若要使用這兩種符號，您必須建立方法來區別它們。 比方說，如果您可以建立從來源文件庫，您可以包裝在唯一的命名空間中的每個程式庫。 或者，您可以建立新的包裝函式程式庫，用以包裝至其中一個原始程式庫的參考，將新的程式庫連結至原始的程式庫，然後將可執行檔連結至您新的程式庫，而不是原始的程式庫的唯一名稱。

- 如果會發生此錯誤`extern const`變數定義了兩次，並在每個定義中有不同的值。 若要修正此問題，請定義常數的唯一一次，或使用命名空間或`enum class`來區別常數的定義。

- 如果您將 uuid.lib 與其他定義 Guid （例如 oledb.lib 和 adsiid.lib） 的.lib 檔案，就會發生此錯誤。 例如: 

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   若要修正此問題，請新增[/force: multiple 都會](../../build/reference/force-force-file-output.md)連結器命令列選項，並確定 uuid.lib 是第一個參考的程式庫。
