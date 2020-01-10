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
ms.openlocfilehash: df753241c093db75202a10b106631ce36cf73379
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857277"
---
# <a name="__stdcall"></a>__stdcall

**__Stdcall**呼叫慣例是用來呼叫 WIN32 API 函式。 被呼叫端會清除堆疊，因此編譯器會 **__cdecl**`vararg` 函數。 使用這個呼叫慣例的函式需要函式原型。 **__Stdcall**修飾詞是 Microsoft 專有的。

## <a name="syntax"></a>語法

> 傳回*類型* **\_\_stdcall**函*式名稱*[ **（** *引數-清單* **）** ]

## <a name="remarks"></a>備註

下列清單會顯示這個呼叫慣例的實作。

|項目|實作|
|-------------|--------------------|
|引數傳遞順序|由右至左。|
|引數傳遞慣例|以傳值方式，除非傳遞指標或參考類型。|
|堆疊維護責任|被呼叫函式會從堆疊快顯其本身的引數。|
|名稱裝飾慣例|名稱前面會加底線 (_)。 名稱後面加上 @ 符號，再接著引數清單中的位元組數目 (十進位)。 因此，宣告為 `int func( int a, double b )` 的函式會裝飾為如下：`_func@12`|
|大小寫轉譯慣例|None|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會為所有未以不同呼叫慣例明確宣告的函式指定 **__stdcall** 。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_stdcall**是 **__stdcall**的同義字。

使用 **__stdcall**修飾詞所宣告的函式傳回值的方式，與使用[__cdecl](../cpp/cdecl.md)宣告的函式相同。

在 ARM 和 x64 處理器上，編譯器會接受並忽略 **__stdcall** ;根據慣例，在 ARM 和 x64 架構上，引數會盡可能在暫存器中傳遞，而後續引數會在堆疊上傳遞。

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

在下列範例中，使用 **__stdcall**會導致所有 `WINAPI` 函式類型當做標準呼叫來處理：

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)