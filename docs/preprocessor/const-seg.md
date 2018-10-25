---
title: const_seg |Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b700b1e1b83586635f0628c9b2b6be7377315b27
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079424"
---
# <a name="constseg"></a>const_seg
指定的區段位置[const](../cpp/const-cpp.md)變數會儲存在.obj 檔案。

## <a name="syntax"></a>語法

```
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>參數

**push**<br/>
（選擇性）將記錄放入內部編譯器堆疊上。 A**推播**可以有*識別項*並*區段名稱*。

**pop**<br/>
（選擇性）從內部編譯器堆疊頂端移除記錄。

*identifier*<br/>
（選擇性）當搭配**推播**，將名稱指派給內部編譯器堆疊上的記錄。 當搭配**pop**，會將記錄推出內部堆疊，直到*識別項*已移除; 如果*識別碼*找不到在內部堆疊上，不會推出。

使用*識別碼*可讓一推出多筆記錄**pop**命令。

「*區段名稱*"<br/>
（選擇性）區段名稱。 當搭配**pop**，時會推出堆疊並*區段名稱*會變成作用中區段名稱。

「*區段類別*"<br/>
（選擇性）包含與 c + + 2.0 以前版本的相容性。 會忽略此項。

## <a name="remarks"></a>備註

意義*區段*並*一節*是本主題中的可互換的。

OBJ 檔案可以使用檢視[dumpbin](../build/reference/dumpbin-command-line.md)應用程式。 .obj 檔案中 `const` 變數的預設區段是 .rdata。 某些 `const` 變數 (例如純量) 會自動內嵌於程式碼資料流中。 內嵌的程式碼不會出現在 .rdata 中。

定義必須在 `const_seg` 中進行動態初始化的物件時，會產生未定義的行為。

未包含參數的 `#pragma const_seg` 會將區段重設為 .rdata。

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

## <a name="comments"></a>註解

請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，應該不會使用您的名稱。

您也可以指定為初始化的資料區段 ([data_seg](../preprocessor/data-seg.md))，未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md))，和函式 ([code_seg](../preprocessor/code-seg.md))。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)