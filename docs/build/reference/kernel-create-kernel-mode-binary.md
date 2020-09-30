---
title: /kernel (建立核心模式二進位檔)
description: Microsoft C/c + + 編譯器/kernel 選項會建立和連結專案以進行核心模式執行。
ms.date: 09/28/2020
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: 8a8c02a6f102a52afbc52c154ce215ede3f38f74
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509354"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (建立核心模式二進位檔)

建立可在 Windows 核心中執行的二進位檔。 目前專案中的程式碼會使用一組簡化的 c + + 語言功能進行編譯和連結，這些功能是以核心模式執行的程式碼所特有。

## <a name="syntax"></a>語法

> **`/kernel`**

## <a name="remarks"></a>備註

指定 **`/kernel`** 選項會指示編譯器和連結器仲裁哪些語言功能可在核心模式中使用，並確保您有足夠的表達能力，以避免對核心模式 c + + 而言是唯一的執行時間不穩定。 這是藉由禁止使用在核心模式中干擾的 c + + 語言功能來完成。 編譯器會產生可能幹擾性但無法停用之 c + + 語言功能的警告。

此 **`/kernel`** 選項同時適用于組建的編譯器和連結器階段，並且是在專案層級設定。 傳遞 **`/kernel`** 參數以向編譯器指出在連結之後產生的二進位檔應該載入至 Windows 核心。 編譯器會將 c + + 語言功能的範圍縮小為與核心相容的子集。

下表列出指定時編譯器行為的變更 **`/kernel`** 。

| 行為類型 | **`/kernel`** 行為 |
|--|--|
| C++ 例外狀況處理 | 停用。 **`throw`** 除了例外狀況規格) 之外，和關鍵字的所有實例都會 **`try`** 發出編譯器錯誤 (`throw()` 。 **`/EH`** 除了以外，沒有任何選項與相容 **`/kernel`** **`/EH-`** 。 |
| RTTI | 停用。 除非以靜態方式 **`dynamic_cast`** 使用，否則和關鍵字的所有實例 **`typeid`** 都會發出編譯器錯誤 **`dynamic_cast`** 。 |
| `new` 和 `delete` | 您必須明確定義 `new()` or `delete()` 運算子。 編譯器和執行時間不提供預設定義。 |

[`/GS`](gs-buffer-security-check.md)當您使用選項時，會允許自訂呼叫慣例、組建選項和所有優化 **`/kernel`** 。 內嵌大部分不會受到的影響 **`/kernel`** ，但編譯器採用相同的語法。 如果您想要確定 **`__forceinline`** 是否接受內嵌限定詞，您必須確定已啟用警告 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ，讓您知道特定函式何時 **`__forceinline`** 未內嵌。

沒有任何 `#pragma` 相當於控制此選項的專案。

當編譯器傳遞 **`/kernel`** 參數時，它會預先定義名為 `_KERNEL_MODE` 且值為 **1**的預處理器宏。 您可以使用這個宏，根據執行環境是在使用者模式或核心模式中，有條件地編譯器代碼。 例如，下列程式碼會指定 `MyNonPagedClass` 當編譯為核心模式執行時，類別應該位於不可分頁的記憶體區段中。

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

下列其中一些目標架構和選項的組合 **`/arch`** 會在搭配使用時產生錯誤 **`/kernel`** ：

- **`/arch:SSE`****`/arch:SSE2`** **`/arch:AVX`** **`/arch:AVX2`** x86 不支援、、、和 **`/arch:AVX512`** 。 只有 **`/arch:IA32`** **`/kernel`** 在 x86 上才支援。

- **`/arch:AVX`****`/arch:AVX2`** **`/arch:AVX512`** 在 x64 上不支援、和 **`/kernel`** 。

使用建立時， **`/kernel`** 也會傳遞 **`/kernel`** 至連結器。 此選項會影響連結器的行為：

- 增量連結已停用。 如果您將加入 **`/incremental`** 至命令列，連結器會發出這個嚴重錯誤：

   **嚴重錯誤 LNK1295： '/INCREMENTAL ' 與 '/KERNEL ' 規格不相容;沒有 '/INCREMENTAL ' 的連結**

- 連結器會檢查每個物件檔 (或靜態程式庫中任何包含的封存成員) 以查看它是否可能已使用選項進行編譯，但不是 **`/kernel`** 。 如果任何實例符合此準則，連結器仍會成功連結，但可能會發出警告，如下表所示。

   | 命令 | **`/kernel`** Obj | 非 **`/kernel`** obj、MASM obj 或 cvtres obj | 混合 **`/kernel`** 和非 **`/kernel`** obj |
   |--|--|--|--|
   | **`link /kernel`** | 是 | 是 | 是，警告 LNK4257 |
   | **`link`** | 是 | 是 | 是 |

   **未以/KERNEL 編譯的 LNK4257 連結化物件;映射可能無法執行**

**`/kernel`** 選項和選項會 **`/driver`** 獨立運作。 它們彼此不會有任何作用。

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/kernel 編譯器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +**  >  **命令列**] 屬性頁。

1. 在 [ **其他選項** ] 方塊中，加入 *`/kernel`* 。 選擇 **[確定]** 或 [套用] 以儲存 **您的變更** 。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
