---
title: data_seg
ms.date: 10/22/2018
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: 414fc542aa3f84f985e326960d8cf73b67fd1580
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456377"
---
# <a name="dataseg"></a>data_seg

指定儲存在 .obj 檔案中已初始化之變數的資料區段。

## <a name="syntax"></a>語法

```
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>參數

**push**<br/>
（選擇性）將記錄放入內部編譯器堆疊上。 A**推播**可以有*識別項*並*區段名稱*。

**pop**<br/>
（選擇性）從內部編譯器堆疊頂端移除記錄。

*identifier*<br/>
（選擇性）當搭配**推播**，將名稱指派給內部編譯器堆疊上的記錄。 當搭配**pop**，會將記錄推出內部堆疊，直到*識別項*已移除; 如果*識別碼*找不到在內部堆疊上，不會推出。

*識別項*可讓一推出多筆資料錄**pop**命令。

*「 區段名稱 」*<br/>
（選擇性）區段名稱。 當搭配**pop**，時會推出堆疊並*區段名稱*會變成作用中區段名稱。

*「 區段類別 」*<br/>
（選擇性）包含與 c + + 2.0 以前版本的相容性。 會忽略此項。

## <a name="remarks"></a>備註

意義*區段*並*一節*是本主題中的可互換的。

OBJ 檔案可以使用檢視[dumpbin](../build/reference/dumpbin-command-line.md)應用程式。 .obj 檔案中已初始化之變數的預設區段是 .data。 未初始化的變數會被視為要初始化為零，並儲存在 .bss 中。

**data_seg**不含任何參數區段重設為.data。

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

使用配置的資料**data_seg**不會保留與其位置相關的任何資訊。

請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，應該不會使用您的名稱。

您也可以指定為 const 變數的區段 ([const_seg](../preprocessor/const-seg.md))，未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md))，和函式 ([code_seg](../preprocessor/code-seg.md))。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
