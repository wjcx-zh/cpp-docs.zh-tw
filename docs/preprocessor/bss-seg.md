---
title: bss_seg
ms.date: 10/22/2018
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: 489ced11bb6024fdf9818872c07ab7feebfeabf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212408"
---
# <a name="bssseg"></a>bss_seg

指定儲存在 .obj 檔案中未初始化之變數的區段。

## <a name="syntax"></a>語法

```
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>參數

**push**<br/>
（選擇性）將記錄放入內部編譯器堆疊上。 A *pu*sh * 可以有*識別項*並*區段名稱*。

**pop**<br/>
（選擇性）從內部編譯器堆疊頂端移除記錄。

*identifier*<br/>
（選擇性）當搭配**推播**，將名稱指派給內部編譯器堆疊上的記錄。 *識別項*可讓一推出多筆資料錄**pop**命令。 當搭配**pop**，指示詞會將記錄推出內部堆疊，直到*識別項*已移除; 如果*識別碼*找不到在內部堆疊上，沒有快顯。

*"segment-name"*<br/>
（選擇性）區段名稱。 當搭配**pop**，時會推出堆疊並*區段名稱*會變成作用中區段名稱。

*"segment-class"*<br/>
（選擇性）包含與相容性C++早於 2.0 版。 會忽略此項。

## <a name="remarks"></a>備註

.Obj 檔案可以使用檢視[dumpbin](../build/reference/dumpbin-command-line.md)應用程式。 .obj 檔案中未初始化之資料的預設區段是 .bss。 在某些情況下使用**bss_seg**可加速載入時間的未初始化的資料分組成一個區段。

**bss_seg**不含任何參數區段重設為.bss。

使用配置的資料**bss_seg** pragma 不會保留與其位置相關的任何資訊。

您也可以指定為初始化的資料區段 ([data_seg](../preprocessor/data-seg.md))，函式 ([code_seg](../preprocessor/code-seg.md))，和 const 變數 ([const_seg](../preprocessor/const-seg.md))。

請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，應該不會使用您的名稱。

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

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
