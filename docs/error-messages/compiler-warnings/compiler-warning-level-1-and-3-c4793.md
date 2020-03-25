---
title: 編譯器警告 (層級 1 和 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164803"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>編譯器警告 (層級 1 和 3) C4793

> '*function*'：函式編譯為機器碼： '*reason*'

## <a name="remarks"></a>備註

即使已指定[/clr](../../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，編譯器還是無法將函*式編譯成*managed 程式碼。 相反地，編譯器會發出警告 C4793 和說明接續訊息，然後將函*式編譯成*機器碼。 接續訊息包含*說明為何無法*將函式編譯為 `MSIL`的*原因*文字。

當您指定 **/clr： pure**編譯器選項時，這就是層級1警告。  **/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

下表列出所有可能的接續訊息。

|原因訊息|備註|
|--------------------|-------------|
|受控碼中不支援對齊的資料類型|CLR 必須能夠視需要配置資料，如果資料對齊[__m128](../../cpp/m128.md)或[align](../../cpp/align-cpp.md)之類的宣告，可能就不可能發生這種情況。|
|Managed 程式碼中不支援使用 ' __ImageBase ' 的函數|`__ImageBase` 是特殊的連結器符號，通常僅供低層級機器碼用來載入 DLL。|
|'/clr ' 編譯器選項不支援 varargs|因為函式有不同的堆疊配置需求，所以原生函式無法呼叫具有[變數引數清單](../../cpp/functions-with-variable-argument-lists-cpp.md)（varargs）的 managed 函數。 不過，如果您指定 **/clr： pure**編譯器選項，則會支援變數引數清單，因為元件只能包含 managed 函數。 如需詳細資訊，請參閱[單純和可C++驗證的程式碼（/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|
|64位 CLR 不支援使用 __ptr32 修飾詞所宣告的資料|指標必須與目前平臺上的原生指標大小相同。 如需詳細資訊，請參閱[__ptr32，\__ptr64](../../cpp/ptr32-ptr64.md)。|
|32位 CLR 不支援使用 __ptr64 修飾詞所宣告的資料|指標必須與目前平臺上的原生指標大小相同。 如需詳細資訊，請參閱[__ptr32，\__ptr64](../../cpp/ptr32-ptr64.md)。|
|Managed 程式碼中不支援一個或多個內建函式|內建函式的名稱在發出訊息時無法使用。 不過，造成此訊息的內建函式通常代表低層級的機器指令。|
|Managed 程式碼中不支援內嵌原生組解碼（' __asm '）|[內嵌組解碼程式碼](../../assembler/inline/asm.md)可以包含無法管理的任意機器碼。|
|非 __clrcall 的虛擬函式 Thunk 必須編譯為 native|非[__clrcall](../../cpp/clrcall.md)的虛擬函數 Thunk 必須使用非受控位址。|
|使用 ' _setjmp ' 的函數必須編譯為 native|CLR 必須能夠控制程式執行。 不過， [setjmp](../../cpp/using-setjmp-longjmp.md)函數會藉由儲存和還原低層級的資訊（例如暫存器和執行狀態）來略過一般程式執行。|

## <a name="example"></a>範例

下列範例會產生 C4793。

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

下列範例會產生 C4793。

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```
