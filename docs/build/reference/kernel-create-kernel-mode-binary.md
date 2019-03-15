---
title: /kernel (建立核心模式二進位檔)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: d065364cf6d3ae824098634c070f3651324aa52a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816447"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (建立核心模式二進位檔)

建立可以在 Windows 核心中執行的二進位檔。

## <a name="syntax"></a>語法

```
/kernel[-]
```

## <a name="arguments"></a>引數

**/kernel**<br/>
目前的專案中的程式碼編譯及連結使用一組專屬於會在核心模式中執行的程式碼的 c + + 語言規則。

**/kernel-**<br/>
目前的專案中的程式碼編譯及連結而不需使用專屬於會在核心模式中執行的程式碼的 c + + 語言規則。

## <a name="remarks"></a>備註

沒有任何`#pragma`等於控制這個選項。

指定 **/kernel**選項會告訴編譯器和連結器仲裁哪一個語言功能是允許在核心模式中，請確定您有足夠的表達能力，不必是唯一的執行階段不穩定核心模式 c + +。 這是藉由禁止使用是干擾性核心模式中的 c + + 語言功能，以及提供 c + + 語言功能可能干擾性，但不能停用的警告。

**/Kernel**選項套用至組建的編譯器和連結器階段，並設定專案層級。 傳遞 **/kernel**參數，指出編譯器，產生的二進位檔，連結之後，應該載入 Windows 核心。 編譯器會縮小 c + + 語言功能與核心相容的子集合的範圍。

下表列出的編譯器行為的變更時 **/kernel**指定。

|行為型別|**/kernel** Behavior|
|-------------------|---------------------------|
|C++ 例外狀況處理|已停用。 所有執行個體`throw`並`try`關鍵字會發出編譯器錯誤 (除了例外狀況規格`throw()`)。 否 **/EH**的選項為相容於 **/kernel**，除了 **/EH-**。|
|RTTI|已停用。 所有執行個體`dynamic_cast`並`typeid`關鍵字會發出編譯器錯誤，除非`dynamic_cast`以靜態方式使用。|
|`new` 和 `delete`|您必須明確地定義`new()`或`delete()`運算子; 沒有編譯器或執行階段會提供預設定義。|

呼叫慣例，自訂[/GS](gs-buffer-security-check.md)當您使用允許組建選項，以及所有最佳化 **/kernel**選項。 內嵌多半不會受到 **/kernel**，利用相同的語意，編譯器接受。 如果您想要確定`__forceinline`內嵌的限定詞會接受，您必須確定該警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)會啟用，以便您知道某一特定`__forceinline`函式不是內嵌。

當傳遞編譯器 **/kernel**參數，它會預先定義前置處理器巨集，稱為`_KERNEL_MODE`且具有值**1**。 您可以使用這有條件地編譯為基礎的執行環境是在使用者模式或核心模式程式碼。 例如，下列程式碼會指定類別應該是在非可分頁記憶體區段中，編譯核心模式執行時。

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

某些目標架構的下列組合並 **/arch**搭配使用時，選項會產生錯誤 **/kernel**:

- **/arch: {SSE&#124;SSE2&#124;AVX}** 不支援在 x86 上。 只有 **/arch:ia32**支援 **/kernel** x86 上。

- **/arch: avx**不支援 **/kernel**在 x64 上。

使用建置 **/kernel**也會傳遞 **/kernel**連結器。 她是這如何影響連結器行為：

- 已停用累加連結。 如果您加入 **/incremental**至命令列中，連結器會發出此嚴重的錯誤：

   **LINK： 嚴重錯誤 LNK1295: '/ 增量' 不相容於 '/ 核心' 規格;連結而不需要 '/ 增量'**

- 連結器會檢查每個目的檔 （或任何包含的封存成員從靜態程式庫） 以查看是否它可能已編譯使用 **/kernel**選項，但卻是沒有。 如果任何執行個體符合此準則，連結器仍然可以成功連結，但可能會發出警告下, 表所示。

   ||**/kernel** obj|**/kernel-** obj，MASM obj 或 cvtresed|「 混合 **/kernel**並 **/kernel-** obj|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**link /kernel**|是|是|是，但有警告 LNK4257|
   |**link**|是|是|是|

   **/Kernel; 未編譯的 LNK4257 連結物件映像可能無法執行**

**/Kernel**選項並 **/driver**選項是獨立運作，並且不會影響其他。

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /kernel 編譯器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取  **C/c + +** 資料夾。

1. 選取 **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入`/kernel`或`/kernel-`。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
