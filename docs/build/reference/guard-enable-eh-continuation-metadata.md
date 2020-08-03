---
title: /guard:ehcont (啟用 EH 接續中繼資料)
description: Microsoft c + +/guard： ehcont 編譯器選項的參考指南。
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: 0c5a49d578e626d052aa9d132afbaee5686cb7a7
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520521"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>/guard:ehcont (啟用 EH 接續中繼資料)

可讓編譯器產生 EH 接續（EHCONT）中繼資料。

## <a name="syntax"></a>Syntax

> **`/guard:ehcont`**[**`-`**]

## <a name="remarks"></a>備註

**`/guard:ehcont`** 選項會使編譯器針對二進位檔的所有有效例外狀況處理接續目標，產生其相對虛擬位址（RVA）的排序清單。 它會在執行時間用於 `NtContinue` 和 `SetThreadContext` 指令指標驗證。 根據預設， **`/guard:ehcont`** 會關閉，而且必須明確啟用。 若要明確停用此選項，請使用 **`/guard:ehcont-`** 。

**`/guard:ehcont`** Visual Studio 2019 16.7 版和更新版本提供選項。 64位作業系統上的64位處理常式支援此功能。

[控制流程強制技術（CET）](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)是以硬體為基礎的安全性功能，可保護以傳回導向程式設計（ROP）為基礎的攻擊。 它會針對每個呼叫堆疊維護「陰影堆疊」，以強制執行控制流程完整性。

當陰影堆疊可用來防止 ROP 攻擊時，攻擊者會繼續使用其他惡意探索技術。 其可能使用的一項技巧是在[內容](/windows/win32/api/winnt/ns-winnt-context)結構內損毀指令指標值。 這個結構會傳遞至重新導向執行緒執行的系統呼叫，例如 `NtContinue` 、 [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) 和 [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) 。 `CONTEXT`結構會儲存在記憶體中。 損毀它所包含的指令指標，可能會導致系統呼叫將執行轉移到攻擊者控制的位址。 目前， `NTContinue` 可以使用任何接續點呼叫。 這就是為什麼在啟用陰影堆疊時驗證指令指標很重要的原因。

`RtlRestoreContext`和 `NtContinue` 會在結構化例外狀況處理（SEH）例外狀況回溯期間用於回溯至包含區塊的目標框架 **`__except`** 。 區塊的指令指標 **`__except`** 不應該位於陰影堆疊上，因為它會失敗指令指標驗證。 **`/guard:ehcont`** 編譯器參數會產生「EH 接續資料表」。 其中包含二進位中所有有效例外狀況處理接續目標的 Rva 排序清單。 `NtContinue`會先檢查使用者提供的指令指標的陰影堆疊，如果在該處找不到指令指標，則會繼續從包含指令指標的二進位檔檢查 EH 接續資料表。 如果包含的二進位檔未與資料表一起編譯，則可以繼續進行與舊版二進位檔的相容性 `NtContinue` 。 請務必區分沒有 EHCONT 資料的舊版二進位檔，以及包含 EHCONT 資料但不含資料表專案的二進位檔。 前者會允許二進位檔內的所有位址成為有效的接續目標。 後者不允許二進位檔內的任何位址做為有效的接續目標。

**`/guard:ehcont`** 選項必須同時傳遞給編譯器和連結器，以產生二進位檔的 EH 接續目標 rva。 如果您的二進位檔是使用單一 `cl` 命令建置，則編譯器會將選項傳遞給連結器。 編譯器也會將 [**`/guard:cf`**](guard-enable-control-flow-guard.md) 選項傳遞給連結器。 如果您分別編譯和連結，則必須同時在編譯器和連結器命令上設定這些選項。

您可以將使用編譯的程式碼連結 **`/guard:ehcont`** 至不含它的編譯庫和物件檔案。 連結器會在下列任何一種情況下傳回嚴重錯誤：

- 程式碼區段具有「本機回溯」。 如需詳細資訊，請參閱[try Finally 語句](../../cpp/try-finally-statement.md#abnormal-termination)中的異常終止。

- EH （.xdata）區段包含程式碼區段的指標，而不是 SEH。

- 指標適用于 SEH，但未使用函式層級連結（[/gy](gy-enable-function-level-linking.md)）來編譯物件檔案，以產生 comdat。

連結器會傳回嚴重錯誤，因為在這些情況下無法產生中繼資料。 這表示擲回例外狀況可能會在執行時間造成損毀。

若為 Comdat 中找到的 SEH 區段資訊，但未使用進行編譯， **`/guard:ehcont`** 則連結器會發出警告**LNK4291**。 在此情況下，連結器會為區段產生正確但保守的中繼資料。 若要忽略此警告，請使用[/IGNORE （忽略特定的警告）](ignore-ignore-specific-warnings.md)。

如果連結器無法產生中繼資料，它會發出下列其中一個錯誤：

- `LNK2046: module contains _local_unwind but was not compiled with /guard:ehcont`

- `LNK2047: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

若要檢查二進位檔是否包含 EHCONT 資料，請在傾印二進位載入設定時，尋找下列元素：

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +** 程式  >  **代碼產生**] 屬性頁。

1. 選取 [**啟用 EH 接續中繼資料**] 屬性。

1. 在下拉式清單控制項中，選擇 **[是] \ （/guard： ehcont）** 以啟用 EH 接續中繼資料，或選取 [**否] （/guard： ehcont-）** 來停用它。

## <a name="see-also"></a>另請參閱

[/guard （啟用控制流程防護）](guard-enable-control-flow-guard.md)\
[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
