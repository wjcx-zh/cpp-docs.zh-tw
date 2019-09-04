---
title: bss_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: a343fb45b4bbe4789f38b7a1102572cf4241ec53
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218556"
---
# <a name="bss_seg-pragma"></a>bss_seg pragma

指定未初始化的變數儲存在物件 (.obj) 檔案中的區段 (區段)。

## <a name="syntax"></a>語法

> **#pragma bss_seg (** ["*區段-名稱*" [ **,** "*區段類別*"]] **)** \
> **#pragma bss_seg (** { **push**  |  **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section class*"]] **)**

### <a name="parameters"></a>參數

**式**\
選擇性將記錄放在內部編譯器堆疊上。 **推送**可以具有*識別碼*和*區段名稱*。

**提示**\
選擇性從內部編譯器堆疊頂端移除記錄。 **Pop**可以有*識別碼*和*區段名稱*。 您可以使用*識別碼*, 只使用一個**pop**命令來彈出多個記錄。 *區段名稱*會變成 pop 後面的作用中 BSS 區段名稱。

*標識*\
選擇性與**push**搭配使用時, 會指派名稱給內部編譯器堆疊上的記錄。 與**pop**搭配使用時, 指示詞會從內部堆疊登出, 直到移除*識別碼*為止。 如果在內部堆疊上找不到*識別碼*, 則不會彈出任何內容。

*「區段名稱」* \
選擇性區段的名稱。 與**pop**搭配使用時, 會彈出堆疊, 而*區段名稱*會變成作用中的 BSS 區段名稱。

*「區段類別」* \
選擇性已忽略, 但隨附于2.0 版之前的C++ Microsoft 版本相容性。

## <a name="remarks"></a>備註

物件檔案中的*區段*是一種已命名的資料區塊, 會以單位的形式載入至記憶體中。 *BSS 區段*是包含未初始化資料的區段。 在本文中, 「*區段*」和「*區段*」的意義相同。

**Bss_seg** pragma 指示詞會告訴編譯器, 將所有未初始化的資料項目從轉譯單位放入名為*section-name*的 bss 區段中。 在某些情況下, 使用**bss_seg**可以藉由將未初始化的資料分組成一個區段來加速載入時間。 根據預設, 物件檔案中未初始化資料所用的 BSS 區段會命名`.bss`為。 沒有*section name*參數的**bss_seg** pragma 指示詞會將後續未初始化資料項目的 bss 區段名稱重設為`.bss`。

使用**bss_seg** pragma 配置的資料不會保留其位置的任何相關資訊。

如需不應用來建立區段的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md)。

您也可以為已初始化的資料 ([data_seg](../preprocessor/data-seg.md))、函數 ([code_seg](../preprocessor/code-seg.md)) 和 const 變數 ([const_seg](../preprocessor/const-seg.md)) 指定區段。

您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式來查看物件檔案。 Visual Studio 中包含每個支援的目標架構的 DUMPBIN 版本。

## <a name="example"></a>範例

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
