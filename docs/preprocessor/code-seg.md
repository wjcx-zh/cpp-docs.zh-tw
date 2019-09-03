---
title: code_seg pragma
ms.date: 08/29/2019
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 0144b3ed220c39cd30aeb8e53bc2aa3c0381b668
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218319"
---
# <a name="code_seg-pragma"></a>code_seg pragma

指定在物件 (.obj) 檔案中儲存函數的文字區段 (區段)。

## <a name="syntax"></a>語法

> **#pragma code_seg (** ["*區段-名稱*" [ **,** "*區段類別*"]] **)** \
> **#pragma code_seg (** { **push**  |  **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section class*"]] **)**

### <a name="parameters"></a>參數

**式**\
選擇性將記錄放在內部編譯器堆疊上。 **推送**可以具有*識別碼*和*區段名稱*。

**提示**\
選擇性從內部編譯器堆疊頂端移除記錄。 **Pop**可以有*識別碼*和*區段名稱*。 您可以使用*識別碼*, 只使用一個**pop**命令來彈出多個記錄。 *區段名稱*會成為 pop 後面的現用文字區段名稱。

*標識*\
選擇性與**push**搭配使用時, 會指派名稱給內部編譯器堆疊上的記錄。 與**pop**搭配使用時, 指示詞會從內部堆疊登出, 直到移除*識別碼*為止。 如果在內部堆疊上找不到*識別碼*, 則不會彈出任何內容。

「*區段名稱*」 \
選擇性區段的名稱。 與**pop**搭配使用時, 會彈出堆疊, 而*區段名稱*會變成使用中的文字區段名稱。

「*區段類別*」 \
選擇性已忽略, 但隨附于2.0 版之前的C++ Microsoft 版本相容性。

## <a name="remarks"></a>備註

物件檔案中的*區段*是一種已命名的資料區塊, 會以單位的形式載入至記憶體中。 *文字區段*是包含可執行程式碼的區段。 在本文中, 「*區段*」和「*區段*」的意義相同。

**Code_seg** pragma 指示詞會告知編譯器將所有後續的物件程式碼從轉譯單位放入名為*section-name*的文字區段中。 根據預設, 物件檔中函式所使用的文字區段會命名`.text`為。 沒有*section name*參數的**code_seg** pragma 指示詞會將後續物件程式碼的文字區段名稱重設`.text`為。

**Code_seg** pragma 指示詞不會控制針對具現化範本所產生之物件程式碼的位置。 也不會控制由編譯器隱含產生的程式碼, 例如特殊的成員函式。 若要控制該程式碼, 我們建議您改用[__declspec (code_seg (...))](../cpp/code-seg-declspec.md)屬性。 它可讓您控制所有物件程式碼的放置, 包括編譯器產生的程式碼。

如需不應用來建立區段的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md)。

您也可以為已初始化的資料 ([data_seg](../preprocessor/data-seg.md))、未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md)) 和 const 變數 ([const_seg](../preprocessor/const-seg.md)) 指定區段。

您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式來查看物件檔案。 Visual Studio 中包含每個支援的目標架構的 DUMPBIN 版本。

## <a name="example"></a>範例

這個範例示範如何使用**code_seg** pragma 指示詞來控制物件程式碼的 put 位置:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>另請參閱

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
