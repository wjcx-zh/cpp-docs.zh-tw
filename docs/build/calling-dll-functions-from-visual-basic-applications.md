---
title: 從 Visual Basic 應用程式中呼叫 DLL 函式
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221191"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>從 Visual Basic 應用程式中呼叫 DLL 函式

若要讓 Visual Basic 應用程式（或 Pascal 或 Fortran 等其他語言的應用程式）呼叫 C/c + + DLL 中的函式，則必須使用正確的呼叫慣例來匯出函式，而編譯器不會執行任何名稱裝飾

`__stdcall`為函式建立正確的呼叫慣例（被呼叫的函式會清除堆疊，而參數會從右至左傳遞），但會以不同的方式裝飾函式名稱。 因此，在 DLL 中的匯出函式上使用 **__declspec （dllexport）** 時，會匯出裝飾名稱。

`__stdcall`名稱裝飾會在符號名稱前面加上底線（ **\_** ），並以 @ 符號（**\@**）字元附加符號，後面接著引數清單中的位元組數目（所需的堆疊空間）。 因此，當宣告為時，函式會：

```C
int __stdcall func (int a, double b)
```

在輸出中`_func@12`會裝飾為。

C 呼叫慣例（`__cdecl`）會將名稱裝飾為`_func`。

若要取得裝飾名稱，請使用[/MAP](reference/map-generate-mapfile.md)。 使用 **__declspec （dllexport）** 會執行下列動作：

- 如果函式是以 C 呼叫慣例（`__cdecl`）匯出，則會在匯出名稱時去除**\_** 前置底線（）。

- 如果要匯出的函式不使用 C 呼叫慣例（例如`__stdcall`），它會匯出裝飾名稱。

因為沒有任何方法可以覆寫堆疊清除發生的位置，所以您必須`__stdcall`使用。 若要使用`__stdcall`undecorate 名稱，您必須在 .def 檔的 [匯出] 區段中，使用別名來指定它們。 下列函式宣告如下所示：

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

在。DEF 檔案：

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

若要讓以 Visual Basic 撰寫的程式呼叫 Dll，請在 .def 檔案中使用本主題所顯示的別名技術。 如果別名是在 Visual Basic 程式中完成，則不需要在 .def 檔中使用「別名」。 您可以藉由將 alias 子句加入[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)語句中，在 Visual Basic 程式中完成此作業。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [從 DLL 匯出](exporting-from-a-dll.md)

- [使用從 DLL 匯出。DEF 檔案](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出 C++ 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [裝飾名稱](reference/decorated-names.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
