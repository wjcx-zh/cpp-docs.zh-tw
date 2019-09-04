---
title: init_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221012"
---
# <a name="init_seg-pragma"></a>init_seg pragma

**C++特殊**

指定會影響啟始程式碼執行順序的關鍵字或程式碼區段。

## <a name="syntax"></a>語法

> **#pragma init_seg (** {**編譯器** |  **lib**  | **使用者**|"*section-name*" [ **,** *func-name* ]} **)**

## <a name="remarks"></a>備註

本文中的詞彙*區段*和*區段*具有相同的意義。

因為程式碼有時需要初始化全域靜態物件, 所以您必須指定何時要建立物件。 特別的是, 在動態連結程式庫 (Dll) 或需要初始化的程式庫中使用**init_seg** pragma 是很重要的。

**Init_seg** pragma 的選項如下:

**編譯器**\
針對 Microsoft C 執行階段程式庫初始化保留。 這個群組中的物件會最先結構。

**lib**\
可供協力廠商類別程式庫廠商進行初始化。 這個群組中的物件會在標記為**編譯器**的專案之後, 但在其他任何專案之前進行。

**使用者**\
可供任何使用者使用。 這個群組中的物件會最後結構。

*區段-名稱*\
允許明確指定初始化區段。 使用者指定之*區段名稱*中的物件不會以隱含方式建立。 不過, 其位址會放在以*區段名稱*命名的區段中。

您所提供的*區段名稱*會包含 helper 函式的指標, 該函數將會在該模組中, 建立在 pragma 之後宣告的全域物件。

如需建立區段時不應該使用的名稱清單, 請參閱[/SECTION](../build/reference/section-specify-section-attributes.md)。

*func-name*\
指定程式結束時，要取代 `atexit` 呼叫的函式。 這個 helper 函式也會呼叫具有全域物件之函式指標的[atexit](../c-runtime-library/reference/atexit.md) 。 如果您使用下列形式的 pragma 指定函式識別項：

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

那麼將會呼叫您的函式，而不是 C 執行階段程式庫的 `atexit`。 當您準備好終結物件時, 它可讓您建立要呼叫的析構函數清單。

如果您需要延遲初始化 (例如在 DLL 中)，可以選擇明確指定區段名稱。 接著, 您的程式碼必須呼叫每個靜態物件的函式。

取代 `atexit` 的識別項前後沒有引號。

您的物件仍會放在其他`XXX_seg` pragma 所定義的區段中。

在模組中宣告的物件不會由 C 執行時間自動初始化。 您的程式碼必須執行初始化。

根據預設，`init_seg` 區段是唯讀的。 如果區段名稱為, `.CRT`則編譯器會以無訊息方式將屬性變更為唯讀, 即使它標示為 read、write 也一樣。

您不能在轉譯單位中多次指定**init_seg** 。

即使您的物件沒有使用者定義的函式, 但在程式碼中明確定義, 編譯器還是會為您產生一個。 例如, 它可能會建立一個來系結 v-資料表指標。 如有需要, 您的程式碼會呼叫編譯器所產生的函式。

## <a name="example"></a>範例

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
