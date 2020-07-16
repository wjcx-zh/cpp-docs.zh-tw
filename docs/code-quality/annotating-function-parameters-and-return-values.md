---
title: 標注函式參數和傳回值
description: 函式參數和傳回值注釋的參考指南。
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
ms.openlocfilehash: d2aa57abc6c0bcc50bcae743a50f86e5de65ab64
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404033"
---
# <a name="annotating-function-parameters-and-return-values"></a>標注函式參數和傳回值

本文描述簡單函式參數（純量）和結構和類別的指標，以及大多數類型的緩衝區之注釋的一般用法。 本文也會說明批註的常見使用模式。 如需與函式相關的其他批註，請參閱批註函式[行為](../code-quality/annotating-function-behavior.md)。

## <a name="pointer-parameters"></a>指標參數

針對下表中的批註，當標注指標參數時，分析器會在指標為 null 時報告錯誤。 此注釋適用于指標和指向的任何資料項目。

### <a name="annotations-and-descriptions"></a>注釋和描述

- `_In_`

     標注輸入參數，其為純量、結構、結構的指標，以及 like。 明確可能用於簡單純量。 參數在預先狀態中必須是有效的，而且不會修改。

- `_Out_`

     標注輸出參數，其為純量、結構、結構的指標，以及 like。 請勿將此注釋套用至無法傳回值的物件，例如以傳值方式傳遞的純量。 參數在預先狀態中不一定是有效的，但在後置狀態中必須是有效的。

- `_Inout_`

     標注將由函式變更的參數。 它必須在前置狀態和後置狀態中都是有效的，但假設在呼叫前後有不同的值。 必須套用至可修改的值。

- `_In_z_`

     以 null 結束的字串指標，用來做為輸入。 此字串在前置狀態中必須是有效的。 慣用的變數 `PSTR` 已有正確的批註。

- `_Inout_z_`

     將修改之以 null 結束之字元陣列的指標。 它在呼叫之前和之後都必須是有效的，但假設值已變更。 可以移動 null 結束字元，但只能存取最多到原始 null 結束字元的元素。

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     陣列的指標，由函數讀取。 陣列是大小的 `s` 元素，全部都必須是有效的。

     `_bytes_`Variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此變體。 例如，只有在使用的類似函式 `char` 時，字串才會使用 `_bytes_` variant `wchar_t` 。

- `_In_reads_z_(s)`

     陣列的指標，其以 null 結束且具有已知的大小。 最多為 null 結束字元的元素（ `s` 如果沒有 null 結束字元）必須在前置狀態中有效。 如果大小是以位元組為單位，則會 `s` 依元素大小進行調整。

- `_In_reads_or_z_(s)`

     陣列的指標，其以 null 結束或具有已知大小，或兩者皆為。 最多為 null 結束字元的元素（ `s` 如果沒有 null 結束字元）必須在前置狀態中有效。 如果大小是以位元組為單位，則會 `s` 依元素大小進行調整。 （用於 `strn` 系列）。

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     將由函式寫入之 `s` 元素陣列（resp）的指標。 陣列元素不一定要在前置狀態中有效，而且在後置狀態中有效的元素數目也不會指定。 如果參數類型上有批註，則會在後置狀態下套用。 例如，試想下列程式碼。

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     在此範例中，呼叫者會提供的 `size` 元素緩衝區 `p1` 。 `MyStringCopy`使部分元素有效。 更重要的 `_Null_terminated_` 是，上的注釋 `PWSTR` 表示 `p1` 在後置狀態中是以 null 終止。 如此一來，有效元素的數目仍然定義良好，但不需要特定的元素計數。

     `_bytes_`Variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此變體。 例如，只有在使用的類似函式 `char` 時，字串才會使用 `_bytes_` variant `wchar_t` 。

- `_Out_writes_z_(s)`

     元素陣列的指標 `s` 。 元素在預先狀態中不一定是有效的。 在後置狀態中，已完成 null 結束字元的元素（必須存在）必須是有效的。 如果大小是以位元組為單位，則會 `s` 依元素大小進行調整。

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     陣列的指標，在函式中讀取和寫入。 這是大小 `s` 元素，且在前置狀態和後置狀態中有效。

     `_bytes_`Variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此變體。 例如，只有在使用的類似函式 `char` 時，字串才會使用 `_bytes_` variant `wchar_t` 。

- `_Inout_updates_z_(s)`

     陣列的指標，其以 null 結束且具有已知的大小。 完成 null 結束字元的元素（必須存在）必須是前置狀態和後置狀態中的有效專案。 後置狀態中的值會假設為與前置狀態中的值不同。，其中包括 null 結束字元的位置。 如果大小是以位元組為單位，則會 `s` 依元素大小進行調整。

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     元素陣列的指標 `s` 。 元素在預先狀態中不一定是有效的。 在後置狀態中，最多為 `c` -第個元素的元素必須是有效的。 `_bytes_`如果大小是以位元組為單位，而不是元素數目，則可以使用 variant。

     例如：

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     陣列的指標，這是函式的讀取和寫入。 這是大小的 `s` 元素，全部都必須在前置狀態中有效，而 `c` 元素在後置狀態中必須是有效的。

     `_bytes_`Variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此變體。 例如，只有在使用的類似函式 `char` 時，字串才會使用 `_bytes_` variant `wchar_t` 。

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     陣列的指標，這是由大小元素的函式讀取和寫入 `s` 。 定義為相當於：

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     換句話說，處於前置狀態的緩衝區中的每個元素，在 `s` 前置狀態和後置狀態中都是有效的。

     `_bytes_`Variant 會提供以位元組為單位的大小，而不是元素。 只有當大小無法以元素表示時，才使用此變體。 例如，只有在使用的類似函式 `char` 時，字串才會使用 `_bytes_` variant `wchar_t` 。

- `_In_reads_to_ptr_(p)`

     陣列的指標，其 `p - _Curr_` （也就是 `p` 減號 `_Curr_` ）是有效的運算式。 前面的元素 `p` 必須在前置狀態中有效。

    例如：

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     以 null 結束之陣列的指標，其運算式 `p - _Curr_` （也就是 `p` 減號 `_Curr_` ）是有效的運算式。 前面的元素 `p` 必須在前置狀態中有效。

- `_Out_writes_to_ptr_(p)`

     陣列的指標，其 `p - _Curr_` （也就是 `p` 減號 `_Curr_` ）是有效的運算式。 前面的元素 `p` 不一定要在預先狀態中有效，而且在後置狀態中必須是有效的。

- `_Out_writes_to_ptr_z_(p)`

     以 null 結束之陣列的指標，其 `p - _Curr_` （也就是 `p` 減號 `_Curr_` ）是有效的運算式。 前面的元素 `p` 不一定要在預先狀態中有效，而且在後置狀態中必須是有效的。

## <a name="optional-pointer-parameters"></a>選擇性指標參數

當指標參數注釋包含時 `_opt_` ，它會指出參數可能是 null。 否則，批註的行為會與不包含的版本相同 `_opt_` 。 以下是 `_opt_` 指標參數注釋的變數清單：

:::row:::
    :::column:::
        `_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`
    :::column-end:::
    :::column:::
        `_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`
    :::column-end:::
    :::column:::
        `_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`
    :::column-end:::
:::row-end:::

## <a name="output-pointer-parameters"></a>輸出指標參數

輸出指標參數需要特殊的標記法，以區分參數上的 null 和指向的位置。

### <a name="annotations-and-descriptions"></a>注釋和描述

- `_Outptr_`

   參數不可以是 null，而且在後置狀態中，指向的位置不能是 null，而且必須有效。

- `_Outptr_opt_`

   參數可以是 null，但在後置狀態中，指向的位置不可以是 null，而且必須有效。

- `_Outptr_result_maybenull_`

   參數不可以是 null，而且在後置狀態中，指向的位置可以是 null。

- `_Outptr_opt_result_maybenull_`

   參數可以是 null，而在後置狀態中，指向的位置可以是 null。

  在下表中，其他子字串會插入批註名稱中，以進一步限定注釋的意義。 各種子字串為 `_z` 、 `_COM_` 、 `_buffer_` 、 `_bytebuffer_` 和 `_to_` 。

> [!IMPORTANT]
> 如果您要標注的介面是 COM，請使用這些批註的 COM 形式。 請勿將 COM 注釋與任何其他類型介面搭配使用。

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   傳回的指標具有 `_Null_terminated_` 注釋。

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   傳回的指標具有 COM 語義，這就是為什麼它會產生 `_On_failure_` 傳回的指標為 null 的後置條件。

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   傳回的指標會指向大小 `s` 元素或位元組的有效緩衝區。

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   傳回的指標會指向大小 `s` 元素或位元組的緩衝區，其中第一個 `c` 是有效的。

某些介面慣例假設輸出參數會在失敗時 nullified。 除了明確的 COM 程式碼以外，下表中的表單是慣用的。 針對 COM 程式碼，請使用上一節中所列的對應 COM 表單。

- `_Result_nullonfailure_`

   修改其他批註。 如果函數失敗，結果會設定為 null。

- `_Result_zeroonfailure_`

   修改其他批註。 如果函數失敗，結果會設定為零。

- `_Outptr_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于非選擇性的參數。

- `_Outptr_opt_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于選擇性參數。

- `_Outref_result_nullonfailure_`

   如果函式成功，傳回的指標會指向有效的緩衝區; 如果函式失敗，則為 null。 此注釋適用于參考參數。

## <a name="output-reference-parameters"></a>輸出參考參數

參考參數的常見用法是用於輸出參數。 對於簡單的輸出參考參數（例如 `int&` ），會 `_Out_` 提供正確的語法。 不過，當輸出值是之類的指標時 `int *&` ，類似的指標注釋（例如） `_Outptr_ int **` 不會提供正確的語法。 若要以簡明的表示指標類型的輸出參考參數的語法，請使用下列複合批註：

### <a name="annotations-and-descriptions"></a>注釋和描述

- `_Outref_`

     結果在後置狀態中必須是有效的，而且不能是 null。

- `_Outref_result_maybenull_`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。

- `_Outref_result_buffer_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向大小元素的有效緩衝區 `s` 。

- `_Outref_result_bytebuffer_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向大小為位元組的有效緩衝區 `s` 。

- `_Outref_result_buffer_to_(s, c)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向元素的緩衝區 `s` ，其中第一個 `c` 是有效的。

- `_Outref_result_bytebuffer_to_(s, c)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向 `s` 第一個有效位元組的緩衝區 `c` 。

- `_Outref_result_buffer_all_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向大小有效元素的有效緩衝區 `s` 。

- `_Outref_result_bytebuffer_all_(s)`

     結果在後置狀態中必須是有效的，而且不能是 null。 指向 `s` 有效元素位元組的有效緩衝區。

- `_Outref_result_buffer_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向大小元素的有效緩衝區 `s` 。

- `_Outref_result_bytebuffer_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向大小為位元組的有效緩衝區 `s` 。

- `_Outref_result_buffer_to_maybenull_(s, c)`

     結果在後置狀態中必須是有效的，但在後置狀態中可能是 null。 指向元素的緩衝區 `s` ，其中第一個 `c` 是有效的。

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向 `s` 第一個有效位元組的緩衝區 `c` 。

- `_Outref_result_buffer_all_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向大小有效元素的有效緩衝區 `s` 。

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     結果在後置狀態中必須是有效的，但在 post 狀態中可能會是 null。 指向 `s` 有效元素位元組的有效緩衝區。

## <a name="return-values"></a>傳回值

函式的傳回值類似于 `_Out_` 參數，但位於不同的取消參考層級，而且您不需要考慮結果指標的概念。 針對下列注釋，傳回值是批註物件（純量、結構的指標或緩衝區的指標）。 這些批註與對應的注釋具有相同的語義 `_Out_` 。

:::row:::
    :::column:::
        `_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`
    :::column-end:::
    :::column:::
        `_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`
    :::column-end:::
:::row-end:::

## <a name="format-string-parameters"></a>格式字串參數

- `_Printf_format_string_`指出參數是用於運算式的格式字串 `printf` 。

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

- `_Scanf_format_string_`指出參數是用於運算式的格式字串 `scanf` 。

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

- `_Scanf_s_format_string_`指出參數是用於運算式的格式字串 `scanf_s` 。

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

## <a name="other-common-annotations"></a>其他常見注釋

### <a name="annotations-and-descriptions"></a>注釋和描述

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     參數、欄位或結果會在從到的範圍內（含） `low` `hi` 。 相當於 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` ，其會套用至加上批註的物件，以及適當的前置狀態或後置狀態條件。

    > [!IMPORTANT]
    > 雖然名稱包含「in」和「out」，但和的語義 `_In_` 並 `_Out_` 不適**not**用於這些注釋。

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     標注的值完全是 `expr` 。 相當於 `_Satisfies_(_Curr_ == expr)` ，其會套用至加上批註的物件，以及適當的前置狀態或後置狀態條件。

- `_Struct_size_bytes_(size)`

     適用于結構或類別宣告。 表示該類型的有效物件可能大於宣告的類型，且提供的位元組數目 `size` 。 例如：

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     類型參數的緩衝區大小（以位元組為單位）會被視為 `pM` `MyStruct *` ：

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="see-also"></a>另請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [內建函式](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
