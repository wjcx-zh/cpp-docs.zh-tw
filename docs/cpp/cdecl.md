---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371558"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl**是 C 和 C++程式的預設調用約定。 由於堆疊由調用方清理,因此它可以執行`vararg`函數。 **__cdecl**調用約定創建比[__stdcall](../cpp/stdcall.md)更大的可執行檔,因為它需要每個函數調用來包含堆疊清理代碼。 下列清單會顯示這個呼叫慣例的實作。 **__cdecl**修改器特定於 Microsoft。

|項目|實作|
|-------------|--------------------|
|引數傳遞順序|由右至左。|
|堆疊維護責任|呼叫函式會從堆疊取出引數。|
|名稱裝飾慣例|底線字元 (*) 預先名稱,\_但匯出使用 C 連結的_cdecl函數除外。|
|大小寫轉譯慣例|未執行大小寫轉譯。|

> [!NOTE]
> 有關相關資訊,請參閱[修飾名稱](../build/reference/decorated-names.md)。

將 **__cdecl**修改器放在變數或函數名稱之前。 由於 C 命名和調用約定是預設值,因此在 x86 代碼中必須使用 **__cdecl**的`/Gv`唯一時間是指定 (向量呼叫`/Gz`)、(stdcall) 或`/Gr`(快速調用)編譯器選項。 [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項強制 **__cdecl**調用約定。

在 ARM 和 x64 處理器上 **,__cdecl**被編譯器接受,但通常忽略。 ARM 和 x64 的慣例會盡可能在暫存器中傳遞引數，並在堆疊上傳遞後續的引數。 在 x64 代碼中,使用 **__cdecl**來重寫 **/Gv**編譯器選項並使用預設 x64 調用約定。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義：

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

這個：

```cpp
void CMyClass::mymethod() { return; }
```

相當於這個：

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

為了與早期版本相容 **,cdecl**和 **_cdecl**是 **__cdecl**的同義詞,除非指定編譯器選項[/Za\(禁用語言擴展)。](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>範例

在下列範例中，編譯器收到的指示是針對 `system` 函式使用 C 命名及呼叫慣例。

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
