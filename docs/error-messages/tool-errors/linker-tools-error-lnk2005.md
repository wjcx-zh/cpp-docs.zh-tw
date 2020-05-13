---
title: 連結器工具錯誤 LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353231"
---
# <a name="linker-tools-error-lnk2005"></a>連結器工具錯誤 LNK2005

> *定義*物件定義的符號

符號*已*多次定義。

錯誤後跟致命錯誤[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能的原因和解決方案

通常,此錯誤意味著您已損壞*一個定義規則*,該定義規則只允許給定物件檔中任何已使用的範本、函數、類型或物件定義一個定義,並且在整個可執行檔中僅允許一個外部可見物件或函數的定義。

以下是此錯誤的一些常見原因。

- 當標頭檔定義變數時,可能會發生此錯誤。 例如,如果將此標頭檔包含在專案中的多個源檔中,則會導致錯誤:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解決方案包括：

  - 宣告標頭檔中`extern`的變數: `extern int global_int;`,然後定義它,並選擇性地在一個和只有一個源檔案中初始`int global_int = 17;`化 它: 。 此變數現在是一個全域變數,您可以通過聲明它`extern`(例如,包括標頭檔)在任何源檔中使用。 對於必須是全域的變數,我們建議使用此解決方案,但良好的軟體工程實踐可最大限度地減少全域變數。

  - 宣告變數[靜態](../../cpp/storage-classes-cpp.md#static) `static int static_int = 17;`: 這將定義的範圍限制為當前物件檔,並允許多個物件檔具有自己的變數副本。 我們不建議您在頭檔中定義靜態變數,因為可能會與全域變數混淆。 更喜歡將靜態變數定義移動到使用它們的源檔中。

  - 宣告變數[selectany](../../cpp/selectany.md) `__declspec(selectany) int global_int = 17;`: . . 這告訴連結器選擇一個定義供所有外部引用使用,並丟棄其餘。 此解決方案有時在組合導入庫時很有用。 否則,我們不推薦它作為避免連結器錯誤的一種方式。

- 當標頭檔定義不是`inline`的函數時,可能會發生此錯誤。 如果在此標頭檔包含多個源檔中,則可以在可執行檔中獲取該函數的多個定義。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解決方案包括：

  - 將`inline`關鍵字新增到函數:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - 從標頭檔中刪除函數正文,只保留聲明,然後在一個和只有一個源檔案中實現該函數:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- 如果在標頭檔中的類聲明之外定義成員函數,也可能發生此錯誤:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   要解決此問題,在類中移動成員函數定義。 在類聲明中定義的成員函數隱式內聯。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果連結了多個版本的標準庫或 CRT,則可能發生此錯誤。 例如,如果您嘗試將零售庫和調試CRT庫或庫的靜態和動態版本或標準庫的兩個不同版本連結到可執行檔,則此錯誤可能會報告多次。 要解決此問題,請從連結命令中刪除每個庫除一個副本外的所有副本。 我們不建議您將零售庫和調試庫或庫的不同版本混合在同一可執行檔中。

   要告訴連結器在命令列上使用預設值以外的庫,請指定要使用的庫,並使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)選項禁用預設庫。 在 IDE 中,新增對專案的引用以指定要使用的庫,然後打開專案**的屬性頁**對話框,並在 **「連結器**、**輸入**屬性」頁中設定 **「忽略所有預設函式庫**」或 **「忽略特定預設函式庫」** 屬性以禁用預設庫。

- 如果在使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項時混合使用靜態和動態庫,則可能發生此錯誤。 例如,如果建構 DLL 以用於靜態 CRT 中的連結的可執行檔,則可能發生此錯誤。 要解決此問題,請使用靜態庫或僅對整個可執行檔以及生成要在可執行檔中使用的任何庫使用動態庫。

- 如果符號是打包函數(通過編譯[創建)並且](../../build/reference/gy-enable-function-level-linking.md)它包含在多個檔中,但在編譯之間更改,則可能發生此錯誤。 要解決此問題,請重新編譯包含打包函數的所有檔。

- 如果符號在不同的庫中的兩個成員物件中定義不同,並且使用兩個成員物件,則可能發生此錯誤。 當庫以靜態連結時解決此問題的一種方法是僅從一個庫中使用成員物件,並首先在連結器命令行中包括該庫。 要使用這兩個符號,必須創建一種方法來區分它們。 例如,如果可以從源生成庫,則可以將每個庫包裝在一個唯一的命名空間中。 或者,您可以創建一個新的包裝庫,該庫使用唯一名稱來包裝對其中一個原始庫的引用,將新庫連結到原始庫,然後將可執行檔連結到新庫而不是原始庫。

- 如果`extern const`變數定義兩次,並且每個定義中具有不同的值,則可能發生此錯誤。 要解決此問題,請僅定義一次常量,或使用命名空間或`enum class`定義來區分常量。

- 如果將 uuid.lib 與其他定義 GUID 的檔(例如 oledb.lib 和 adiid.lib)結合使用,則可能發生此錯誤。 例如：

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   要解決此問題,請確保將[/FORCE:MULTI](../../build/reference/force-force-file-output.md)添加到連結器命令行選項,並確保 uuid.lib 是第一個引用的庫。
