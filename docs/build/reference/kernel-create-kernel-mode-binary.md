---
title: /kernel (建立核心模式二進位檔)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: bcef52144e4da932e9e1b6acbcd5f2170c4c7f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211940"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (建立核心模式二進位檔)

建立可在 Windows 核心中執行的二進位檔。

## <a name="syntax"></a>語法

```
/kernel[-]
```

## <a name="arguments"></a>引數

**/kernel**<br/>
目前專案中的程式碼會使用一組 c + + 語言規則來進行編譯和連結，而程式碼會以核心模式執行。

**/kernel**<br/>
目前專案中的程式碼會進行編譯和連結，而不會使用將在核心模式中執行的程式碼特定的 c + + 語言規則。

## <a name="remarks"></a>備註

沒有 `#pragma` 對等的可控制此選項。

指定 **/kernel**選項會告知編譯器和連結器，以在核心模式中仲裁允許的語言功能，並確保您有足夠的表達能力來避免核心模式 c + + 特有的執行時間不穩定。 這是藉由禁止使用在核心模式中干擾性的 c + + 語言功能，以及提供可能有干擾但無法停用之 c + + 語言功能的警告，來完成這項作業。

**/Kernel**選項會套用至組建的編譯器和連結器階段，並在專案層級設定。 傳遞 **/kernel**參數，以向編譯器指出所產生的二進位檔在連結之後應該載入至 Windows 核心。 編譯器會將 c + + 語言功能的範圍縮小為與核心相容的子集。

下表列出在指定 **/kernel**時編譯器行為的變更。

|行為類型|**/kernel**表現|
|-------------------|---------------------------|
|C++ 例外狀況處理|已停用。 和關鍵字的所有實例都會 **`throw`** **`try`** 發出編譯器錯誤（例外狀況規格除外 `throw()` ）。 除了 **/EH-** 以外，沒有任何 **/EH**選項與 **/kernel**相容。|
|RTTI|已停用。 **`dynamic_cast`** 除非是以靜態方式使用，否則和關鍵字的所有實例 **`typeid`** 都會發出編譯器錯誤 **`dynamic_cast`** 。|
|`new` 和 `delete`|您必須明確定義 `new()` or `delete()` 運算子; 編譯器和執行時間都不會提供預設定義。|

當您使用 **/kernel**選項時，會允許自訂呼叫慣例、 [/gs](gs-buffer-security-check.md)組建選項和所有優化。 內嵌主要不會受到 **/kernel**的影響，因為編譯器會接受相同的語義。 如果您想要確定已 **`__forceinline`** 接受內嵌限定詞，必須確定已啟用警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ，讓您知道特定函式何時 **`__forceinline`** 未內嵌。

當編譯器傳遞 **/kernel**參數時，它會預先定義名為且值為1的預處理器宏 `_KERNEL_MODE` 。 **1** 您可以根據執行環境是在使用者模式或核心模式中，使用這個來有條件地編譯器代碼。 例如，下列程式碼會指定當編譯成核心模式執行時，類別應該在不可分頁的記憶體區段中。

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

下列一些目標架構和 **/arch**選項的組合，會在與 **/kernel**搭配使用時產生錯誤：

- /arch： x86 上不支援 **&#124;SSE2&#124;AVX} 的 SSE** 。 只有 **/arch： IA32**支援 x86 上的 **/kernel** 。

- **/arch：** 在 x64 上的 **/KERNEL**不支援 AVX。

使用 **/kernel**建立時，也會將 **/kernel**傳遞至連結器。 這會影響連結器的行為：

- 已停用增量連結。 如果您將 **/incremental**加入至命令列，連結器就會發出此嚴重錯誤：

   **連結：嚴重錯誤 LNK1295： '/INCREMENTAL ' 與 '/KERNEL ' 規格不相容;不含 '/INCREMENTAL ' 的連結**

- 連結器會檢查每個物件檔案（或靜態程式庫中任何包含的封存成員），以查看它是否可以使用 **/kernel**選項進行編譯，但不是。 如果有任何實例符合此準則，連結器仍然會成功連結，但可能會發出警告，如下表所示。

   ||**/kernel** obj|**/kernel-** OBJ、MASM obj 或 cvtresed|混合使用 **/kernel**和 **/kernel-** obj|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**連結/kernel**|是|是|是，有警告 LNK4257|
   |**link**|是|是|是|

   **未使用/KERNEL 編譯的 LNK4257 連結化物件映射可能無法執行**

**/Kernel**選項和 **/driver**選項會獨立運作，同時也不會影響另一個。

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/kernel 編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [ **C/c + +** ] 資料夾。

1. 選取 [**命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，新增 `/kernel` 或 `/kernel-` 。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
