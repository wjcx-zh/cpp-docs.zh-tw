---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: e566fb01bf70b343b75254a10466bdda2bc7ce1b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041237"
---
# <a name="codeseg"></a>code_seg
指定文字區段，其中函式儲存在 .obj 檔案中。

## <a name="syntax"></a>語法

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>參數

**push**<br/>
（選擇性）將記錄放入內部編譯器堆疊上。 A**推播**可以有*識別項*並*區段名稱*。

**pop**<br/>
（選擇性）從內部編譯器堆疊頂端移除記錄。

*識別項*<br/>
（選擇性）當搭配**推播**，將名稱指派給內部編譯器堆疊上的記錄。 當搭配**pop**，會將記錄推出內部堆疊，直到*識別項*已移除; 如果*識別碼*找不到在內部堆疊上，不會推出。

*識別項*可讓多筆記錄，是只使用一個快顯**pop**命令。

"*segment-name*"<br/>
（選擇性）區段名稱。 當搭配**pop**，時會推出堆疊並*區段名稱*會變成作用中的文字區段名稱。

"*segment-class*"<br/>
（選擇性）會被忽略，包含與 c + + 的版本早於 2.0 版相容。

## <a name="remarks"></a>備註

**Code_seg** pragma 指示詞不會控制具現化的範本，產生的物件程式碼，也不會隱含地編譯器所產生的程式碼的位置，例如特殊成員函式。 我們建議您改用[__declspec(code_seg(...))](../cpp/code-seg-declspec.md)改為屬性，因為它可讓您控制所有目的碼的位置。 這包括編譯器產生的程式碼。

A*區段*在.obj 檔案是載入成為記憶體單位的資料的具名的區塊。 A*文字區段*是包含可執行程式碼區段。 在本文中，詞彙*區段*並*一節*交替使用。

**Code_seg** pragma 指示詞會指示編譯器 z jednotky překladu 的後續物件的所有程式碼置於名為文字區段*區段名稱*。 根據預設，.obj 檔中函式所使用的文字區段是具名的 .text。

A **code_seg**不含參數的 pragma 指示詞會將後續目的碼的文字區段名稱重設為.text。

您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式檢視.obj 檔。 每個支援的目標架構的 DUMPBIN 版本是隨附於 Visual Studio。

## <a name="example"></a>範例

此範例示範如何使用**code_seg** pragma 指示詞控制目的碼要在其中放置：

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

如需不應該用來建立的區段名稱的清單，請參閱 < [/section](../build/reference/section-specify-section-attributes.md)。

您也可以指定為初始化的資料區段 ([data_seg](../preprocessor/data-seg.md))，未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md))，和 const 變數 ([const_seg](../preprocessor/const-seg.md))。

## <a name="see-also"></a>另請參閱

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)