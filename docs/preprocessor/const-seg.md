---
title: const_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 845583889eb922ba97d145eefe6bca280a83817b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220441"
---
# <a name="const_seg-pragma"></a>const_seg pragma

指定在物件 (.obj) 檔案中儲存[const](../cpp/const-cpp.md)變數的區段 (區段)。

## <a name="syntax"></a>語法

> **#pragma const_seg (** ["*區段-名稱*" [ **,** "*區段類別*"]] **)** \
> **#pragma const_seg (** { **push**  |  **pop** } [ **,** *identifier* ] [ **,** "*section-name*" [ **,** "*section class*"]] **)**

### <a name="parameters"></a>參數

**式**\
選擇性將記錄放在內部編譯器堆疊上。 **推送**可以具有*識別碼*和*區段名稱*。

**提示**\
選擇性從內部編譯器堆疊頂端移除記錄。 **Pop**可以有*識別碼*和*區段名稱*。 您可以使用*識別碼*, 只使用一個**pop**命令來彈出多個記錄。 *區段名稱*會成為 pop 後面的作用中 const 區段名稱。

*標識*\
選擇性與**push**搭配使用時, 會指派名稱給內部編譯器堆疊上的記錄。 與**pop**搭配使用時, 指示詞會從內部堆疊登出, 直到移除*識別碼*為止。 如果在內部堆疊上找不到*識別碼*, 則不會彈出任何內容。

「*區段名稱*」 \
選擇性區段的名稱。 與**pop**搭配使用時, 會彈出堆疊, 而*區段名稱*會變成作用中的 const 區段名稱。

「*區段類別*」 \
選擇性已忽略, 但隨附于2.0 版之前的C++ Microsoft 版本相容性。

## <a name="remarks"></a>備註

物件檔案中的*區段*是一種已命名的資料區塊, 會以單位的形式載入至記憶體中。 *Const 區段*是包含常數資料的區段。 在本文中, 「*區段*」和「*區段*」的意義相同。

**Const_seg** pragma 指示詞會告知編譯器將所有常數資料項目從轉譯單位放入名為*section-name*的 const 區段中。 **Const**變數的物件檔中的預設區段是`.rdata`。 某些**const**變數 (例如純量) 會自動內嵌至程式碼資料流程中。 內嵌程式碼不會`.rdata`出現在中。 沒有*section name*參數的**const_seg** pragma 指示詞會將後續**const**資料項目的區段名稱重設為`.rdata`。

如果您在中`const_seg`定義需要動態初始化的物件, 則結果會是未定義的行為。

如需不應用來建立區段的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md)。

您也可以為已初始化的資料 ([data_seg](../preprocessor/data-seg.md))、未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md)) 及函式 ([code_seg](../preprocessor/code-seg.md)) 指定區段。

您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式來查看物件檔案。 Visual Studio 中包含每個支援的目標架構的 DUMPBIN 版本。

## <a name="example"></a>範例

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
