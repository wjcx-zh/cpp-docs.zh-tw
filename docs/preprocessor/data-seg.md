---
title: data_seg pragma
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220388"
---
# <a name="data_seg-pragma"></a>data_seg pragma

指定初始化的變數儲存在物件 (.obj) 檔案中的資料區段 (區段)。

## <a name="syntax"></a>語法

> **#pragma data_seg (** ["*區段-名稱*" [ **,** "*區段類別*"]] **)** \
> **#pragma data_seg (** { **push**  |  **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section class*"]] **)**

### <a name="parameters"></a>參數

**式**\
選擇性將記錄放在內部編譯器堆疊上。 **推送**可以具有*識別碼*和*區段名稱*。

**提示**\
選擇性從內部編譯器堆疊頂端移除記錄。 **Pop**可以有*識別碼*和*區段名稱*。 您可以使用*識別碼*, 只使用一個**pop**命令來彈出多個記錄。 *區段名稱*會成為 pop 後面的作用中資料區段名稱。

*標識*\
選擇性與**push**搭配使用時, 會指派名稱給內部編譯器堆疊上的記錄。 與**pop**搭配使用時, 會將內部堆疊的記錄, 直到移除*識別碼*為止。 如果在內部堆疊上找不到*識別碼*, 則不會彈出任何內容。

「*識別碼*」可讓您使用單一**pop**命令來彈出多筆記錄。

*「區段名稱」* \
選擇性區段的名稱。 與**pop**搭配使用時, 會彈出堆疊, 而*區段名稱*會變成使用中的資料區段名稱。

*「區段類別」* \
選擇性已忽略, 但隨附于2.0 版之前的C++ Microsoft 版本相容性。

## <a name="remarks"></a>備註

物件檔案中的*區段*是一種已命名的資料區塊, 會以單位的形式載入至記憶體中。 *資料區段*是包含已初始化資料的區段。 在本文中, 「*區段*」和「*區段*」的意義相同。

已初始化變數的 .obj 檔案中的預設區段是`.data`。 未初始化的變數會被視為初始化為零, 並儲存在中`.bss`。

**Data_seg** pragma 指示詞會告訴編譯器, 將所有初始化的資料項目從轉譯單位放入名為*section-name*的資料區段中。 根據預設, 用於初始化物件檔案中之資料的資料區段會命名`.data`為。 未初始化的變數會被視為初始化為零, 而且會儲存在中`.bss`。 沒有*section name*參數的`.data` **data_seg** pragma 指示詞會將後續初始化資料項目的資料區段名稱重設為。

使用**data_seg**配置的資料不會保留其位置的任何相關資訊。

如需不應用來建立區段的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md)。

您也可以為 const 變數 ([const_seg](../preprocessor/const-seg.md))、未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md)) 及函式 ([code_seg](../preprocessor/code-seg.md)) 指定區段。

您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式來查看物件檔案。 Visual Studio 中包含每個支援的目標架構的 DUMPBIN 版本。

## <a name="example"></a>範例

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
