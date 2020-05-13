---
title: 對函數參數和傳回值進行交代
description: 函數參數和返回值註釋的參考指南。
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328002"
---
# <a name="annotating-function-parameters-and-return-values"></a>對函數參數和傳回值進行交代

本文介紹了註釋對簡單函數參數(scalars)和指向結構和類的指標以及大多數緩衝區的典型用途。 本文還顯示了註釋的常見使用模式。 有關與函數相關的其他註釋,請參閱[註解函數行為](../code-quality/annotating-function-behavior.md)。

## <a name="pointer-parameters"></a>指標參數

對於下表中的註釋,當對指標參數進行批註時,如果指標為空,分析器將報告錯誤。 此註釋適用於指標和指向的任何數據項。

### <a name="annotations-and-descriptions"></a>註解與說明

- `_In_`

     對標量、結構、指向結構的指標等的輸入參數進行符號。 顯式可用於簡單的標量。 參數必須以預狀態有效,並且不會修改。

- `_Out_`

     對標量、結構、指向結構的指標等輸出參數進行分出。 不要將此註釋應用於無法返回值的物件,例如,由值傳遞的標量。 參數不必在預狀態下有效,但必須在後狀態中有效。

- `_Inout_`

     對函數將更改的參數進行加號。 它必須在預狀態和後狀態中都有效,但假定在調用之前和之後具有不同的值。 必須應用於可修改的值。

- `_In_z_`

     指向用作輸入的 null 連接字串的指標。 字串必須以預狀態有效。 首選`PSTR`的 變體,這些變體已具有正確的註釋。

- `_Inout_z_`

     指向將修改的 null 終止字元陣列的指標。 它必須在調用之前和之後有效,但假定該值已更改。 可以移動空終止符,但只能訪問到原始空終止符的元素。

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     指向陣列的指標,該指標由函數讀取。 陣列的大小`s`元素,所有元素都必須有效。

     該`_bytes_`變體以位元組而不是元素的形式提供大小。 僅當大小不能表示為元素時,才使用此變體。 例如,`char`僅當`_bytes_``wchar_t`使用的類似函數使用時,字串才會使用該變體。

- `_In_reads_z_(s)`

     指向為 null 終止且具有已知大小的陣列的指標。 到 null 終止符的元素`s`(或者 如果沒有空終止符)必須在預狀態下有效。 如果大小以位元組為單位已知,則按`s`元素大小縮放。

- `_In_reads_or_z_(s)`

     指向為 null 終止或具有已知大小的陣列的指標,或兩者兼而有之。 到 null 終止符的元素`s`(或者 如果沒有空終止符)必須在預狀態下有效。 如果大小以位元組為單位已知,則按`s`元素大小縮放。 (用於`strn`家庭。

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     指向由函數寫入`s`的元素陣列(resp. 位元組)的指標。 陣列元素不必在預狀態下有效,並且未指定在後狀態下有效的元素數。 如果參數類型上有註釋,則它們以後狀態應用。 例如，試想下列程式碼。

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     這個選項, 以使用元素的`size`緩衝區`p1`。 `MyStringCopy`使其中一些元素有效。 更重要的是,`_Null_terminated_``PWSTR`上的註釋`p1`意味著 在後狀態下為 null 終止。 這樣,有效元素的數量仍然定義良好,但不需要特定的元素計數。

     該`_bytes_`變體以位元組而不是元素的形式提供大小。 僅當大小不能表示為元素時,才使用此變體。 例如,`char`僅當`_bytes_``wchar_t`使用的類似函數使用時,字串才會使用該變體。

- `_Out_writes_z_(s)`

     指向元素陣列的`s`指標。 元素不必在預狀態下有效。 在後狀態中,透過 null 中斷上的元素(必須存在)必須有效。 如果大小以位元組為單位已知,則按`s`元素大小縮放。

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     指向陣列的指標,該陣列在函數中讀取和寫入。 它是大小`s`元素,在狀態前和後狀態有效。

     該`_bytes_`變體以位元組而不是元素的形式提供大小。 僅當大小不能表示為元素時,才使用此變體。 例如,`char`僅當`_bytes_``wchar_t`使用的類似函數使用時,字串才會使用該變體。

- `_Inout_updates_z_(s)`

     指向為 null 終止且具有已知大小的陣列的指標。 通過空終止符向上的元素(必須存在)必須在前狀態和後狀態中有效。 假定后狀態中的值與前狀態中的值不同;包括空終止符的位置。 如果大小以位元組為單位已知,則按`s`元素大小縮放。

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     指向元素陣列的`s`指標。 元素不必在預狀態下有效。 在後狀態下,最多到 -th`c`元素的元素必須有效。 如果`_bytes_`大小以位元組為單位(而不是元素數)已知,則可以使用該變體。

     例如：

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     指向陣列的指標,該指標由函數讀取和寫入。 它是大小`s`元素,所有元素都必須在預狀態下有效,`c`並且 元素必須在後狀態中有效。

     該`_bytes_`變體以位元組而不是元素的形式提供大小。 僅當大小不能表示為元素時,才使用此變體。 例如,`char`僅當`_bytes_``wchar_t`使用的類似函數使用時,字串才會使用該變體。

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     指向陣列的指標,該陣列由大小`s`元素的函數讀取和寫入。 定義為等效於:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     換句話說,緩衝區中一直存在`s`到預狀態的每個元素在預狀態和後狀態中都有效。

     該`_bytes_`變體以位元組而不是元素的形式提供大小。 僅當大小不能表示為元素時,才使用此變體。 例如,`char`僅當`_bytes_``wchar_t`使用的類似函數使用時,字串才會使用該變體。

- `_In_reads_to_ptr_(p)`

     指向陣列的指標`p - _Curr_`(即`p`減`_Curr_`號)是有效的表達式。 之前`p`的元素必須以預狀態有效。

    例如：

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     指向 null 端接陣列的指標,`p - _Curr_`其 運算式`p`(`_Curr_`即減號)是有效的運算式。 之前`p`的元素必須以預狀態有效。

- `_Out_writes_to_ptr_(p)`

     指向陣列的指標`p - _Curr_`(即`p`減`_Curr_`號)是有效的表達式。 之前`p`的元素不必在預狀態中有效,並且必須在後狀態中有效。

- `_Out_writes_to_ptr_z_(p)`

     指向 null 端接陣列的`p - _Curr_`指標`p`(`_Curr_`即負 )是有效的運算式。 之前`p`的元素不必在預狀態中有效,並且必須在後狀態中有效。

## <a name="optional-pointer-parameters"></a>選擇式指標參數

當指標參數註釋包含`_opt_`時,它指示參數可能為空。 否則,註釋的表示行為與不包含的版本相同`_opt_`。 下面是指針參數註釋`_opt_`的變體清單:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>輸出指標參數

輸出指標參數需要特殊的表示法來消除參數和指向位置的空值。

### <a name="annotations-and-descriptions"></a>註解與說明

- `_Outptr_`

   參數不能為空,在後狀態下,指向位置不能為空,並且必須有效。

- `_Outptr_opt_`

   參數可能為空,但在後狀態下,指向位置不能為空,並且必須有效。

- `_Outptr_result_maybenull_`

   參數不能為空,在後狀態下,指向位置可以為空。

- `_Outptr_opt_result_maybenull_`

   參數可能為空,在後狀態下,指向位置可以為空。

  在下表中,其他子字串將插入到註釋名稱中,以進一步限定註釋的含義。 各種`_z`子字串是 、、、`_bytebuffer_``_to_``_COM_``_buffer_`與 。

> [!IMPORTANT]
> 如果要註釋的介面是 COM,請使用這些註註的 COM 形式。 不要將 COM 註釋與任何其他類型介面一起使用。

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   返回的指標具有`_Null_terminated_`註釋。

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   返回的指標具有 COM 語義,因此帶有`_On_failure_`返回的指標為空的後條件。

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   返回的指標指向大小`s`元素或位元組的有效緩衝區。

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   返回的指標指向大小`s`元素或位元組的緩衝區,其中第一`c`個緩衝區有效。

某些介面約定假定輸出參數在失敗時無效。 除了顯式 COM 代碼之外,首選下表中的窗體。 對於 COM 代碼,請使用上一節中列出的相應的 COM 窗體。

- `_Result_nullonfailure_`

   修改其他註釋。 如果函數失敗,結果將設置為 null。

- `_Result_zeroonfailure_`

   修改其他註釋。 如果函數失敗,結果將設置為零。

- `_Outptr_result_nullonfailure_`

   如果函數成功,返回的指標指向有效緩衝區;如果函數失敗,則返回的指標指向空緩衝區。 此註釋適用於非可選參數。

- `_Outptr_opt_result_nullonfailure_`

   如果函數成功,返回的指標指向有效緩衝區;如果函數失敗,則返回的指標指向空緩衝區。 此註釋適用於可選參數。

- `_Outref_result_nullonfailure_`

   如果函數成功,返回的指標指向有效緩衝區;如果函數失敗,則返回的指標指向空緩衝區。 此註釋用於參考參數。

## <a name="output-reference-parameters"></a>輸出參考參數

參考參數的常見用途是輸出參數。 對於簡單的輸出引用參數,如`int&``_Out_`, 提供了正確的語義。 但是,當輸出值是指針(如`int *&`)時,等效指標註釋(如`_Outptr_ int **`)不提供正確的語義。 要簡潔地表示指標類型的輸出引用參數的語義,請使用以下復合註釋:

### <a name="annotations-and-descriptions"></a>註解與說明

- `_Outref_`

     結果必須在後狀態中有效,並且不能為 null。

- `_Outref_result_maybenull_`

     結果必須在後狀態中有效,但在後狀態時可能為空。

- `_Outref_result_buffer_(s)`

     結果必須在後狀態中有效,並且不能為 null。 指向大小`s`元素的有效緩衝區。

- `_Outref_result_bytebuffer_(s)`

     結果必須在後狀態中有效,並且不能為 null。 指向大小`s`位元組的有效緩衝區。

- `_Outref_result_buffer_to_(s, c)`

     結果必須在後狀態中有效,並且不能為 null。 指向元素的`s`緩衝區,其中第一`c`個有效。

- `_Outref_result_bytebuffer_to_(s, c)`

     結果必須在後狀態中有效,並且不能為 null。 指向第一個`s``c`有效位元組的緩衝區。

- `_Outref_result_buffer_all_(s)`

     結果必須在後狀態中有效,並且不能為 null。 指向大小`s`有效元素的有效緩衝區。

- `_Outref_result_bytebuffer_all_(s)`

     結果必須在後狀態中有效,並且不能為 null。 指向有效元素`s`位元組的有效緩衝區。

- `_Outref_result_buffer_maybenull_(s)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向大小`s`元素的有效緩衝區。

- `_Outref_result_bytebuffer_maybenull_(s)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向大小`s`位元組的有效緩衝區。

- `_Outref_result_buffer_to_maybenull_(s, c)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向元素的`s`緩衝區,其中第一`c`個有效。

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向第一個`s``c`有效位元組的緩衝區。

- `_Outref_result_buffer_all_maybenull_(s)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向大小`s`有效元素的有效緩衝區。

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     結果必須在後狀態中有效,但在後狀態時可能為空。 指向有效元素`s`位元組的有效緩衝區。

## <a name="return-values"></a>傳回值

函數的返回值類似於`_Out_`參數,但處於不同的去引用級別,您不必考慮指向結果的指標的概念。 對於以下註釋,返回值是註釋的物件 - 標量、指向結構的指標或指向緩衝區的指標。 這些註釋的語義與相應的`_Out_`註釋相同。

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>格式化字串參數

- `_Printf_format_string_`指示參數是用於表達式的`printf`格式字串。

     **範例**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`指示參數是用於表達式的`scanf`格式字串。

     **範例**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`指示參數是用於表達式的`scanf_s`格式字串。

     **範例**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>其他常見註解

### <a name="annotations-and-descriptions"></a>註解與說明

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     參數、欄位或結果在從`low`到`hi`的範圍(包括)中。 等效於`_Satisfies_(_Curr_ >= low && _Curr_ <= hi)`該物件應用於帶標的物件以及適當的前狀態或後狀態條件。

    > [!IMPORTANT]
    > 儘管名稱包含"in"和"out",但和`_In_``_Out_`的語義**不適用於**這些註釋。

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     已用的已用值正是`expr`。 等效於`_Satisfies_(_Curr_ == expr)`該物件應用於帶標的物件以及適當的前狀態或後狀態條件。

- `_Struct_size_bytes_(size)`

     應用於結構或類聲明。 指示該類型的有效物件可能大於聲明的類型,由給出`size`的位元組數。 例如：

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     然後,以類型`pM``MyStruct *`參數的位元組為單位的緩衝區大小將採用:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>相關資源

[程式碼分析團隊部落格](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>另請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [內在函數](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
