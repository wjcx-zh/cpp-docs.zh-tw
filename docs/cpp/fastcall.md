---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 3e7cd4b1202ee717abf9a9767785ed8abe96bd69
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627360"
---
# <a name="fastcall"></a>__fastcall

**Microsoft 專屬**

**__Fastcall**呼叫慣例會指定函數的引數會傳入暫存器，盡可能中。 這個呼叫慣例僅適用於 x86 架構。 下列清單會顯示這個呼叫慣例的實作。

|元素|實作|
|-------------|--------------------|
|引數傳遞順序|引數清單中的前兩個 DWORD 引數或較小引數會由左至右傳入 ECX 和 EDX 暫存器，所有其他引數則由右至左傳遞至堆疊上。|
|堆疊維護責任|所呼叫的函式會從堆疊取出引數。|
|名稱裝飾慣例|@ 記號 (\@) 加在名稱後面接著位元組數 （十進位） 參數中的符號清單後置字元的名稱。|
|大小寫轉譯慣例|未執行大小寫轉譯。|

> [!NOTE]
> 未來的編譯器版本可能會使用不同的暫存器來儲存參數。

使用[/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md)編譯器選項會造成編譯為模組中的每個函式 **__fastcall**除非使用衝突的屬性，宣告的函式或函式的名稱是`main`.

**__Fastcall**關鍵字會接受並忽略 ARM 和 x64 為目標的編譯器架構; 在 x64 晶片，依照慣例前, 四個引數會傳入暫存器，可能的話，請傳遞額外引數在堆疊中。 如需詳細資訊，請參閱 < [x64 呼叫慣例](../build/x64-calling-convention.md)。 在 ARM 晶片上，最多可以在暫存器中傳遞四個整數引數和八個浮點引數，而其他引數則是在堆疊上傳遞。

對於非靜態類別函式，如果函式是以非正規的方式定義，則不需要在非正規定義上指定呼叫慣例修飾詞。 也就是說，對於類別非靜態成員方法而言，宣告時所指定的呼叫慣例是在定義時假設。 如果已指定此類別定義：

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

這個：

```cpp
void CMyClass::mymethod() { return; }
```

相當於這個：

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

為了與舊版中，相容性 **_fastcall**同義 **__fastcall**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)是指定此項目。

## <a name="example"></a>範例

下列範例會對暫存器中的 `DeleteAggrWrapper` 函式傳遞引數：

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)