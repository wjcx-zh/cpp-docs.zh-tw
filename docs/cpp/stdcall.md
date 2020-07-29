---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: 85d1b29fddece741aa94364bb6edfdf3b973faaf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213173"
---
# <a name="__stdcall"></a>__stdcall

呼叫 **`__stdcall`** 慣例用於呼叫 WIN32 API 函式。 被呼叫端會清除堆疊，因此編譯器會建立函式 `vararg` **`__cdecl`** 。 使用這個呼叫慣例的函式需要函式原型。 **`__stdcall`** 修飾詞是 Microsoft 專有的。

## <a name="syntax"></a>語法

> 傳回*類型* **`__stdcall`***函數名稱*[ **`(`** *引數-清單* **`)`** ]

## <a name="remarks"></a>備註

下列清單會顯示這個呼叫慣例的實作。

|元素|實作|
|-------------|--------------------|
|引數傳遞順序|由右至左。|
|引數傳遞慣例|以傳值方式，除非傳遞指標或參考類型。|
|堆疊維護責任|被呼叫函式會從堆疊快顯其本身的引數。|
|名稱裝飾慣例|底線（ `_` ）的前面會加上名稱。 名稱後面會接著 @ 符號（）， `@` 後面接著引數清單中的位元組數目（十進位）。 因此，宣告為 `int func( int a, double b )` 的函式會裝飾為如下：`_func@12`|
|大小寫轉譯慣例|無|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項 **`__stdcall`** 會為所有未以不同呼叫慣例明確宣告的函式指定。

為了與舊版相容， **`_stdcall`** **`__stdcall`** 除非指定了編譯器選項 [停用[ `/Za` \( 語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能]，否則會是同義字。

使用修飾詞所宣告的函式傳回 **`__stdcall`** 值的方式，與使用宣告的函式相同 [`__cdecl`](../cpp/cdecl.md) 。

在 ARM 和 x64 處理器上， **`__stdcall`** 編譯器會接受並忽略; 在 ARM 和 x64 架構上，依照慣例，引數會盡可能在暫存器中傳遞，而後續引數會在堆疊上傳遞。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義，

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

相當於這個

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>範例

在下列範例中，會將 **`__stdcall`** 所有函式類型中的結果當做 `WINAPI` 標準呼叫來處理：

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
