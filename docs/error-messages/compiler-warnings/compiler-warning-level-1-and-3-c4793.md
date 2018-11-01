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
ms.openlocfilehash: e7ca3b10e09b0d6818fbc7f5607ebc9c95c7f15c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623245"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>編譯器警告 (層級 1 和 3) C4793

> '*函式*': 函式會編譯為原生程式碼:'*原因*'

## <a name="remarks"></a>備註

編譯器無法編譯*函式*managed 程式碼，即使[/clr](../../build/reference/clr-common-language-runtime-compilation.md)指定編譯器選項。 相反地，編譯器會發出警告 C4793 和說明的接續訊息，，然後編譯*函式*原生程式碼。 這個接續訊息包含*原因*文字，說明為什麼*函式*無法編譯成`MSIL`。

這是層級 1 警告，當您指定 **/clr: pure**編譯器選項。  **/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

下表列出所有可能的接續訊息。

|原因的訊息|備註|
|--------------------|-------------|
|在 managed 程式碼中不支援對齊的資料類型|CLR 必須要能夠配置資料，如有需要這可能不可行，如果這類的資料對齊與宣告[__m128](../../cpp/m128.md)或是[對齊](../../cpp/align-cpp.md)。|
|Managed 程式碼中不支援使用 '含有 __ImageBase' 函式|`__ImageBase` 是一種特殊的連結器符號通常用來載入 DLL 只能由低層級的原生程式碼。|
|不支援 varargs ' / clr' 編譯器選項|原生函式不能呼叫 managed 函式具有[變數引數清單](../../cpp/functions-with-variable-argument-lists-cpp.md)(varargs) 因為函式具有不同的堆疊配置需求。 不過，如果您指定 **/clr: pure**編譯器選項，因為組件可以包含 managed 函式僅支援清單的變數引數。 如需詳細資訊，請參閱 <<c0> [ 純粹的和可驗證程式碼 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|
|在 64 位元 CLR 不支援 __ptr32 修飾詞宣告的資料|指標必須是目前的平台的原生指標相同的大小。 如需詳細資訊，請參閱 < [__ptr32， \__ptr64](../../cpp/ptr32-ptr64.md)。|
|32 位元 CLR 不支援使用 __ptr64 修飾詞宣告的資料|指標必須是目前的平台的原生指標相同的大小。 如需詳細資訊，請參閱 < [__ptr32， \__ptr64](../../cpp/ptr32-ptr64.md)。|
|一或多個內建函式不支援在 managed 程式碼|就會發出訊息時，不可以使用內建函式的名稱。 不過，內建，通常會導致此訊息表示低階的機器指令。|
|Managed 程式碼中不支援內嵌原生組譯碼 ('__asm')|[內嵌組譯碼](../../assembler/inline/asm.md)可以包含任意的原生程式碼，無法管理它。|
|非 __clrcall 虛擬函式 thunk 必須編譯為原生|為非[__clrcall](../../cpp/clrcall.md)虛擬函式 thunk 必須使用未受管理的位址。|
|使用 '_setjmp' 函式必須以原生編譯|CLR 必須能夠控制執行程式。 不過， [setjmp](../../cpp/using-setjmp-longjmp.md)函式會執行規則的程式略過由儲存和還原低層級的資訊，例如暫存器和執行狀態。|

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