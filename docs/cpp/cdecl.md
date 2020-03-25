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
ms.openlocfilehash: 8f2b2b0cea8ff30cc450aae534fbff0d7b77f457
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190090"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl**是 C 和C++程式的預設呼叫慣例。 因為堆疊是由呼叫端所清除，所以它可以執行 `vararg` 函式。 **__Cdecl**呼叫慣例會建立比[__stdcall](../cpp/stdcall.md)更大的可執行檔，因為它會要求每個函式呼叫都包含堆疊清除程式碼。 下列清單會顯示這個呼叫慣例的實作。 **__Cdecl**修飾詞是 Microsoft 專有的。

|元素|實作|
|-------------|--------------------|
|引數傳遞順序|由右至左。|
|堆疊維護責任|呼叫函式會從堆疊取出引數。|
|名稱裝飾慣例|除非匯出使用 C 連結的 \__cdecl 函式，否則底線字元（_）前面會加上名稱。|
|大小寫轉譯慣例|未執行大小寫轉譯。|

> [!NOTE]
>  如需相關資訊，請參閱[裝飾名稱](../build/reference/decorated-names.md)。

將 **__cdecl**修飾詞放在變數或函數名稱之前。 因為 C 命名和呼叫慣例都是預設值，所以您必須在 x86 程式碼中使用 **__cdecl**的唯一時機，就是當您指定了 `/Gv` （vectorcall）、`/Gz` （stdcall）或 `/Gr` （fastcall）編譯器選項時。 [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會強制執行 **__cdecl**呼叫慣例。

在 ARM 和 x64 處理器上，會接受 **__cdecl** ，但編譯器通常會忽略它。 ARM 和 x64 的慣例會盡可能在暫存器中傳遞引數，並在堆疊上傳遞後續的引數。 在 x64 程式碼中，請使用 **__cdecl**來覆寫 **/Gv**編譯器選項，並使用預設的 x64 呼叫慣例。

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

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則**cdecl**和 **_cdecl**是 **__cdecl**的同義字。

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
